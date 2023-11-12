# TetraNyoTengu
Fastest Scalar &amp; Vector memmem() in C - Linux/Windows tool

This is a practical console tool demonstarting how to use Fastest Needle-in-Haystack Searcher, written in C.
As a rival, 'ripgrep' latest version was used.

![NyoTengu_booklet pdf](https://github.com/Sanmayce/TetraNyoTengu/assets/14062548/f99f7034-97dc-4694-98cd-f0bc0ab5544c)

Bottom-line, first:
TetraNyoTengu (with 4 OpenMP threads, AVX2 variant) is roughly 0.575/0.059=9.74x faster than 'ripgrep' v13, C rules.

TetraNyoTengu (compiled with GCC v11.3.0 compiler) reaches (on laptop with i5-7200U, DDR4 2133MHz, Windows 10):

- 10,669,926,015 bytes/second with VECTOR code, single-threaded
- 9,214,936,103 bytes/second with SCALAR code, single-threaded
- 22.40 GiB/s with VECTOR code, tetra-threaded
- 18.61 GiB/s with SCALAR code, tetra-threaded
- 27,461 MB/s MAX Memory Read (reported by AIDA)

```
D:\Benchmark_Linus-Torvalds_SCALAR-VECTOR_2023>timer64 TetraNyoTengu_YMM_GCC11.3.0_64bit.exe linux-6.6.1.tar needle1.txt
___________          __                    _______                   ___________
\__    ___/  ____  _/  |_ _______ _____    \      \   ___.__.  ____  \__    ___/  ____    ____     ____   __ __
  |    |   _/ __ \ \   __\\_  __ \\__  \   /   |   \ <   |  | /  _ \   |    |   _/ __ \  /    \   / ___\ |  |  \
  |    |   \  ___/  |  |   |  | \/ / __ \_/    |    \ \___  |(  <_> )  |    |   \  ___/ |   |  \ / /_/  >|  |  /
  |____|    \___  > |__|   |__|   (____  /\____|__  / / ____| \____/   |____|    \___  >|___|  / \___  / |____/
                \/                     \/         \/  \/                             \/      \/ /_____/
TNT a.k.a. TetraNyoTengu a.k.a. 'SHETENGU' - the skydogess exact searcher, written by Kaze, 2023-Nov-11, for contacts: sanmayce@sanmayce.com
Current priority class is REALTIME_PRIORITY_CLASS.
Needle = Linus Torvalds
Allocating Source-Buffer 1,419,100,160 bytes ... OK
Memory pool starting address: 000002E94CC95040 ... 32 byte aligned, OK
Memory pool starting address: 000002E94CC95040 ... 64 byte aligned, OK
Searching into Haystack (1,419,100,160) for all occurrences of Needle (14) with fastest (known to me) SCALAR memmem() - 'Railgun_Trolldom_64' ...
Hits: 609
Search took 0.154 seconds.
Pure Search Performance: 9,214,936,103 bytes/second.
Searching (single-threaded) into Haystack (1,419,100,160) for all occurrences of Needle (14) with fastest (known to me) VECTOR memmem() - 'Railgun_Nyotengu_YMM' ...
Hits: 609
Search took 0.133 seconds.
Pure Search Performance: 10,669,926,015 bytes/second.
Searching into Haystack (1,419,100,160) for all occurrences of Needle (14) with fastest (known to me) VECTOR memmem() - 'Railgun_Nyotengu_YMM' ...
omp_get_num_procs( ) = 4
omp_get_max_threads( ) = 4
Enforcing 4 threads using 256bit vectors ...
First run: Hits: 609; Search took 0.061 seconds; Pure Search Performance: 21.67 GiB/s = 23,263,937,049 bytes/second.
Best run (of 11): Hits: 609; Search took 0.059 seconds; Pure Search Performance: 22.40 GiB/s = 24,052,545,084 bytes/second.
Searching into Haystack (1,419,100,160) for all occurrences of Needle (14) with fastest (known to me) SCALAR memmem() - 'Railgun_Trolldom_64' ...
omp_get_num_procs( ) = 4
omp_get_max_threads( ) = 4
Enforcing 4 threads using SCALAR 64bit code ...
First run: Hits: 609; Search took 0.074 seconds; Pure Search Performance: 17.86 GiB/s = 19,177,029,189 bytes/second.
Best run (of 11): Hits: 609; Search took 0.071 seconds; Pure Search Performance: 18.61 GiB/s = 19,987,326,197 bytes/second.

Kernel  Time =     0.562 =   24%
User    Time =     5.953 =  263%
Process Time =     6.515 =  288%    Virtual  Memory =   1358 MB
Global  Time =     2.258 =  100%    Physical Memory =   1358 MB
````

TetraNyoTengu (compiled with Intel v19.0 compiler) reaches (on laptop with i5-7200U, DDR4 2133MHz, Windows 10):

- 11,086,720,000 bytes/second with VECTOR code, single-threaded
- 9,096,795,897 bytes/second with SCALAR code, single-threaded
- 22.03 GiB/s with VECTOR code, tetra-threaded
- 21.67 GiB/s with SCALAR code, tetra-threaded
- 27,461 MB/s MAX Memory Read (reported by AIDA)

```
D:\Benchmark_Linus-Torvalds_SCALAR-VECTOR_2023>timer64 TetraNyotengu_YMM_IntelV190_64bit.exe linux-6.6.1.tar needle1.txt
___________          __                    _______                   ___________
\__    ___/  ____  _/  |_ _______ _____    \      \   ___.__.  ____  \__    ___/  ____    ____     ____   __ __
  |    |   _/ __ \ \   __\\_  __ \\__  \   /   |   \ <   |  | /  _ \   |    |   _/ __ \  /    \   / ___\ |  |  \
  |    |   \  ___/  |  |   |  | \/ / __ \_/    |    \ \___  |(  <_> )  |    |   \  ___/ |   |  \ / /_/  >|  |  /
  |____|    \___  > |__|   |__|   (____  /\____|__  / / ____| \____/   |____|    \___  >|___|  / \___  / |____/
                \/                     \/         \/  \/                             \/      \/ /_____/
TNT a.k.a. TetraNyoTengu a.k.a. 'SHETENGU' - the skydogess exact searcher, written by Kaze, 2023-Nov-11, for contacts: sanmayce@sanmayce.com
Current priority class is REALTIME_PRIORITY_CLASS.
Needle = Linus Torvalds
Allocating Source-Buffer 1,419,100,160 bytes ... OK
Memory pool starting address: 000001E780001040 ... 32 byte aligned, OK
Memory pool starting address: 000001E780001040 ... 64 byte aligned, OK
Searching into Haystack (1,419,100,160) for all occurrences of Needle (14) with fastest (known to me) SCALAR memmem() - 'Railgun_Trolldom_64' ...
Hits: 609
Search took 0.156 seconds.
Pure Search Performance: 9,096,795,897 bytes/second.
Searching (single-threaded) into Haystack (1,419,100,160) for all occurrences of Needle (14) with fastest (known to me) VECTOR memmem() - 'Railgun_Nyotengu_YMM' ...
Hits: 609
Search took 0.128 seconds.
Pure Search Performance: 11,086,720,000 bytes/second.
Searching into Haystack (1,419,100,160) for all occurrences of Needle (14) with fastest (known to me) VECTOR memmem() - 'Railgun_Nyotengu_YMM' ...
omp_get_num_procs( ) = 4
omp_get_max_threads( ) = 4
Enforcing 4 threads using 256bit vectors ...
First run: Hits: 609; Search took 0.063 seconds; Pure Search Performance: 20.98 GiB/s = 22,525,399,365 bytes/second.
Best run (of 11): Hits: 609; Search took 0.060 seconds; Pure Search Performance: 22.03 GiB/s = 23,651,669,333 bytes/second.
Searching into Haystack (1,419,100,160) for all occurrences of Needle (14) with fastest (known to me) SCALAR memmem() - 'Railgun_Trolldom_64' ...
omp_get_num_procs( ) = 4
omp_get_max_threads( ) = 4
Enforcing 4 threads using SCALAR 64bit code ...
First run: Hits: 609; Search took 0.064 seconds; Pure Search Performance: 20.65 GiB/s = 22,173,440,000 bytes/second.
Best run (of 11): Hits: 609; Search took 0.061 seconds; Pure Search Performance: 21.67 GiB/s = 23,263,937,049 bytes/second.

Kernel  Time =     0.593 =   26%
User    Time =     5.609 =  245%
Process Time =     6.203 =  271%    Virtual  Memory =   1360 MB
Global  Time =     2.281 =  100%    Physical Memory =   1359 MB
```

Latest superfast grep-like tool written in Rust:
```
D:\Benchmark_Linus-Torvalds_SCALAR-VECTOR_2023>timer64 "ripgrep-13.0.0-x86_64-pc-windows-gnu.exe" -c -F --stats "Linus Torvalds" linux-6.6.1.tar
609

609 matches
609 matched lines
1 files contained matches
1 files searched
0 bytes printed
17 bytes searched
0.463975 seconds spent searching
0.562452 seconds

Kernel  Time =     0.468 =   81%
User    Time =     0.093 =   16%
Process Time =     0.562 =   97%    Virtual  Memory =      5 MB
Global  Time =     0.575 =  100%    Physical Memory =   1360 MB
```

Enfun!
2023-Nov-12
Sanmayce
