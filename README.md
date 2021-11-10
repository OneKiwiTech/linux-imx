# linux-imx

## Download Toolchain
- `cd`
- `mkdir toolchain`
- `cd toolchain`
- `wget -c https://releases.linaro.org/components/toolchain/binaries/7.3-2018.05/aarch64-linux-gnu/gcc-linaro-7.3.1-2018.05-x86_64_aarch64-linux-gnu.tar.xz`
- `tar -xvf gcc-linaro-7.3.1-2018.05-x86_64_aarch64-linux-gnu.tar.xz`

## Get and build linux kernel
- `git clone https://github.com/km-tek/linux-imx -b lf-5.10.y`
- `cd linux-imx`
- `export ARCH=arm64`
- `export CROSS_COMPILE=~/toolchain/gcc-linaro-7.3.1-2018.05-x86_64_aarch64-linux-gnu/bin/aarch64-linux-gnu-`
- `make distclean`
- `make imx_v8_defconfig`
- `make -j8` This will generate linux kernel ('Image') and device-tree binary ('*.dtb') files.
- After you generated the kernel, you might want to build the kernel-modules:
```
    arch/arm64/boot/Image
    arch/arm64/boot/dts/freescale/*.dtb
```
- After you generated the kernel, you might want to build the kernel-modules:
```
    linux-imx$ make modules
    linux-imx$ make modules_install INSTALL_MOD_PATH=~/linux-imx-modules
```