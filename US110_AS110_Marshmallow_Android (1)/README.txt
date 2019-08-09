1. Android build
  - Download original android source code ( android-6.0.1_r1 ) from http://source.android.com
  - Untar opensource packages of US110_AS110_Marshmallow_Android.tar.gz into downloaded android source directory
       a) tar -xvzf US110_AS110_Marshmallow_Android.tar.gz
  - And, merge the source into the android source code
  - Run following scripts to build android
    a) source build/envsetup.sh
    b) lunch aosp_bullhead-userdebug
    c) make -j4
  - When you compile the android source code, you have to add google original prebuilt source(toolchain) into the android directory.
  - After build, you can find output at out/target/product/generic

2. Kernel Build  
  - Uncompress using following command at the android directory
        a) tar -xvzf US110_AS110_Marshmallow_Kernel.tar.gz

  - When you compile the kernel source code, you have to add google original prebuilt source(toolchain) into the android directory.
  - Run following scripts to build kernel
    a) cd kernel
    b) export ARCH=arm
	c) export TARGET_PRODUCT=lv0_usc_us
	d) export CROSS_COMPILE=../../android/prebuilts/gcc/linux-x86/arm/arm-eabi-4.8/bin/arm-eabi-
	e) make lv0_usc_us_defconfig
	f) make zImage -j4
    	
    * "-j4" : The number, 4, is the number of multiple jobs to be invoked simultaneously. 
  - After build, you can find the build image(zImage) at arch/arm/boot
