# July 2023

[The stdenv LLVM bump](https://github.com/NixOS/nixpkgs/issues/234710) is still in need of more reviews. @reckenrode is also working on [fixing cross-compilation from aarch64-darwin to x86_64-darwin](https://github.com/NixOS/nixpkgs/pull/256590).

All the dependencies of the bootstrap-tools are split into branches. The other source releases should be buildable against the new bootstrap-tools and avoid a needless rebuild later. I have a patch for [issue #150655](https://github.com/NixOS/nixpkgs/issues/150655), however, it makes the binutils build fail and that's pretty low down in the dependency chain and I've been focusing on the prerequisite PRs for the LLVM bump instead. I'm also trying to add the Compression framework to the SDKs, which is needed for newer `system_cmds`, but running into needing newer darwin-stubs. Either those need a new release or we can switch to fetching the repo instead.
