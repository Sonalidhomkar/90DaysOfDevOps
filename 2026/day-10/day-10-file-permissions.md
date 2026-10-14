# Day 10 – File Permissions & File Operations

## Objective
To practice Linux file operations, understand file permissions, and modify permissions using the `chmod` command.

## 1. Create Files and Directory

```bash
mkdir -p ~/day-10-practice
cd ~/day-10-practice

touch devops.txt
echo "I am learning Linux file permissions." > notes.txt
printf 'echo "Hello DevOps"\n' > script.sh
```

## 2. Read Files

```bash
cat notes.txt
cat script.sh
head -n 5 /etc/passwd
tail -n 5 /etc/passwd
vim -R script.sh
```

## 3. Check File Permissions

```bash
pwd
ls -l
ls -l devops.txt notes.txt script.sh
```

Linux permission symbols:

- `r` – Read
- `w` – Write
- `x` – Execute

## 4. Modify File Permissions

Make the script executable:

```bash
chmod +x script.sh
./script.sh
ls -l script.sh
```

Expected output:

```text
Hello DevOps
```

Remove write permission from `devops.txt`:

```bash
chmod a-w devops.txt
ls -l devops.txt
```

Set `notes.txt` permission to `640`:

```bash
chmod 640 notes.txt
ls -l notes.txt
```

Create a directory with permission `755`:

```bash
mkdir -p project
chmod 755 project
ls -ld project
```

## 5. Test File Permissions

Test writing to the read-only file:

```bash
echo "Testing write access" >> devops.txt
```

Test executing a script without execute permission:

```bash
chmod a-x script.sh
./script.sh
```

Restore execute permission:

```bash
chmod u+x script.sh
./script.sh
```

Note: Permission-denied errors depend on file ownership and user privileges. Record the actual output from your server.

## 6. What I Learned

1. Learned to create and read files using Linux commands.
2. Understood file permissions: read, write, and execute.
3. Practiced modifying permissions using `chmod`.
4. Learned numeric permissions `640` and `755`.
5. Tested file access restrictions on a Linux server.

## 7. Screenshots

Add actual screenshots showing:

1. File creation and initial permissions.
2. Successful shell script execution.
3. Permission changes using `chmod`.
4. Permission testing and error messages.

## Conclusion

I practiced Linux file operations and file permission management as part of my 90 Days of DevOps Challenge.

#90DaysOfDevOps #DevOpsKaJosh #TrainWithShubham
