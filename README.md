# pico-coremark

Setup

```bash
git clone https://github.com/eembc/coremark.git
git clone https://github.com/owhinata/pico-coremark.git
```

Build

```bash
PICO_SDK_PATH=$(pwd)/pico-sdk cmake pico-coremark \
-Bbuild -GNinja -DCMAKE_EXPORT_COMPILE_COMMANDS=ON \
-DPICO_BOARD=pico2_w \
-DPICO_STDIO_USB=1 \
-DPICO_STDIO_UART=0

cmake --build build
```

Result

```
2K performance run parameters for coremark.
CoreMark Size    : 666
Total ticks      : 23342520
Total time (secs): 23.342520
Iterations/Sec   : 428.402760
Iterations       : 10000
Compiler version : GCC10.3.1 20210824 (release)
Compiler flags   :  -O3 -Wall -Wextra
Memory location  : STACK
seedcrc          : 0xe9f5
[0]crclist       : 0xe714
[0]crcmatrix     : 0x1fd7
[0]crcstate      : 0x8e3a
[0]crcfinal      : 0x988c
Correct operation validated. See README.md for run and reporting rules.
CoreMark 1.0 : 428.402760 / GCC10.3.1 20210824 (release)  -O3 -Wall -Wextra / STACK
```