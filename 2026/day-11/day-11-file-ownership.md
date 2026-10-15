Today, I practiced Linux file ownership and learned how to manage file owners and groups using `chown` and `chgrp`.

## My Understanding of File Ownership

Linux file ownership defines which user owns a file and which group is associated with it. Ownership management helps control access to files and directories.

- `chown` – Changes the file owner.
- `chgrp` – Changes the file group.
- `chown owner:group` – Changes both owner and group.
- `chown -R` – Changes ownership recursively for a directory and its contents.
- `ls -l` – Displays file permissions, owner, and group.

## Practical Commands I Practiced

### 1. Create Users and Groups

```bash
sudo useradd -m user1
sudo useradd -m user2

sudo groupadd group1
sudo groupadd group2
```

### 2. Create Files and Directories

```bash
mkdir -p ~/day-11-practice
cd ~/day-11-practice

touch file1.txt
touch file2.txt
mkdir dir1
touch dir1/file3.txt
```

### 3. Check File Ownership

```bash
ls -l
ls -ld dir1
```

### 4. Change File Owner

```bash
sudo chown user1 file1.txt
ls -l file1.txt
```

### 5. Change File Group

```bash
sudo chgrp group1 file2.txt
ls -l file2.txt
```

### 6. Change Owner and Group Together

```bash
sudo chown user2:group2 file1.txt
ls -l file1.txt
```

### 7. Change Ownership Recursively

```bash
sudo chown -R user1:group1 dir1
ls -lR dir1
```

## What I Learned

1. Understood the difference between file owner and group.
2. Learned to change ownership using `chown`.
3. Practiced changing groups using `chgrp`.
4. Learned to change owner and group in a single command.
5. Practiced recursive ownership changes using `chown -R`.
6. Verified ownership changes using Linux commands.

## Why File Ownership Matters in DevOps

- Managing application deployment files.
- Controlling access to shared directories.
- Managing log files and configuration files.
- Handling permissions for CI/CD pipeline artifacts.

## Screenshots

I will include screenshots showing user and group creation, file creation, ownership changes, and recursive ownership verification.

## My Learning Commitment

I am continuing my 90 Days of DevOps Challenge by practicing Linux commands, documenting my learning, uploading my work to GitHub, and sharing my progress.

**Day 11: Learning Linux File Ownership with `chown` and `chgrp`.**
