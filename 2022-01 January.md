# January 2022

I set out to substitute configd with the SystemConfiguration framework from the
SDK. This means the framework and its dependencies need to build from the
bootstrap-tools so I had to add `print-reexports` to the bootstrap tarball.
Then I ran into the familiar issue with XNU no longer providing all the
availability macros and I set out to patch the affected parts of the SDK. After
making headway through two or three frameworks the realization of how many
locations that would need to be patched set in so I needed a different
approach. I've opted to patch `Availability.h` to redefine availability macros
in terms of the modern `__API_AVAILABLE` style of macros, which are backed by
the
[`availability` attribute](https://releases.llvm.org/11.0.1/tools/clang/docs/AttributeReference.html#availability)
provided by modern compilers. This means we give up the ability to compile
things on Darwin that make use of the source releases with older compilers.
Next step is figuring out why PCRE doesn't have pthreads available anymore when
being built in stage 3.