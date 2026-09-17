---
tags:
  - yocto/concept
  - bootlin
type: concept
---
# [[03-Recipes]]

## Summary
- Describes how to handle software component (application, library)
- A set of instructions to describe how to retrrieve, patch, compile, install and generate binary packages.

## Key Details
- are parsed by [[01-Bitbake]]
- format: recipename_version.bb
- The output of recipe is **a set of binary packages** (rpm, deb or ipk): typically recipename, recipename-doc, recipename-dbg.
- contains functions that can be run called [[05-Tasks]] (fetch, configure, compile...)

- has three main parts:
	- The header: What/Who
	- The sources: Where
	- The tasks: how

## Organization of A Recipe
Because many applications have more than one recipe so to support differrent versions, the common metadata is included in each version and is in **.inc** file:

</application/>.inc  -> Version agnostics metadata

</application/> _ < version > . bb 
	require < application > . inc
	 any version specific metadata

## References