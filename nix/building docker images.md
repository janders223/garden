---
date: 2021-07-25T18:28
---

# Building and Running Docker Images with nix

Use nix to reliably and repeatedly build docker images.

```nix
{ pkgs ? import <nixpkgs> { system = "x86_64-linux"; } }:

pkgs.dockerTools.buildImage {
  name = "hello-docker";
  config = {
    Cmd = [ "${pkgs.hello}/bin/hello" ];
  };
}
```

Then run:
1. `nix-build hello-docer.nix`
1. `docker load < result`

Or:

1. `docker load < $(nix-build hello-docker.nix)`

See [[docker tools]] for more notes or the [manual](https://nixos.org/guides/building-and-running-docker-images.html) for more information
