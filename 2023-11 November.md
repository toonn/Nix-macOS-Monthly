# November 2023

Progress on the cc-wrapper fixes is slow, the large rebuilds make it hard to iterate. The Compression framework bump is currently stuck on a problem with the OpenDirectory framework.

I've opened an [overview issue for the first source release bumps](https://github.com/NixOS/nixpkgs/issues/273425). The intent is to introduce the new source releases alongside the old ones to enable review in small units and then switch over when everything's merged. I've left the PRs in draft for now in case we can come up with a better way than the nested attribute set in the source releases expression.
