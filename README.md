
# Force Format USB Drive in Windows Using DiskPart

 ⚠️ **Warning:** This will erase **all data** on the selected USB drive. Be very careful to select the correct disk!

**Note:** Try formatting your USB through the file explorer first, in case it fails, this method has helped me force the formatting multiple times.

 ## Steps

1. Open a **Command Prompt** as Administrator.
2. Launch **DiskPart**
```cmd
diskpart
```
3. List all disks to identify your USB
```cmd
list disk
```
4. Select your USB disk (replace X with the disk number)
```cmd
select disk X
```
5. Remove read-only attributes
```cmd
attributes disk clear readonly
```
6. Clean the disk (wipes all the disk's partitions)
```cmd
clean
```
7. Create a new primary partition
```cmd
create partition primary
```
8. List volumes to identify the new partition
```cmd
list volume
```
9. Select the new volume (replace Y with the volume number of your USB)
```cmd
select volume Y
```
10. Format the volume as NTFS (quick format)
```cmd
format fs=ntfs quick
```
11. Assign a drive letter (optional but recommended)
```cmd
assign
```
12. You can now close DiskPart and the Command Prompt, your USB should now be writable.
