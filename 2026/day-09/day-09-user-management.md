# Day 09 – Linux User and Group Management

## 1. Create Users
```bash
sudo useradd -m user1
sudo useradd -m user2
sudo useradd -m user3
sudo useradd -m user4
```

Check users:
```bash
id user1
id user2
id user3
id user4
```

## 2. Create Groups
```bash
sudo groupadd developers
sudo groupadd admins
sudo groupadd project-team
```

Check groups:
```bash
getent group developers
getent group admins
getent group project-team
```

## 3. Add Users to Groups
```bash
sudo usermod -aG developers user1
sudo usermod -aG developers,admins user2
sudo usermod -aG admins user3
sudo usermod -aG project-team user4
sudo usermod -aG project-team user1
```

Check membership:
```bash
groups user1
groups user2
groups user3
groups user4
```

## 4. Create Shared Directory
```bash
sudo mkdir -p /opt/dev-project
sudo chgrp developers /opt/dev-project
sudo chmod 775 /opt/dev-project
ls -ld /opt/dev-project
```

## 5. Test File Creation
```bash
sudo -u user1 touch /opt/dev-project/file1.txt
sudo -u user2 touch /opt/dev-project/file2.txt
ls -l /opt/dev-project
```

## 6. Create Team Workspace
```bash
sudo mkdir -p /opt/team-workspace
sudo chgrp project-team /opt/team-workspace
sudo chmod 775 /opt/team-workspace
ls -ld /opt/team-workspace
```

Test file creation:
```bash
sudo -u user4 touch /opt/team-workspace/file3.txt
ls -l /opt/team-workspace
```

## What I Learned
- Creating Linux users and groups.
- Assigning users to groups.
- Managing shared directories.
- Setting permissions using chmod.
- Checking users, groups, and files.
