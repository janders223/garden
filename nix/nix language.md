---
date: 2021-07-25T18:58
---

# nix language

- turing complete language used to define builds and configurations
- an expression based programming language where each program evaluates to 
- Nix language anti-patterns
    - Unquoted URLS
        - syntax supports urls verbatim
        - `https://example.com` instead of `"https://example.com"`
        - [RFC 45](https://github.com/NixOS/rfcs/pull/45) was accepted to deprecate this feature
    - rec {…} expression
        - `rec` allows for recursive reference of variables within an expression
            ```nix
            rec {
            a = 1;
            b = a + 2;
            }```
        - evaluates to `{a = 1; b = 3; }`
        - it is possible to introduce infinite recursion errors when shadowing a variable
        - combining with `overrideAttrs` has a surprising behavior of __not__ overriding every reference
        - prefer `let .. in` syntax
        ```nix
            let
            a = 1;
            in {
            a = a;
            b = a + 2;
            }```
    - with attrset; … expression
        - static analysis tools cannot reason about this code
        - multiple `with` statements confuse about which variables are in scope
        - scoping rules are not intuitive
        ```nix
            # instead of:
            with (import <nixpkgs> {});

            # try this instead:
            let
            pkgs = import <nixpkgs> {};
            inherit (pkgs) curl jq;
            in ...
            # instead of:
            buildInputs = with pkgs; [ curl jq ];

            # try this instead:
            buildInputs = builtins.attrValues {
            inherit (pkgs) curl jq;
            };

            # or this:
            buildInputs = lib.attrVals ["curl" "jq"] pkgs
            ```
    - <…> search path
        - developers are likely to have nixpkgs point to different revisions
        - see [[pinning nixpkgs]]
    - attr1 // attr2 merge operator
        - does not merge nested attributes sets
        - better to use `pkgs.lib.recursiveUpdate`
        - 
