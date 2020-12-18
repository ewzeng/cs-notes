Old computers: no directories, flat

Directory a special type of file; contains mappings

File: group of blocks on a disk.

FAT: Index into FAT with file number (file number is the index in FAT and the starting block number of the file - note not all indices are valid as they can be in the middle of the file). Follow linked list in FAT. Simple, but not efficient, nor secure.

Note: most files are small; most bytes in large files.

UFS (Berkeley! Very similar to ext2/3.) File number is index into a inode array. Indirect pointers, doubly indirect pointers, etc. Size of inode array is limit of number of files in disk.

- Want: sequential blocks for a file. Use free bitmap to find a range of free blocks. Also skip sectors to counter rotational delay.

Soft link: maps one path to together. AKA shortcuts.

In some BSDs, don't have to transverse directories linearly. Use B-Trees.

NTFS: variable length extents. B-tree directory. Master file table. Similar to ext4.

Can we memory map a file into RAM? Yes. Executable files are handled this way. Syscall: mmap.

Buffer cache! UNIX flushes every 30 seconds.