### gflags 2.2.0+

https://github.com/gflags/gflags

+++

The `gflags` package contains a C++ library that implements command line flags processing.

+++

```bash
$ irohad --helpshort
USING ENVIRONMENT VARIABLES:
	$ export FLAGS_flag1=val
	$ export FLAGS_flag2=val
	$ ./irohad -fromenv=flag1,flag2

USING CLI:
	$ ./irohad -flag1=val -flag2=val

USING FLAG FILE:
	$ cat /tmp/flags
	-flag1=val
	-flag2=val
	$ ./irohad -flagfile=/tmp/flags
```
