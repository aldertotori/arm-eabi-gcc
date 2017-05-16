# 4.7.4 version specs

	 gmp-5.0.5
	 mpfr-2.4.2
   mpc-1.0.1
	 gcc-4.7.4
	 binutils-2.26.1
   newlib-2.1.0
	
## soft-float / hard-float ( -mfloat-abi=*** )
	### soft-float option -mfloat-abi=soft (default)
	### hard-float option -mfloat-abi=hard
	
## -msoft-float / -mhard-float
	### soft-float option -mfloat-abi=soft / -msoft-float (default)
	### hard-float option -mfloat-abi=hard / -mhard-float 
	
	
## cpu arch ( -mcpu=* / -march=* )
	### -march=armv7-a / -mcpu=cortex-a5 / -mcpu=cortex-a7 / -mcpu=cortex-a8 / -mcpu=cortex-a9 / -mcpu=cortex-a15 / -mcpu=marvell-pj4 / -mcpu=generic-armv7-a
	### -march=armv7-m / -mcpu=cortex-a3
	### -march=armv7e-m / -mcpu=cortex-a4
	### -march=armv6m / -mcpu=cortex-m0
	### -march=armv4 / -mcpu=arm8 / -mcpu=arm810 / -mcpu=strongarm* / -mcpu=fa526 / -mcpu=fa626:--fix-v4bx
	

## ARM EABI version 5
	
## gcc changes
### when compiling for ARMv6 (but not ARMv6-M), ARMv7-A, ARMv7-R, or ARMv7-M, the new option -munaligned-access  is active by default
which for some sources generates code that accesses memory on unaligned addresses. 
This requires the kernel of those systems to enable such accesses (controlled by CP15 register c1 , refer to ARM documentation). c1 , refer to ARM documentation). 
Alternatively, or for compatibility with kernels where unaligned accesses are not supported,
all code has to be compiled with  -mno-unaligned-access . 
Upstream Linux kernel releases have automatically and unconditionally supported unaligned accesses 
as emitted by GCC due to this option being active since version 2.6.28.
### Support on ARM for the legacy ?oating-point accelerator (FPA) and the mixed-endian floating-point format that it used has been obsoleted.
### The ARM port's  -mwords-little-endian  option has been deprecated. 
