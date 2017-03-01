1. Android build
  - Download original android source code ( android-7.0.0_r7  ) from http://source.android.com
  - Untar opensource packages of F800_Nougat_Android_3.tar.gz into downloaded android source directory
       a) tar -xvzf  F800_Nougat_Android_3.tar.gz
  - And, merge the source into the android source code
  - Run following scripts to build android
    a) source build/envsetup.sh
    b) lunch aosp_bullhead-userdebug
    c) make -j4
  - When you compile the android source code, you have to add google original prebuilt source(toolchain) into the android directory.
  - After build, you can find output at out/target/product/generic

2. Kernel Build  
  - Uncompress using following command at the android directory
        a) F800_Nougat_Kernel.tar.gz

  - When you compile the kernel source code, you have to add google original prebuilt source(toolchain) into the android directory.
  - Run following scripts to build kernel
    a) cd kernel/msm-3.18
    b) 
    	case F800L) make ARCH=arm64 elsa_lgu_kr-perf_defconfig
    	case F800S) make ARCH=arm64 elsa_skt_kr-perf_defconfig
    	case F800K) make ARCH=arm64 elsa_kt_kr-perf_defconfig
    	
    c) make ARCH=arm64 CROSS_COMPILE=../../prebuilts/gcc/linux-x86/aarch64/aarch64-linux-android-4.9/bin/aarch64-linux-android- KERNEL_COMPRESSION_SUFFIX=gz -j4
	
	* "-j4" : The number, 4, is the number of multiple jobs to be invoked simultaneously. 
  - After build, you can find the build image(Image.gz) at arch/arm64/boot
