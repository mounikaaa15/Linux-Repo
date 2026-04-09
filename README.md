# 🐧 Linux for DevOps - Complete Learning Notes

## 📌 1. What is Operating System?

An Operating System (OS) acts as a bridge between user and hardware.

👉 It includes:

* Kernel (core)
* Shell (interface)
* Utilities

---

## 🧠 2. Kernel vs OS

| Kernel           | Operating System              |
| ---------------- | ----------------------------- |
| Core component   | Complete system               |
| Manages hardware | Interface for user + hardware |

👉 Example:
Linux = OS
Linux Kernel = core engine

---

## 🧠 3. What is Shell?

Shell is a command-line interface that allows users to interact with the OS.

👉 Example commands:

```bash
ls
cd
pwd
```

---

## 🧠 4. Linux Architecture

Flow:

User → Shell → Kernel → Hardware

* Shell sends commands
* Kernel executes using hardware

---

## 🧠 5. System Resources

### 🔹 CPU (Processor)

* Executes programs

Check:

```bash
top
```

Healthy:

* Idle > 60%

---

### 🔹 Memory (RAM)

* Stores running applications

Check:

```bash
free -m
```

---

### 🔹 Disk (Storage)

* Stores files and logs

Check:

```bash
df -h
```

---

### 🔹 Network

* Enables communication between services

Check:

```bash
ss -tulnp
```

---

### 🔹 Process

* Running program

Check:

```bash
ps aux

```

---

## 🧠 6. Important Concepts

### OOM Killer

* Triggered when memory is full
* Kernel kills processes automatically

Check:

```bash
dmesg | grep -i kill
```

---

### Disk Naming

* /dev/sda, /dev/sdd → disks
* /dev/sda1 → partition

---

### Ports

* Apps run on ports
* Example:

  * 6379 → Redis
  * 5432 → PostgreSQL

---

## 🔄 7. Process Lifecycle

1. Program exists
2. Executed by user
3. Loaded into memory
4. Assigned PID
5. Runs
6. Terminates

---

## ⚙️ 8. Process Commands

### View processes

```bash
ps aux
```

### Find process

```bash
ps aux | grep app
```

### Kill process

```bash
kill <PID>
```

### Force kill

```bash
kill -9 <PID>
```

---

# 🐧 Linux for DevOps - Complete Learning Notes (Deep Understanding)

## 📘 Command Deep Dive (Expected vs Unexpected)

---

### 🔹 top (CPU & Process Monitor)

What it does:

* Shows real-time CPU, memory, and running processes

Expected Output:

* CPU idle (id) > 60%
* Few processes using CPU

Unexpected:

* CPU idle < 10%
* One process using high CPU (e.g. 90%)

Fix:

```bash
ps aux --sort=-%cpu | head
kill -9 <PID>
```

---

### 🔹 free -m (Memory Check)

What it does:

* Shows RAM usage

Expected:

* Free memory available

Unexpected:

* Very low free memory

Fix:

```bash
ps aux --sort=-%mem | head
kill -9 <PID>
```

* Restart app or increase RAM

---

### 🔹 df -h (Disk Usage)

What it does:

* Shows disk usage

Expected:

* Usage < 80%

Unexpected:

* 90–100% full

Fix:

```bash
du -sh /* | sort -h
rm -rf large_file
```

---

### 🔹 ps aux (Process List)

What it does:

* Lists all running processes

Expected:

* App process visible

Unexpected:

* App missing → not running

Fix:

```bash
systemctl start app
```

---

### 🔹 ps aux | grep app

What it does:

* Searches for specific process

Expected:

* Shows process with PID

Unexpected:

* No output

Fix:

* Start application

---

### 🔹 ss -tulnp (Network Ports)

What it does:

* Shows open ports and services

Expected:

* Required port visible (e.g. 8080)

Unexpected:

* Port missing → app not listening

Fix:

```bash
systemctl restart app
```

---

### 🔹 cd /var/log & tail -f app.log

What it does:

* Reads logs in real-time

Expected:

* Normal logs

Unexpected:

* Errors like "connection failed", "port in use"

Fix:

* Debug based on error message

---

### 🔹 kill / kill -9

What it does:

* Stops process

Expected:

* Process stops

Unexpected:

* Process not stopping → use force

Fix:

```bash
kill -9 <PID>
```

---

### 🔹 echo $PATH

What it does:

* Shows command search paths

Expected:

* Paths like /usr/bin

Unexpected:

* Missing path → command not found

Fix:

```bash
export PATH=$PATH:/new/path
```

---

### 🔹 which <command>

What it does:

* Finds command location

Expected:

* Shows path

Unexpected:

* No output → command missing

Fix:

* Install or update PATH

---

## 🎯 Final DevOps Thinking

Always think:

* Is process running?
* Is CPU overloaded?
* Is memory full?
* Is disk full?
* Is port open?

---

## 🚀 Key Takeaway

Linux is not about commands — it is about understanding system behavior and debugging issues efficiently.
