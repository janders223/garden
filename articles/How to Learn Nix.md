# How to Learn Nix

## Ian Henry

#articles
#mobile_share

![](https://readwise-assets.s3.amazonaws.com/static/images/default-book-icon-1.a08c56e2fedd.png)

### Highlights from July 26, 2021

- derivation
  A description of a build action. The result of a derivation is a store object. Derivations are typically specified in Nix expressions using the derivation primitive. These are translated into low-level store derivations (implicitly by nix-env and nix-build, or explicitly by nix-instantiate).
- store
  The location in the file system where store objects live. Typically /nix/store.
- store path
  The location in the file system of a store object, i.e., an immediate child of the Nix store directory.
- store object
  A file that is an immediate child of the Nix store directory. These can be regular files, but also entire directory trees. Store objects can be sources (objects copied from outside of the store), derivation outputs (objects produced by running a build action), or derivations (files describing a build action).
- Nix expression
  A high-level description of software packages and compositions thereof. Deploying software using Nix entails writing Nix expressions for your packages. Nix expressions are translated to derivations that are stored in the Nix store. These derivations can then be built.
- user environment
  An automatically generated store object that consists of a set of symlinks to “active” applications, i.e., other store paths. These are generated automatically by nix-env.
- $ nix-env -qa
  The -q flag is for “query” and not “quiet” as I would assume from every other CLI I have ever used. Similarly a does not stand for --all but --available.
- $ nix search git -u
  * nixpkgs.act (act-0.2.20)
  Run your GitHub Actions locally
  * nixpkgs.argocd (argocd-1.8.4)
  Argo CD is a declarative, GitOps continuous delivery tool for Kubernetes
  * nixpkgs.axoloti (axoloti-1.0.12-2)
  Sketching embedded digital audio algorithms. To fix permissions of the Axoloti USB device node, add a similar udev rule to <literal>services.udev.extraRule
  s</literal>: <literal>SUBSYSTEM=="usb", ATTR{idVendor}=="16c0", ATTR{idProduct}=="0442", OWNER="someuser", GROUP="somegroup"</literal>
  (much more output elided)
- temporarily override my ~/.nix-profile by setting nix-env --profile my/custom/path
- A Nix channel is just a URL that points to a place that contains a set of Nix expressions and a manifest.
- this is the syntax for function invocation. This is just a function call. stdenv.mkDerivation is the function, and the thing delimited by the curly braces is the argument. This is totally normal syntax in Haskell or OCaml or whatever, but I suspect that is totally not obvious if you’re coming from a “normal” language. In JavaScript, this would be stdenv.mkDerivation({ ... }). It’s just that in (this particular family of) “functional programming languages,” people don’t use the parens. There is a very good reason that it is this way, and that reason is called currying. I don’t know if Nix has curried functions or not, or if functions can only have one argument for other reasons, or what. I’m new here too. Just saying that as background, because it seems like the manual assumes you understand that this is a function call.
- Nixpkgs has a convenience function callPackage that imports and calls a function, filling in any missing arguments by passing the corresponding attribute from the Nixpkgs set, like this:
  hello = callPackage ../applications/misc/hello/ex-1 { };
  If necessary, you can set or override arguments:
  hello = callPackage ../applications/misc/hello/ex-1 { stdenv = myStdenv; };
- The Nix expression language is a pure, lazy, functional language.
- Sets are really the core of the language, since ultimately the Nix language is all about creating derivations, which are really just sets of attributes to be passed to build scripts.
