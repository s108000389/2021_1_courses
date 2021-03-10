# Gnu as
```

```

# Gnu as @ 32bit Ubuntu 16.04 LTS
```
ksu@KSU-Ubuntu-1604-32:~$ gas -s
No command 'gas' found, did you mean:
 Command 'as' from package 'binutils' (main)
 Command 'gak' from package 'gui-apt-key' (universe)
 Command 'gs' from package 'ghostscript' (main)
 Command 'gap' from package 'gap-core' (universe)
 Command 'gaps' from package 'mummer' (universe)
 Command 'cas' from package 'amule-utils' (universe)
 Command 'gac' from package 'gap-dev' (universe)
 Command 'gjs' from package 'gjs' (universe)
 Command 'gss' from package 'libgss-dev' (universe)
 Command 'kas' from package 'openafs-kpasswd' (universe)
 Command 'gav' from package 'gav' (universe)
gas: command not found
ksu@KSU-Ubuntu-1604-32:~$ as -h
as: option '-h' is ambiguous; possibilities: '--hash-size' '--help'
ksu@KSU-Ubuntu-1604-32:~$ as --help
Usage: as [option...] [asmfile...]
Options:
  -a[sub-option...]	  turn on listings
                      	  Sub-options [default hls]:
                      	  c      omit false conditionals
                      	  d      omit debugging directives
                      	  g      include general info
                      	  h      include high-level source
                      	  l      include assembly
                      	  m      include macro expansions
                      	  n      omit forms processing
                      	  s      include symbols
                      	  =FILE  list to FILE (must be last sub-option)
  --alternate             initially turn on alternate macro syntax
  --compress-debug-sections[={none|zlib|zlib-gnu|zlib-gabi}]
                          compress DWARF debug sections using zlib
  --nocompress-debug-sections
                          don't compress DWARF debug sections [default]
  -D                      produce assembler debugging messages
  --debug-prefix-map OLD=NEW
                          map OLD to NEW in debug information
  --defsym SYM=VAL        define symbol SYM to given value
  --execstack             require executable stack for this object
  --noexecstack           don't require executable stack for this object
  --size-check=[error|warning]
			  ELF .size directive check (default --size-check=error)
  --sectname-subst        enable section name substitution sequences
  -f                      skip whitespace and comment preprocessing
  -g --gen-debug          generate debugging information
  --gstabs                generate STABS debugging information
  --gstabs+               generate STABS debug info with GNU extensions
  --gdwarf-2              generate DWARF2 debugging information
  --gdwarf-sections       generate per-function section names for DWARF line information
  --hash-size=<value>     set the hash table size close to <value>
  --help                  show this message and exit
  --target-help           show target specific options
  -I DIR                  add DIR to search list for .include directives
  -J                      don't warn about signed overflow
  -K                      warn when differences altered for long displacements
  -L,--keep-locals        keep local symbols (e.g. starting with `L')
  -M,--mri                assemble in MRI compatibility mode
  --MD FILE               write dependency information in FILE (default none)
  -nocpp                  ignored
  -o OBJFILE              name the object-file output OBJFILE (default a.out)
  -R                      fold data section into text section
  --reduce-memory-overheads 
                          prefer smaller memory use at the cost of longer
                          assembly times
  --statistics            print various measured statistics from execution
  --strip-local-absolute  strip local absolute symbols
  --traditional-format    Use same format as native assembler when possible
  --version               print assembler version number and exit
  -W  --no-warn           suppress warnings
  --warn                  don't suppress warnings
  --fatal-warnings        treat warnings as errors
  -w                      ignored
  -X                      ignored
  -Z                      generate object file even after errors
  --listing-lhs-width     set the width in words of the output data column of
                          the listing
  --listing-lhs-width2    set the width in words of the continuation lines
                          of the output data column; ignored if smaller than
                          the width of the first line
  --listing-rhs-width     set the max width in characters of the lines from
                          the source file
  --listing-cont-lines    set the maximum number of continuation lines used
                          for the output data column of the listing
  @FILE                   read options from FILE
  -Q                      ignored
  -V                      print assembler version number
  -k                      ignored
  -n                      Do not optimize code alignment
  -q                      quieten some warnings
  -s                      ignored
  --32/--64/--x32         generate 32bit/64bit/x32 code
  --divide                ignored
  -march=CPU[,+EXTENSION...]
                          generate code for CPU and EXTENSION, CPU is one of:
                           generic32, generic64, i386, i486, i586, i686,
                           pentium, pentiumpro, pentiumii, pentiumiii, pentium4,
                           prescott, nocona, core, core2, corei7, l1om, k1om,
                           iamcu, k6, k6_2, athlon, opteron, k8, amdfam10,
                           bdver1, bdver2, bdver3, bdver4, znver1, btver1,
                           btver2
                          EXTENSION is combination of:
                           8087, 287, 387, no87, mmx, nommx, sse, sse2, sse3,
                           ssse3, sse4.1, sse4.2, sse4, nosse, avx, avx2,
                           avx512f, avx512cd, avx512er, avx512pf, avx512dq,
                           avx512bw, avx512vl, noavx, vmx, vmfunc, smx, xsave,
                           xsaveopt, xsavec, xsaves, aes, pclmul, fsgsbase,
                           rdrnd, f16c, bmi2, fma, fma4, xop, lwp, movbe, cx16,
                           ept, lzcnt, hle, rtm, invpcid, clflush, nop, syscall,
                           rdtscp, 3dnow, 3dnowa, padlock, svme, sse4a, abm,
                           bmi, tbm, adx, rdseed, prfchw, smap, mpx, sha,
                           clflushopt, prefetchwt1, se1, clwb, pcommit,
                           avx512ifma, avx512vbmi, clzero, mwaitx, ospke
  -mtune=CPU              optimize for CPU, CPU is one of:
                           generic32, generic64, i8086, i186, i286, i386, i486,
                           i586, i686, pentium, pentiumpro, pentiumii,
                           pentiumiii, pentium4, prescott, nocona, core, core2,
                           corei7, l1om, k1om, iamcu, k6, k6_2, athlon, opteron,
                           k8, amdfam10, bdver1, bdver2, bdver3, bdver4, znver1,
                           btver1, btver2
  -msse2avx               encode SSE instructions with VEX prefix
  -msse-check=[none|error|warning]
                          check SSE instructions
  -moperand-check=[none|error|warning]
                          check operand combinations for validity
  -mavxscalar=[128|256]   encode scalar AVX instructions with specific vector
                           length
  -mevexlig=[128|256|512] encode scalar EVEX instructions with specific vector
                           length
  -mevexwig=[0|1]         encode EVEX instructions with specific EVEX.W value
                           for EVEX.W bit ignored instructions
  -mevexrcig=[rne|rd|ru|rz]
                          encode EVEX instructions with specific EVEX.RC value
                           for SAE-only ignored instructions
  -mmnemonic=[att|intel]  use AT&T/Intel mnemonic
  -msyntax=[att|intel]    use AT&T/Intel syntax
  -mindex-reg             support pseudo index registers
  -mnaked-reg             don't require `%' prefix for registers
  -mold-gcc               support old (<= 2.8.1) versions of gcc
  -madd-bnd-prefix        add BND prefix for all valid branches
  -mshared                disable branch optimization for shared code
  -momit-lock-prefix=[no|yes]
                          strip all lock prefixes
  -mrelax-relocations=[no|yes]
                          generate relax relocations
  -mamd64                 accept only AMD64 ISA
  -mintel64               accept only Intel64 ISA

Report bugs to <http://www.sourceware.org/bugzilla/>

```
