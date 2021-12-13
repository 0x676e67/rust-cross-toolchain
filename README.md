# rust-cross-toolchain

- [Platform Support](#platform-support)
  - [Linux (GNU)](#linux-gnu)
  - [Linux (musl)](#linux-musl)
  - [Linux (uClibc)](#linux-uclibc)
  - [FreeBSD](#freebsd)
  - [NetBSD](#netbsd)
  - [OpenBSD](#openbsd)
  - [DragonFly BSD](#dragonfly-bsd)
  - [Solaris](#solaris)
  - [illumos](#illumos)
  - [Redox](#redox)
  - [WASI](#wasi)
  - [Emscripten](#emscripten)
  - [Windows (GNU)](#windows-gnu)

## Platform Support

### Linux (GNU)

| libc | GCC | clang | C++ | test | host |
| ---- | --- | ----- | --- | ---- | ---- |
| glibc [1] | [1] | host | ✓ (libstdc++) | ✓ (qemu-user) [2] | [1] |

[1] See target list below for details<br>
[2] Except for powerpc-unknown-linux-gnuspe, riscv32gc-unknown-linux-gnu, and x86_64-unknown-linux-gnux32<br>

([Dockerfile](docker/linux-gnu.Dockerfile))

**Supported targets**:

| target | glibc | GCC | host |
| ------ | ----- | --- | ---- |
| `aarch64-unknown-linux-gnu` | 2.27 | 7.4.0 | x86_64 linux (glibc 2.27+) |
| `aarch64_be-unknown-linux-gnu` (tier3) | 2.31 | 10.2.1 |x86_64 linux (glibc 2.27+) |
| `arm-unknown-linux-gnueabi` | 2.27 | 7.4.0 | x86_64/aarch64 linux (glibc 2.27+) |
| `arm-unknown-linux-gnueabihf` | 2.24 | 9.4.0 | x86_64/aarch64 linux (glibc 2.27+) |
| `armv5te-unknown-linux-gnueabi` | 2.27 | 7.4.0 | x86_64/aarch64 linux (glibc 2.27+) |
| `armv7-unknown-linux-gnueabi` | 2.27 | 7.4.0 | x86_64/aarch64 linux (glibc 2.27+) |
| `armv7-unknown-linux-gnueabihf` | 2.27 | 7.4.0 | x86_64/aarch64 linux (glibc 2.27+) |
| `i586-unknown-linux-gnu` | 2.27 | 7.4.0 | x86_64/aarch64 linux (glibc 2.27+) |
| `i686-unknown-linux-gnu` | 2.27 | 7.4.0 | x86_64/aarch64 linux (glibc 2.27+) |
| `mips-unknown-linux-gnu` | 2.27 | 7.4.0 | x86_64 linux (glibc 2.27+) |
| `mips64-unknown-linux-gnuabi64` | 2.27 | 7.4.0 | x86_64 linux (glibc 2.27+) |
| `mips64el-unknown-linux-gnuabi64` | 2.27 | 7.4.0 | x86_64 linux (glibc 2.27+) |
| `mipsel-unknown-linux-gnu` | 2.27 | 7.4.0 | x86_64 linux (glibc 2.27+) |
| `mipsisa32r6-unknown-linux-gnu` (tier3) | 2.31 | 9.3.0 | x86_64 linux (glibc 2.31+) |
| `mipsisa32r6el-unknown-linux-gnu` (tier3) | 2.31 | 9.3.0 | x86_64 linux (glibc 2.31+) |
| `mipsisa64r6-unknown-linux-gnuabi64` (tier3) | 2.31 | 9.3.0 | x86_64 linux (glibc 2.31+) |
| `mipsisa64r6el-unknown-linux-gnuabi64` (tier3) | 2.31 | 9.3.0 | x86_64 linux (glibc 2.31+) |
| `powerpc-unknown-linux-gnu` | 2.27 | 7.4.0 | x86_64 linux (glibc 2.27+) |
| `powerpc-unknown-linux-gnuspe` (tier3) | 2.27 | 7.4.0 | x86_64 linux (glibc 2.27+) |
| `powerpc64-unknown-linux-gnu` | 2.27 | 7.4.0 | x86_64 linux (glibc 2.27+) |
| `powerpc64le-unknown-linux-gnu` | 2.27 | 7.4.0 | x86_64/aarch64 linux (glibc 2.27+) |
| `riscv32gc-unknown-linux-gnu` (tier3) | 2.33 | 11.1.0 | x86_64 linux (glibc 2.27+) |
| `riscv64gc-unknown-linux-gnu` | 2.27 | 7.4.0 | x86_64/aarch64 linux (glibc 2.27+) |
| `s390x-unknown-linux-gnu` | 2.27 | 7.4.0 | x86_64/aarch64 linux (glibc 2.27+) |
| `sparc64-unknown-linux-gnu` | 2.27 | 7.4.0 | x86_64 linux (glibc 2.27+) |
| `thumbv7neon-unknown-linux-gnueabihf` | 2.27 | 7.4.0 | x86_64/aarch64 linux (glibc 2.27+) |
| `x86_64-unknown-linux-gnu` | 2.27 | 7.4.0 | aarch64 linux (glibc 2.27+) |
| `x86_64-unknown-linux-gnux32` | 2.27 | 7.4.0 | x86_64/aarch64 linux (glibc 2.27+) |

### Linux (musl)

| libc | GCC | clang | C++ | test | host |
| ---- | --- | ----- | --- | ---- | ---- |
| musl 1.1.24 [1] [2] / 1.2.2 | 9.4.0 | host | ✓ (libstdc++) | ✓ (qemu-user) | x86_64 linux (any libc) |

[1] Default (see [libc#1848] for details)<br>
[2] With a patch that fixes CVE-2020-28928<br>

([Dockerfile](docker/linux-musl.Dockerfile))

[libc#1848]: https://github.com/rust-lang/libc/issues/1848

**Supported targets**:

- `aarch64-unknown-linux-musl`
- `arm-unknown-linux-musleabi`
- `arm-unknown-linux-musleabihf`
- `armv5te-unknown-linux-musleabi`
- `armv7-unknown-linux-musleabi`
- `armv7-unknown-linux-musleabihf`
- `i586-unknown-linux-musl`
- `i686-unknown-linux-musl`
- `mips-unknown-linux-musl`
- `mips64-unknown-linux-muslabi64`
- `mips64el-unknown-linux-muslabi64`
- `mipsel-unknown-linux-musl`
- `powerpc-unknown-linux-musl` (tier3)
- `powerpc64le-unknown-linux-musl` (tier3)
- `s390x-unknown-linux-musl` (tier3)
- `thumbv7neon-unknown-linux-musleabihf` (tier3)
- `x86_64-unknown-linux-musl`

### Linux (uClibc)

| libc | GCC | clang | C++ | test | host |
| ---- | --- | ----- | --- | ---- | ---- |
| uClibc-ng 1.0.34 | 10.2.0 | host [1] | ✓ (libstdc++) | ✓ (qemu-user) | x86_64 linux (glibc 2.27+) |

[1] It is not recommended to use clang for these targets at this time due to some bugs.

([Dockerfile](docker/linux-uclibc.Dockerfile))

**Supported targets**:

- `armv5te-unknown-linux-uclibceabi` (tier3)
- `armv7-unknown-linux-uclibceabihf` (tier3)
- `mips-unknown-linux-uclibc` (tier3)
- `mipsel-unknown-linux-uclibc` (tier3)

### FreeBSD

| libc | GCC | clang | C++ | test | host |
| ---- | --- | ----- | --- | ---- | ---- |
| freebsd [1] | N/A | host | ✓ (libc++) |  | x86_64/aarch64 linux (any libc) |

[1] See target list below for details<br>

([Dockerfile](docker/freebsd.Dockerfile))

**Supported targets**:

| target | version |
| ------ | ------- |
| `aarch64-unknown-freebsd` (tier3) | 12.2 (default), 13.0 |
| `i686-unknown-freebsd` | 12.2 (default), 13.0 |
| `powerpc-unknown-freebsd` (tier3) | 13.0 |
| `powerpc64-unknown-freebsd` (tier3) | 13.0 |
| `powerpc64le-unknown-freebsd` (tier3) | 13.0 |
| `x86_64-unknown-freebsd` | 12.2 (default), 13.0 |

### NetBSD

| libc | GCC | clang | C++ | test | host |
| ---- | --- | ----- | --- | ---- | ---- |
| netbsd [1] | 7.5.0 | host | ✓ (libstdc++) |  | x86_64 linux (glibc 2.27+) |

[1] See target list below for details<br>

([Dockerfile](docker/netbsd.Dockerfile))

**Supported targets**:

| target | version |
| ------ | ------- |
| `aarch64-unknown-netbsd` (tier3) | 9.2 |
| `armv6-unknown-netbsd-eabihf` (tier3) | 8.2 (default), 9.2 |
| `armv7-unknown-netbsd-eabihf` (tier3) | 8.2 (default), 9.2 |
| `i686-unknown-netbsd` (tier3) | 8.2 (default), 9.2 |
| `powerpc-unknown-netbsd` (tier3) | 8.2 (default), 9.2 |
| `sparc64-unknown-netbsd` (tier3) | 8.2 (default), 9.2 |
| `x86_64-unknown-netbsd` | 8.2 (default), 9.2 |

### OpenBSD

| libc | GCC | clang | C++ | test | host |
| ---- | --- | ----- | --- | ---- | ---- |
| openbsd 7.0 | N/A | host | ✓ (libc++) [1] |  | x86_64/aarch64 linux (any libc) |

[1] only i686 and x86_64<br>

([Dockerfile](docker/openbsd.Dockerfile))

**Supported targets**:

- `aarch64-unknown-openbsd` (tier3)
- `i686-unknown-openbsd` (tier3)
- `x86_64-unknown-openbsd` (tier3)

### DragonFly BSD

| libc | GCC | clang | C++ | test | host |
| ---- | --- | ----- | --- | ---- | ---- |
| dragonfly 6.0 | N/A | host (requires 13+) | ✓ (libstdc++) |  | x86_64/aarch64 linux (any libc) |

([Dockerfile](docker/dragonfly.Dockerfile))

**Supported targets**:

- `x86_64-unknown-dragonfly` (tier3)

### Solaris

| libc | GCC | clang | C++ | test | host |
| ---- | --- | ----- | --- | ---- | ---- |
| solaris 2.11 | 8.5.0 |  | ✓ (libstdc++) |  | x86_64 linux (glibc 2.27+) |

([Dockerfile](docker/solaris.Dockerfile))

**Supported targets**:

- `sparcv9-sun-solaris`
- `x86_64-pc-solaris`
- `x86_64-sun-solaris`

### illumos

| libc | GCC | clang | C++ | test | host |
| ---- | --- | ----- | --- | ---- | ---- |
| solaris 2.10 | 8.5.0 | host | ✓ (libstdc++) |  | x86_64 linux (glibc 2.27+) |

([Dockerfile](docker/illumos.Dockerfile))

**Supported targets**:

- `x86_64-unknown-illumos`

### Redox

| libc | GCC | clang | C++ | test | host |
| ---- | --- | ----- | --- | ---- | ---- |
| redox 0.6.0 | 8.2.0 | host | ✓ (libstdc++) |  | x86_64 linux (glibc 2.31+) |

([Dockerfile](docker/redox.Dockerfile))

<!--
TODO: I guess libc from https://static.redox-os.org/toolchain is for the latest version of redox, but I'm not 100% sure it is correct.
https://gitlab.redox-os.org/redox-os/redox/-/releases
-->

**Supported targets**:

- `x86_64-unknown-redox`

### WASI

| libc | GCC | clang | C++ | test | host |
| ---- | --- | ----- | --- | ---- | ---- |
| wasi-sdk 14 (wasi-libc ad51334) | N/A | 13.0.0 | ? (libc++) | ✓ (wasmtime) | x86_64 linux (glibc 2.27+) |

<!--
wasi-libc hash can be found here: https://github.com/WebAssembly/wasi-sdk/tree/wasi-sdk-14/src
-->

([Dockerfile](docker/wasi.Dockerfile))

**Supported targets**:

- `wasm32-wasi`

### Emscripten

| libc | GCC | clang | C++ | test | host |
| ---- | --- | ----- | --- | ---- | ---- |
| emscripten 1.39.20 | N/A |  | ? (libc++) | ✓ (node) | x86_64 linux (glibc 2.27+) |

([Dockerfile](docker/emscripten.Dockerfile))

**Supported targets**:

- `asmjs-unknown-emscripten`
- `wasm32-unknown-emscripten`

### Windows (GNU)

| libc | GCC | clang | C++ | test | host |
| ---- | --- | ----- | --- | ---- | ---- |
| Mingw-w64 7.0.0 | 9.3.0 | host | ✓ (libstdc++) | ✓ (wine) | [1] |

<!--
Mingw-w64 version: https://packages.ubuntu.com/en/focal/mingw-w64-common
GCC version: https://packages.ubuntu.com/en/focal/gcc-mingw-w64-base
-->

[1] See target list below for details<br>

([Dockerfile](docker/windows-gnu.Dockerfile))

**Supported targets**:

| target | host |
| ------ | ---- |
| `x86_64-pc-windows-gnu` | x86_64/aarch64 linux (glibc 2.31+) |
| `i686-pc-windows-gnu` | x86_64 linux (glibc 2.31+) |
