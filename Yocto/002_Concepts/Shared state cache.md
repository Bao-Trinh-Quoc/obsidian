
- [[01-Bitbake]] stores the output of each task in a directory, the ==shared state cache==
- This cache is used to speed up the compilation.
-  Its location is defined by ==SSTATE_DIR== variable and defaults to build/sstate-cache
- Can be cleaned:

```
$ find sstate-cache/ -type f -atime +30 -delete
```

This removes all files that have last been accessed more than 30 days ago (for example)