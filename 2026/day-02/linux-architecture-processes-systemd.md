# Day 02 – Linux Architecture, Processes, and systemd

## My Understanding of Linux Architecture

Linux is an operating system that is widely used in servers, cloud platforms, and DevOps environments. Understanding Linux architecture is important for troubleshooting and managing servers.

The main components I learned today are:

* **Kernel:** The core of Linux that manages CPU, memory, processes, devices, networking, and other system resources.
* **User Space:** The area where users and applications interact with the operating system through commands, tools, and applications.
* **Shell:** Provides an interface for users to communicate with the Linux operating system.
* **systemd:** The system and service manager that starts and manages services during the Linux boot process.

## Linux Boot Process

I learned the basic Linux boot process:

```text
BIOS / UEFI
     ↓
Bootloader
     ↓
Linux Kernel
     ↓
systemd (PID 1)
     ↓
System Services
     ↓
User Login
```

The Linux kernel starts the `systemd` process, which normally runs as **PID 1** and manages system services.

## My Understanding of Processes

A process is a running instance of a program.

For example, when I start an application, Linux creates a process for that application. Every process has a unique **Process ID (PID)**.

I learned these commands to inspect processes:

```bash
ps
ps aux
top
pstree
```

I can check a specific process using:

```bash
ps aux | grep <process-name>
```

I also learned that processes can have parent-child relationships.

## My Understanding of systemd

`systemd` is responsible for managing system services and the startup process on modern Linux systems.

It can:

* Start services during system boot
* Stop and restart services
* Monitor service status
* Manage service dependencies
* Enable services to start automatically
* Help troubleshoot service-related issues

I learned that `systemd` normally runs with **PID 1**.

I can verify it using:

```bash
ps -p 1
```

## systemctl Commands I Practiced

I learned that `systemctl` is used to manage systemd services.

Check service status:

```bash
systemctl status ssh
```

Start a service:

```bash
sudo systemctl start ssh
```

Stop a service:

```bash
sudo systemctl stop ssh
```

Restart a service:

```bash
sudo systemctl restart ssh
```

Enable a service at boot:

```bash
sudo systemctl enable ssh
```

Disable a service at boot:

```bash
sudo systemctl disable ssh
```

Check whether a service is active:

```bash
systemctl is-active ssh
```

## Why This Is Important for DevOps

Linux is one of the most important technologies used in DevOps and cloud environments.

As a DevOps engineer, I need to understand processes and services to troubleshoot application and server issues.

For example, if an application is not working, I can check:

1. Whether the process is running.
2. The PID of the process.
3. Whether the required service is active.
4. Whether the service needs to be restarted.
5. Whether there are service or system errors.

This knowledge will help me troubleshoot Linux servers and applications more confidently.

## What I Learned Today

Today I learned:

* Linux architecture
* Kernel and user space
* Linux boot process
* Processes and PIDs
* Parent and child processes
* systemd and PID 1
* `systemctl` commands
* Basic Linux service troubleshooting

## My Day 02 Takeaway

Today I understood that Linux is not just about running commands. Understanding how the **kernel, processes, and system services** work is important for troubleshooting real-world servers.

This is an important foundation for my DevOps journey.

**Day 02: Understanding Linux processes and systemd as a foundation for DevOps troubleshooting.**
