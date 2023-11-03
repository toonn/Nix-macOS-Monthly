# October 2023

[The stdenv LLVM bump](https://github.com/NixOS/nixpkgs/pull/241692) was merged. It introduced [some issues but they're being addressed](https://github.com/NixOS/nixpkgs/issues/234710). [The cross-compilation PR](https://github.com/NixOS/nixpkgs/pull/256590) is still open, but, currently fixes required due to the bump are prioritized.

The patch for [issue #150655](https://github.com/NixOS/nixpkgs/issues/150655) broke the binutils build because of unused argument warnings, which cause its configure script to misdetect the presence of standard library headers. I'm still looking into the linker-side of things, the current patch only addresses the compiler-side. I will also continue with the Compression framework, to unblock newer `system_cmds` and then the stdenv work.
