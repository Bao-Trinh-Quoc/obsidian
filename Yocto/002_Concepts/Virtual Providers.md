
## Reason

- Some recipes have the **same purpose**, and only one can be used at a time.
- The build system [[01-Bitbake]] uses Virtual Providers to reflect this. 
- ONLY ONE of the recipes that provides the functionality will be compiled and integrated into the resulting image.

## Example

	- virtual/<name>
	- virtual/bootloader: u-boot, u-boot-ti-staging, ...
	- virtual/kernel: linux-yocto, linux-yocto-tiny, ...
	- virtual/libc: glibc, musl, newlib,
	- virtual/xserver: xserver-xorg


## Provider Selection

	PREFERRED_PROVIDER: 

Examples:
- PREFERRED_PROVIDER_virtual/kernel ?= "linux-ti-staging"
- PREFERRED_PROVIDER_virtual/libgl = "mesa"

## Version Selection
- By default, Bitbake will try to build the recipe with the highest version number, from the highest priority layer.
- use ==PREFERRED_VERSION== to explicitly pick one.





























