# 1. version specs ( armv8-a support added )
    gmp-4.3.2 / mpfr-2.4.2 / mpc-0.8.1 / isl-0.12.2
    gcc-5.4.0 / binutils-2.28 / newlib-2.5.0 / libnosys

# 2. soft-float/hard-float
	2.1 mfloat-abi=hard  (hard-float)
	2.2 mfloat-abi=soft	 (soft-float)
	
# 3. cpu arch ( default: -march=armv7-a )
	3.1 -march=armv7-a ( -mcpu=cortex-a5 / -mcpu=cortex-a7 / -mcpu=cortex-a8 / -mcpu=cortex-a9 / -mcpu=cortex-a15 / -mcpu=marvell-pj4 / -mcpu=generic-armv7-a)
	3.2 -march=armv7-m ( -mcpu=cortex-a3 )
	3.3 -march=armv7e-m ( -mcpu=cortex-a4 )
	3.4 -march=armv6m ( -mcpu=cortex-m0 )
	3.5 -march=armv8-a 
	3.6 -march=armv5 
	3.7 -march=armv4 ( -mcpu=arm8 / -mcpu=arm810 / -mcpu=strongarm* / -mcpu=fa526 / -mcpu=fa626:--fix-v4bx )
	
# 4. ARM EABI version 5 (default)

# 5. gcc changes
5.1 when compiling for ARMv6 (but not ARMv6-M), ARMv7-A, ARMv7-R, or ARMv7-M, the new option -munaligned-access  is active by default
which for some sources generates code that accesses memory on unaligned addresses. 
This requires the kernel of those systems to enable such accesses (controlled by CP15 register c1 , refer to ARM documentation). c1 , refer to ARM documentation). 
Alternatively, or for compatibility with kernels where unaligned accesses are not supported,
all code has to be compiled with  -mno-unaligned-access . 
Upstream Linux kernel releases have automatically and unconditionally supported unaligned accesses 
as emitted by GCC due to this option being active since version 2.6.28.
5.2 Support on ARM for the legacy floating-point accelerator (FPA) and the mixed-endian floating-point format that it used has been obsoleted.
5.3 The ARM port's  -mwords-little-endian  option has been deprecated. 

# 6. newlib ports
6.1 nosys.a default not link with gcc,please use option "-lnosys" manual
		eg:
      arm-eabi-gcc test.c -lnosys
