# September 2022

[Latest evaluation](https://hydra.nixos.org/eval/1782462?compare=1782186#tabs-now-fail) still has many failing jobs. I included one too many changes from `darwin-stubs` and those will only start working once the corresponding Nixpkgs PR is merged. The [deadline for changes to release critical packages for 22.11](https://github.com/NixOS/nixpkgs/issues/194208) is coming up in less than two weeks. This doesn't leave enough time for thorough reviewing. So a bit of a false start but on the bright side this should be the last release window missed.  

Thanks to @a-m-joseph :heart: for fixing the bootstrap-tools SNAFU in [PR #183072](https://github.com/NixOS/nixpkgs/pull/183072), this change is currently making its way through staging. The `bootstrap-tools` are [failing on aarch64-darwin](https://hydra.nixos.org/eval/1782953?filter=bootstraptools&compare=1782933), which will block `nixpkgs-unstable` so there is more work to be done.
