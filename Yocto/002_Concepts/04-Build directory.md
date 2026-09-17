# Glossary

**BUILDDIR**: Absolute path of the build directory.
**BB_NUMBER_THREAD**
**PARALLEL_MAKE**
**MACHINE**

# The build/conf/ directory:
- **bblayers.conf**: Explicitly list the layers to use.
- **local.conf**: Set up the configuration variables relative to the current user for the build. Configuration variables can be overridden there.
- **site.conf**: Similar to **local.conf** but intended to be used for site-specific settings, such as network mirrors and CPU/memory resource usage limits

# The build/conf directory after build

- **conf/** Configuration files, as before, not touched by the build. 
- **downloads**/ Downloaded upstream tarballs of the recipes used in the builds. 
- **sstate-cache/** Shared state cache. Used by all builds. 
- **tmp/** Holds all the build system outputs.
- **tmp/work/** Set of specific work directories, split by architecture. They are used to unpack, configure and build the packages. Contains the patched sources, generated objects and logs. 
- **tmp/sysroots/** Shared libraries and headers used to compile applications for the target but also for the host. 
- **tmp/deploy/** Final output of the build. 
- **tmp/deploy/images/** Contains the complete images built by the OpenEmbedded build system. These images are used to flash the target. 
- **tmp/buildstats/** Build statistics for all packages built (CPU usage, elapsed time, host, timestamps…)