# Decompiling from Machine Code into LLVM-IR

* https://github.com/decomp/decompilation

* https://github.com/trailofbits/mcsema (last update: 1 month ago) ([video presentation](https://www.youtube.com/watch?v=nW9bE5tUVYg))

* https://github.com/draperlaboratory/fracture (last update: 3 months ago)

* https://github.com/jcdutton/libbeauty (last update: 11 months ago)

* http://dagger.repzret.org/ (last update: 1 year ago as taken from the news) ([presentation](http://llvm.org/devmtg/2013-04/bougacha-slides.pdf))

# Decompiling from LLVM-IR into other languages

**Can we revert the translation from LLVM-IR into the source language?** In general, **no** because the *translation is lossy*, so the IR does not include enough information to reconstruct the original code.

Additionally, there are hardly any compilers from IR into other languages. The two most well known reverse-compilers are: [llvm-cbe](https://github.com/draperlaboratory/llvm-cbe), and [emscripten](https://github.com/kripken/emscripten). Note, however, that both of these projects do not aim to *reconstruct* code, and are instead simple compiler.

References:

* [Design of a Retargetable Decompiler for a Static Platform-Independent Malware Analysis](http://www.sersc.org/journals/IJSIA/vol5_no4_2011/8.pdf)
* [LLVM-C backend](https://github.com/draperlaboratory/llvm-cbe) aka LLVM-IR to C
* [How to convert llvm IR to c code?](http://stackoverflow.com/questions/8563670/)
* [llvm ir back to human-readable source language?](http://stackoverflow.com/questions/5180914/)
* [Re-generating source code from LLVM parse tree?](http://stackoverflow.com/questions/23296823/)
* [LLVM IR is a poor system for building a Platform](http://lists.cs.uiuc.edu/pipermail/llvmdev/2011-October/043719.html)

>  Apple has some LLVM IR transformations for Objective-C, however
> the transformations have to reverse-engineer the high-level semantics
> out of the lowered code, which is awkward. Further, they're
> reasoning about high-level semantics in a way that isn't guaranteed
> to be safe by LLVM IR rules alone. It works for the kinds of code
> clang generates for Objective C, but it wouldn't necessarily be
> correct if run on code produced by other front-ends. LLVM IR
> isn't capable of representing the necessary semantics for this
> unless we start embedding Objective C into it.

Source: [LLVM IR is a poor system for building a Platform](http://lists.cs.uiuc.edu/pipermail/llvmdev/2011-October/043719.html)

# See also

* http://www.phatcode.net/res/228/files/decompilation_thesis.pdf
