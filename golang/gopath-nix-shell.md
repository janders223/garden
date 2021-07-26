---
date: 2021-07-26T19:02
---

# Setting `$GOPATH` in `nix-shell`

To make this a truly repeatable shell and keep packages in their respective project, set the `$GOPATH` to a relative directory. Also using the `curdir` variable to add the `$GOPATH/bin` to the `$PATH`.

```nix
{  pkgs ? import (fetchTarball "https://github.com/nixos/nixpkgs/archive/3590f02e7d5760e52072c1a729ee2250b5560746.tar.gz") {} }:

let
  curdir = builtins.getEnv "PWD";

in
with pkgs;

mkShell {
    nativeBuildInputs = [
      azure-cli
      go
      pulumi-bin
    ];

    GOPATH="${curdir}/.go";
    PATH="${curdir}/.go/bin:$PATH";
}
```

Also be sure to add the `$GOPATH` to the projects `.gitignore` file.

```shell
echo .go >> .gitignore
```
