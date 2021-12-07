# November 2021

At the start of the month I was spending time on getting the SDK bump to work
on LLVM 7, this was not fruitful and the only reason was making the 21.11
cut-off deadline so I dropped it. Instead I finished up work on the LLVM 11
bump, which has been merged to staging. Stabilizing is ongoing on staging-next
to shake out any remaining problems, like [breaking MariaDB because it was
updated](https://github.com/NixOS/nixpkgs/pull/149096).

[Domen's call for Darwin
maintainers](https://github.com/NixOS/nixpkgs/issues/145230) had a good
response. The [darwin-maintainers
team](https://github.com/orgs/NixOS/teams/darwin-maintainers) has grown to
almost 40 people, this should help with both response times and number of
eyeballs on any Darwin issues that pop up. [Five new Darwin builders were added
to OfBorg](https://github.com/NixOS/nixos-org-configurations/issues/179) to
help with Darwin maintenance, very useful for maintainers without access to a
Darwin system. These builders are sponsored by
[MacStadium](https://www.macstadium.com/).

@pxc asked me to shout out [@bergkvist's work on generating small binary
wrappers](https://github.com/NixOS/nixpkgs/pull/124556/). Darwin does not allow
for interpreted scripts to be used as shebang interpreters. Using a binary
wrapper for programs that are commonly used as shebang interpreters, like
Python, Perl or Ruby, would workaround this limitation.
