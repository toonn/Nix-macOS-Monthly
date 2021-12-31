# December 2021

The LLVM bump caused a couple regressions on aarch64-darwin because of generic `isDarwin` guards I removed but these were rather easily fixed. With the LLVM bump completed I've been able to focus on the SDK bump. After rebasing libuv stopped building and it's a dependency of the bootstrap-tools. I found and fixed the problem this week and am now at the point where I can try out substituting parts of the SDK distributed by Apple for open source releases that don't build. This should unblock the SDK bump and allow us to move forward.
