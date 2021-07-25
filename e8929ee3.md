---
date: 2021-07-25T19:03
---

# Pinning nixpkgs

Until flakes are stable, this is the most reliable way to pin nixpkgs to
a certain version. Of course it is also possible to use [niv](https://github.com/nmattia/niv).

https://nix.dev/tutorials/towards-reproducibility-pinning-nixpkgs.html#pinning-nixpkgs

### Options
#### A
```nix
{ pkgs ? import (fetchTarball "https://github.com/NixOS/nixpkgs/archive/3590f02e7d5760e52072c1a729ee2250b5560746.tar.gz") {}
}:

...
```
#### B
use [niv](https://github.com/nmattia/niv)
```nix
{ sources ? import ./nix/sources.nix
, pkgs ? import sources.nixpkgs {}
}:

...
```
#### C
- [[cb49a6c9]]
