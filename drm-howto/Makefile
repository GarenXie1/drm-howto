FLAGS=`pkg-config --cflags --libs libdrm`
FLAGS+=-Wall -O0 -g
FLAGS+=-D_FILE_OFFSET_BITS=64

###
##Cross_compile=/home/garen/gcc-linaro-7.3.1-2018.05-x86_64_aarch64-linux-gnu/bin/aarch64-linux-gnu-
##GCC=$(Cross_compile)gcc
##
##
##LindrmInstallDir=/home/garen/SC300/elan_mini_control_tools/libdrm/libdrm-2.4.107/install_dir
##LibdrmInclude=$(LindrmInstallDir)/usr/include
##LibdrmInclude+=-I$(LindrmInstallDir)/usr/include/libdrm
##LibdrmSo=$(LindrmInstallDir)/usr/lib
###

### 基于 buildroot aarch64 linaro 交叉编译工具链，编译出来的 libdrm
Cross_compile=/home/garen/buildroot/buildroot/output/host/bin/aarch64-linux-gnu-
GCC=$(Cross_compile)gcc

LindrmInstallDir=/home/garen/buildroot/buildroot/output/build/libdrm-2.4.107/install_dir
LibdrmInclude=$(LindrmInstallDir)/usr/include
LibdrmInclude+=-I$(LindrmInstallDir)/usr/include/libdrm
LibdrmSo=$(LindrmInstallDir)/usr/lib


all:
	gcc -o modeset modeset.c $(FLAGS)
	gcc -o modeset-double-buffered modeset-double-buffered.c $(FLAGS)
	gcc -o modeset-vsync modeset-vsync.c $(FLAGS)

modeset:modeset.c
	$(warning "LibdrmInclude --> $(LibdrmInclude)")
	$(GCC) -o modeset modeset.c -I$(LibdrmInclude) -L$(LibdrmSo) -ldrm
clean:
	rm modeset