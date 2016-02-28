Apply the patches for both llvm and compiler-rt, targeting ver. 3.7.1.

The BitMask implementation for tsan will print statistics at tsan exit. Currently only the PC address will be listed. If you need to get the file name and line number, run addr2line.

The Adhoc filter requires a file containing the list of synchronization variable pairs to be specified as TSAN_ADHOC_LIST environment variable. The format of the format of the pair will be:

(filename: lineno) (filename: lineno)
