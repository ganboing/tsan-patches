Apply the patches for both llvm and compiler-rt, targeting ver. 3.7.1
Assuming you have initialized or cloned the git repo at ${llvm-src} and ${llvm-src}/projects/compiler-rt

    cd ${llvm-src}
    git am llvm.patch
    cd ${llvm-src}/projects/compiler-rt
    git am compiler-rt.patch

You can update the patch repo by

    cd ${llvm-src}
    git format-patch ${llvm-init-commit}..HEAD --stdout > llvm.patch
    cd ${llvm-src}/projects/compiler-rt
    git format-patch ${compiler-rt-init-commit}..HEAD --stdout > compiler-rt.patch

Where the ${llvm-init-commit} is the commit specification of the commit right before my tsan patch commits at your llvm repo. If you cloned from the llvm official repo, aka http://llvm.org/git/llvm.git, please replase the ${llvm-init-commit} by release\_37, as you should have checked out the release\_37 branch and applied the tsan-patches on it. Otherwise if you created the git repo yourself, you may replace ${llvm-init-commit} by your git commit sha1 or tag/branch name right before applying the tsan-patches. So you may create a tag at your current commit just for your convenience.

Same applies for ${compiler-rt-init-commit}

--

The BitMask implementation for tsan will print statistics at tsan exit. Currently only the PC address will be listed. If you need to get the file name and line number, run addr2line.

The Adhoc filter requires a file containing the list of synchronization variable pairs to be specified as TSAN_ADHOC_LIST environment variable. The format of the format of the pair will be:

(filename: lineno) (filename: lineno)
