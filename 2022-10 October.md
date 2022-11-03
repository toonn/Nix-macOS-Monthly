# October 2022

The availability attribute I started using [here](https://github.com/toonn/nixpkgs/commit/d4d6f4c65a81a5b4299f9f03d9fd12d2ebd97b0c) is not compatible with GCC. This didn't really come up before because Darwin stdenv uses Clang. However, many packages in Nixpkgs do use GFortran, which is really GCC so it did come up in the Hydra evaluation. The way to support availability macros for GCC is simply to go with Apple's older approach of having macros for all the various combinations of versions.

I want to highlight @stephank's work [bringing Swift to Darwin](https://github.com/NixOS/nixpkgs/pull/189977). It's a big change so more eyes to help along the review would be welcome.
