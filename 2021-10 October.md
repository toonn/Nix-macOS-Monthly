# October 2021

Up to this point I've been developing the Apple SDK bump on top of my [PR bumping LLVM in the x86_64 Darwin stdenv from 7 to 11](https://github.com/NixOS/nixpkgs/pull/126411), which is undergoing review now. However, NixOS seems to have a policy of not bumping major things, like the LLVM version, between releases within a year ([@sterni's comment on the PR](https://github.com/NixOS/nixpkgs/pull/126411#issuecomment-950128484)). This means the LLVM 11 bump will have to wait until after the 21.11 release has more or less been finalized. Once that's done we'll be able to work on [bumping the default LLVM for Linux too](https://github.com/NixOS/nixpkgs/pull/142593). Side Note: LLVM 13 is already on the horizon and Rust 1.56 depends on it. Rust has also become a dependency of Sphinx, through the Python cryptography library. Harmonizing with this version would avoid having to wait for two LLVM builds in Hydra evaluations, which would be great.

After finding out the LLVM bump couldn't make it into the next release I shifted my focus back to the Apple SDK bump, rebasing it on Nixpkgs without my LLVM bump. The intent was to make it possible to merge before the release and the next step was to add earlier unpacking of the SDK, so we can substitute parts of Apple's open source releases that do not build. This is where the first hurdle has come up. The Darwin stdenv depends on cmake, which depends on libuv and libuv's configure phase tries to compile a simple conftest and ld errors out on an absolute path to CoreFoundation, which seems to be passed in by clang. Apple SDK 10.13 switched to providing only `.tbd` files, no object files. This causes the linker to fail to find CoreFoundation at the absolute path. Clang 7 does support text-based stubs and libuv uses the recommended approach of using `dlopen()` to load dynamic libraries so seemingly this absolute path being passed to ld is all that's standing in the way of having it build. There's very little time left before the release and there's more work left to do getting the source releases to build. I'm going to focus on building the source releases with an LLVM 11 stdenv.

In other news, [RFC 112](https://github.com/NixOS/rfcs/pull/112) is proposing to demote x86_64 Darwin from Tier 2 to Tier 3 platform. There is no intent to decrease the support for Darwin but this would be a more honest reflection of the current status. Darwin CI is regularly running into problems where builders are idle but the queue runner isn't scheduling jobs for them. The main problem this causes is that some channel updates depend on a set of Darwin jobs passing and this ends up delaying the channel advance. In order to alleviate the parts of the issues raised that can be addressed by the community, Domen has started [a call for Darwin maintainers](https://github.com/NixOS/nixpkgs/issues/145230).

Nix 2.4 was released recently and it comes with installer improvements, especially on Darwin. Unfortunately it does have a [hard to debug issue](https://github.com/NixOS/nix/issues/3605) on Darwin. I'll be trying to find a way to reproduce this issue but extra eyes are needed.