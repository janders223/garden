---
date: 2021-07-25T18:33
---

# dockerTools

## buildImage
```nix
buildImage {
  name = "redis"; 
  tag = "latest"; 

  fromImage = someBaseImage; 
  fromImageName = null; 
  fromImageTag = "latest"; 

  contents = pkgs.redis; 
  runAsRoot = '' 
    #!${pkgs.runtimeShell}
    mkdir -p /data
  '';

  config = { 
    Cmd = [ "/bin/redis-server" ];
    WorkingDir = "/data";
    Volumes = {
      "/data" = {};
    };
  };
}
```
- name: name of the output image `*required`
- tag: tag of the output image
- fromImage: must be a valid docker image as exported by `docker save`. Default is `null` which is equivalent to `FROM scratch` in a Dockerfile
- fromImageName: further  specify the base image within the repository in case it contains multiple images
- fromImagTag: further specify the tag of the base image in case the repository contains multiple tags
- contents: a derivation that will be copied in the new layer of the result image. akin to `ADD contents/ /` in a Dockerfile
- runAsRoot: a bash script that will run as root in the environment that overlays the editing layers of the base image with the new resulting layer. Similar to  calling `RUN` in a Dockerfile
- config: is the configuration of the containers that will be started based on the resulting image. The available options are listed in the [Docker Image Specification v1.2.0](https://github.com/moby/moby/blob/master/image/spec/v1.2.md#image-json-field-descriptions)

## pullImage
```nix
pullImage {
  imageName = "nixos/nix"; 
  imageDigest = "sha256:20d9485b25ecfd89204e843a962c1bd70e9cc6858d65d7f5fadc340246e2116b"; 
  finalImageName = "nix"; 
  finalImageTag = "1.11";  
  sha256 = "0mqjy3zq2v6rrhizgb9nvhczl87lcfphq9601wcprdika2jz7qh8"; 
  os = "linux"; 
  arch = "x86_64"; 
}
```
- analogous to `docker pull` and will pull using the Docker hub
- imageName - the name of the image to be downloaded which can include a registry namespace `*require`
- imageDigest - the digest of the image to be downloaded `*required`
- finalImageName - the name of the image to be created. default `imageName`
- sha256 - the checksum of the whole fetched image `*required`
- os - the operating system of the fetched image
- arch - the cpu architecture of the fetched image
- use `nix-prefetch-docker` to get the required information
    - `nix run nixpkgs.nix-prefetch-docker -c nix-prefetch-docker --image-name mysql --image-tag 5`

## shadowSetup
- is a helper for setting ups he base filesystem for managing users and groups
- suitable for being used in a `buildImage.runAsRoot` script
- creates base files like `/etc/passwd` or /etc/login.defs` necessary for shadow-utils to manipulate users and groups
