# Day 13 – Linux Volume Management (LVM)

## Objective

The objective of this practical is to understand Linux Logical Volume Management (LVM) and learn how to create, format, mount, and extend logical volumes.

## 1. Check Current Storage

### Commands Used

```bash
lsblk
sudo pvs
sudo vgs
sudo lvs
df -h
```

### Key Learnings

- `lsblk` displays block devices and partitions.
- `pvs` displays Physical Volumes.
- `vgs` displays Volume Groups.
- `lvs` displays Logical Volumes.
- `df -h` displays filesystem disk usage.

## 2. Create a Physical Volume

```bash
sudo pvcreate /dev/sdb
sudo pvs
```

A Physical Volume (PV) is a disk or partition initialized for LVM.

## 3. Create a Volume Group

```bash
sudo vgcreate devops-vg /dev/sdb
sudo vgs
```

A Volume Group (VG) combines Physical Volumes to provide storage for Logical Volumes.

## 4. Create a Logical Volume

```bash
sudo lvcreate -L 500M -n app-data devops-vg
sudo lvs
```

- `-L 500M` specifies the logical volume size.
- `-n app-data` specifies the logical volume name.
- `devops-vg` is the Volume Group name.

## 5. Format and Mount the Logical Volume

```bash
sudo mkfs.ext4 /dev/devops-vg/app-data
sudo mkdir -p /mnt/app-data
sudo mount /dev/devops-vg/app-data /mnt/app-data
df -h /mnt/app-data
```

- `mkfs.ext4` creates an ext4 filesystem.
- `mkdir -p` creates the mount-point directory.
- `mount` mounts the filesystem.
- `df -h` verifies filesystem usage.

## 6. Extend the Logical Volume

```bash
sudo lvextend -L +200M /dev/devops-vg/app-data
sudo resize2fs /dev/devops-vg/app-data
df -h /mnt/app-data
```

- `lvextend` increases the logical volume size by 200 MB.
- `resize2fs` expands the ext4 filesystem.
- `df -h` verifies the updated filesystem size.

The Volume Group must have sufficient free space before extending the volume.

## 7. What I Learned

1. Understood the relationship between Physical Volumes, Volume Groups, and Logical Volumes.
2. Learned how to create, format, and mount a logical volume.
3. Practiced extending a logical volume and resizing an ext4 filesystem.

## Conclusion

Day 13 helped me understand Linux Logical Volume Management (LVM) and flexible storage administration. I learned how LVM organizes storage and how logical volumes can be extended when sufficient free space is available.

**Challenge:** 90 Days of DevOps  
**Day:** 13 – Linux Volume Management (LVM)

#90DaysOfDevOps #DevOpsKaJosh #TrainWithShubham
