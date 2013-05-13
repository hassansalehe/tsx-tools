![tsx-tools](http://halobates.de/tsx-tools.png)

# Useful TSX related tools

TSX (Intel Transactional Synchronization Extension) is a hardware transactional memory in recent Intel CPU codenamed Haswell. For more information see http://en.wikipedia.org/wiki/Transactional_Synchronization_Extensions

This package provides some tools for TSX development.

## ignore-xend.so

When running with the RTM enabled glibc unlocking and unlocked lock causes 
a general protection fault. Normal glibc ignores those.
This LD_PRELOAD catches these faults and allows the buggy programs to run.
May also be useful with older RTM based lock libraries.

LD_PRELOAD=/path/to/ignore-xend.so program 

## remove-hle.py

Remove HLE prefixes from a binary. Useful for verifying that a problem
happens without HLE too. First run without -p and verify the patch sites,
then use with -p binary to patch.

Warning: this can destroy a binary since there can be false positives.
Always run on a backup copy.

## tsx-assert 

A facility to do asserts in transactions.
Requires a special hook into the elided lock library
