---
tags: [yocto/concept, bootlin]
type: concept
---
# [[05-Tasks]]

## Summary
> A brief, 1-2 sentence definition in your own words.

**The build process** implemented by a [[03-Recipes]] is split in a several tasks.

## Key Details
* Each task performs a **specific** step in the build
* *fetch, configure, compile, package*
* Tasks can depend on other tasks (including on tasks of other recipes) 

## References
* Bootlin Slide Page: #