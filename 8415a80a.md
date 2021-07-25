---
date: 2021-07-25T19:01
---

# nix package manager

- The Nix Packages collection (Nixpkgs)[https://github.com/NixOS/nixpkgs] is a set of *over 80 000 packages* for the Nix package manager.
- https://wiki.nikitavoloboev.xyz/package-managers/nix
- https://github.com/justinwoo/nix-shorts
- https://github.com/noteed/nix-notes
- Nix never uses host dependencies instead building with precise dependencies every time
- Changes can be rolled back atomically
- mixing and matching with domain specific package managers is possible, though best avoided
- does not solve dependency resolution, only pinning
- What makes Nix so peculiar is that it doesn't seem to aim at implementing specific functionality, instead implementing primitives that make this functionality trivial.
- a radical simplification of a whole slew of build system and package management tooling
- can be extremely puzzling for beginners
