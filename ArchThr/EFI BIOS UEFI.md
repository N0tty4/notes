every device needs non-volatile code to execute when powered up (ROM or FLASH). Today's devices read two, or even three bootloader from external storage. 
In case for PC bootloader we cave BIOS (past) or UEFI (new).
- BIOS
  is very simple, just reads first sector from active disk which works as second bootloader an loads OS.
- UEFI
  more advanced an supports signed bootloaders prevent virus.
# partitions
## MBR (Master Boot Record)
Disk, storage for store data needs to be formatted (ext4, FAT32) and partitioned. First partition system was MBR (Master Boot Record) was created to HDD's for its time.
- supports up to 4 partitions per disk, (disks store data in blocks called sectors), each 512 bytes in size (SSDs have 4KB), and each sector is uniquely numbered, called (Logical Block Addressing).
	- `LBA` starts with 22 bits (max 4 million sectors), followed by 28 and finally 48 bits (length of addresses).
- max dimensions disk was `2^(32bit LBA) / 512 = 2.2 TB`
## GPT (GUID Partition Table)
- invented for replace MBR, using `64 bits` and `128` available partitions.
- stores `CRC (Cyclick Redundancy Check)`.
# File system
file systems care about files, is what you see when open explorer.
- files are stored in cluster. Each cluster could have one or more sectors
- file system has a `directory` called (File Allocation Table) where info about cluster is used by files to kept.
- Minimal file size is a clusterk