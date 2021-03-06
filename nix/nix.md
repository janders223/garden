---
date: 2021-07-25T19:03
---

# nix

- Nix is a tool that takes a unique approach to package management and system configuration. Learn how to make reproducible, declarative and reliable systems.
- Reproducible
  - Nix builds packages in isolation from each other. This ensures that they are reproducible and don't have undeclared dependencies, so **if a package works on one machine, it will also work on another**.
- Declarative
  - Nix makes it **trivial to share development and build environments** for your projects, regardless of what programming languages and tools you’re using.
- Reliable
  - Nix ensures that installing or upgrading one package **cannot break other packages**. It allows you to **roll back to previous versions**, and ensures that no package is in an inconsistent state during an upgrade.
- Always working development environment.
  - **Nix provides developers with a \*\***complete and consistent development environment\***\*. Stop worrying how to install dependencies for your project.**
  - https://nixos.org/guides/how-nix-works.html#complete-dependencies
  - With Nix, a build process only has access to dependencies that have been declared explicitly. So if a build succeeds, you know you've specified all necessary dependencies.
  - The same build process specification can be used to start a development environment (optionally augmented with additional development tools).
  - You will no longer have to hear: **But it works on my machine!**
- One tool, many languages.
  - **With today's polyglot development environments, each language has its own way of building and testing. Encourage cross-team development by providing a single way of building everything.**
  - https://nixos.org/guides/how-nix-works.html#multiple-versions
  - https://nixos.org/guides/how-nix-works.html#portable
  - Instead of complicated installation instructions, with Nix the development environment is always only one command away. And that is without using Docker or any other virtualization.
  - Language specific package managers are good at dependencies in their specific language. But they cannot provide other dependencies, like the ones you would usually have to install system-wide.
- Continuous integration for free.
  - Your development environment is your continuous integration environment. The same environment always and everywhere.
  - https://nixos.org/guides/continuous-integration-github-actions.html
  - Being able to fix broken continuous integration runs is great, but being able to fix problems locally, before pushing, is priceless.
  - Trying to keep system dependencies of development environments in sync with continuous integration is a disaster waiting to happen. **Don't wait for the disaster, prevent it**.
- From zero to cloud.
  - Use the same tool to build projects, configure machines and deploy to the cloud.
  - https://nixos.org/learn.html
  - https://nixos.org/guides/building-and-running-docker-images.html
  - https://nixos.org/guides/how-nix-works.html#nixos
  - Using one tool to develop, test and build Amazon EC2, Google Cloud, Azure, Virtualbox, KVM and other images in a declarative way is a DevOps dream.
  - Forget `Dockerfiles` s and build docker images with Nix in a declarative and efficient way. **Nix and Docker is a match made in heaven.**
- Is the previous version better? Roll back anytime.
  - Always be able to roll back to the version that you want. Never end up with a broken system.
  - https://nixos.org/guides/how-nix-works.html#atomic
  - https://nixos.org/guides/how-nix-works.html#garbage-collection
  - https://nixos.org/guides/how-nix-works.html#atomic
  - https://nixos.org/guides/how-nix-works.html#multiple-versions
  - Nix never overwrites files, but just adds new versions in different paths.
  - And since nothing is overwritten, the old versions are still there after an upgrade. This means that you can quickly roll back to the old version.
- Experiment without fear.
  - https://nixos.org/guides/how-nix-works.html#atomic
  - https://nixos.org/guides/how-nix-works.html#multiple-versions
  - There should be no fear of breaking your system when experimenting with new software. We all learn best when we play around.
  - Install new software without risk of things breaking. Nix prevents conflicts not only between multiple development environments, but also with the operating system. Your work environment will stay intact, but allows you to experiment in a safe way.
  - No need to turn your system upside down just because you want to test some experimental and bleeding edge versions of software.
- Contributing is only a pull request away.

  - Community is at the core of Nix. Collaboration is encouraged by providing a low barrier to contribute and bots to guide contributors through the process.
  - https://nixos.org/community/index.html
  - https://nixos.org/guides/contributing.html
  - https://github.com/NixOS/nixpkgs
  - Development of Nix, the Nix packages collection and the NixOS Linux distribution happens on GitHub. To contribute to any of the Nix projects, just open a pull request on GitHub. The bots and community members will guide you through the process to ensure quality.

---

- [[nix language]]#
- [[nix package manager]]#
- [[pinning nixpkgs]]#
- [[nix hydra]]#
- [[docker tools]]#
- [[building docker images]]#
- [[cheap docker images]]#
