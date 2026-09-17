
[[01-Bitbake]] [[02-Variables]]

==VARIABLE:override = "some value"


# Overrides to modify variable values
- The *append* override adds **at the end** of the variable (without space)
	- IMAGE_INSTALL:append = " dropbear" adds dropbear to the packages installed on the image
- The *prepend* override adds **at the beginning** of the variable (without space)
	- PATH:prepend = "${COREBASE}/scripts/native-intercept:" adds a path before the ones already present.
- The *remove* removes **ALL occurrences** of a value within a variable.
	- IMAGE_INSTALL:remove = "i2c-tools"

# Overrides for conditional assignment

```
OVERRIDES="arm:armv7a:ti-soc:ti33x:beaglebone:poky" 

KERNEL_DEVICETREE:beaglebone = "am335x-bone.dtb" # This is applied 
KERNEL_DEVICETREE:dra7xx-evm = "dra7-evm.dtb" # This is ignored
```

- The **most specific assignment** takes precedence
```
IMAGE_INSTALL:beaglebone = "busybox mtd-utils i2c-tools" 
IMAGE_INSTALL = "busybox mtd-utils"

if MACHINE is beaglebone then IMAGE_INSTALL = "busybox mtd-utils i2c-tools"
else IMAGE_INSTALL = "busybox mtd-utils"
```

- The previous methods can be combined
```
IMAGE_INSTALL = "busybox mtd-utils" 
IMAGE_INSTALL:append = " dropbear" 
IMAGE_INSTALL:append:beaglebone = " i2c-tools"


IMAGE_INSTALL = "busybox mtd-utils dropbear i2c-tools" if the machine being built is beaglebone. 
IMAGE_INSTALL = "busybox mtd-utils dropbear" otherwise.

```
- Order of variable assignment
![[Pasted image 20260708235648.png]]