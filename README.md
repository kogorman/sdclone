# sdclone
Backup/restore tool for entire drives, using `partclone(8)` for most copies and `zstd(1)` for compression.  The '`sd`' in the name '`sdclone`' is a reference to the fact that it is mostly intended for /dev/**SD**-something drives.

At the moment, `sdclone` hopes to copy drives partitioned in a manner understood by `sfdisk(8)`, and any filesystem recognized by `partclone` but will do binary copies of other filesystems or of partitions without a filesystem.  As an exception, swap partitions are not copied, but are newly formatted when restored.  You should avoid large binary partitions of other kinds -- especially RAID members -- if clone speed, size or compression is important, because `sdclone` does not understand their format.  It should copy them in binary mode, so it will work, but not compress as well as -- for instance -- applying `partclone` to the full RAID filesystem.

Written in Python3 for Ubuntu Linux, this should be fairly easy to modify for other environments, so long as the basics are available:
  - Python3
  - partclone
  - zstd
  - dd
  - Bash-like shell
  - lsblk
  - sfdisk
