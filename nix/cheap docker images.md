---
date: 2021-07-25T18:48
---

# Cheap Docker Images with nix

[source](http://lethalman.blogspot.com/2016/04/cheap-docker-images-with-nix_15.html)

```nix
{ pkgs ? import <nixpkgs> {} }:

with pkgs;
dockerTools.buildImage {
  name = "redis";
  runAsRoot = ''
    #!${stdenv.shell}
    ${dockerTools.shadowSetup}
    groupadd -r redis
    useradd -r -g redis -d /data -M redis
    mkdir /data
    chown redis:redis /data
  '';

  config = {
    Cmd = [ "${goPackages.gosu.bin}/bin/gosu" "redis" "${redis}/bin/redis-server" ];
    ExposedPorts = {
      "6379/tcp" = {};
    };
    WorkingDir = "/data";
    Volumes = {
      "/data" = {};
    };
  };
```
