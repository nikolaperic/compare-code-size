# Code size comparison script

This script collects code size information for two specified project builds.
For that purpose, ```GNU size``` tool is used.
Only executable files are considered for size measurement.
Executable files from two builds are matched by name.

Differences in code size are measured by subtracting the size of executable file from the second given build from the size of that file from the first given build.

In other words: ```diff = size(exe_from_the_first_build) - size(exe_from_the_second_build)```

If the difference is greater than zero there are savings in code size. If the difference is less that zero there are regressions in code size.

After computing the difference in code size, two graphs are generated to showcase executable files with the most significant savings or regressions in code size.

### Required Python modules:

- `pandas`
- `numpy`
- `matplotlib`

Install the dependencies by running:
```bash
pip install -r requirements.txt
```

### Required installed tools:

- `size` - list section sizes and total size of binary files (https://www.gnu.org/software/binutils/)
- `file` - determine file type (https://darwinsys.com/file/)

### Usage:

```bash
$ python3 compare_code_size.py <path_to_the_first_build> <path_to_the_second_build> size
```

**Note**: Typically, the first build is the clean one, while the second build includes extra optimizations, requiring an assessment of their effect on code size.
