# Decompiling from Machine Code into LLVM-IR

* https://github.com/decomp/decompilation

* https://github.com/trailofbits/mcsema (last update: 1 month ago) ([video presentation](https://www.youtube.com/watch?v=nW9bE5tUVYg))

* https://github.com/draperlaboratory/fracture (last update: 3 months ago)

* https://github.com/jcdutton/libbeauty (last update: 11 months ago)

* http://dagger.repzret.org/ (last update: 1 year ago as taken from the news) ([presentation](http://llvm.org/devmtg/2013-04/bougacha-slides.pdf))

# Decompiling from LLVM-IR into other languages

In general it is not possible, as translation is **lossy**, so the IR does not include enough information to reconstruct the original code.

Additionally, there are hardly any compilers from IR to other languages. The two most well known ones are: [llvm-cbe](https://github.com/draperlaboratory/llvm-cbe), and [emscripten](https://github.com/kripken/emscripten).

References:

* [Design of a Retargetable Decompiler for a Static Platform-Independent Malware Analysis](http://www.sersc.org/journals/IJSIA/vol5_no4_2011/8.pdf)
* [LLVM-C backend](https://github.com/draperlaboratory/llvm-cbe) aka LLVM-IR to C
* [How to convert llvm IR to c code?](http://stackoverflow.com/questions/8563670/)
* [llvm ir back to human-readable source language?](http://stackoverflow.com/questions/5180914/)
* [Re-generating source code from LLVM parse tree?](http://stackoverflow.com/questions/23296823/)
* [LLVM IR is a poor system for building a Platform](http://lists.cs.uiuc.edu/pipermail/llvmdev/2011-October/043719.html)

# See also

* http://www.phatcode.net/res/228/files/decompilation_thesis.pdf
