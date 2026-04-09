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

## 🧠 9. Debugging Mindset (VERY IMPORTANT)

### Step 1: Check process

```bash
ps aux | grep app
```

### Step 2: Check logs

```bash
cd /var/log
tail -f app.log
```

### Step 3: Check CPU

```bash
top
```

### Step 4: Check memory

```bash
free -m
```

### Step 5: Check disk

```bash
df -h
```

### Step 6: Check network

```bash
ss -tulnp
```

---

## 🔥 10. Real Scenarios

### ❌ App not running

* Process missing

Fix:

```bash
systemctl start app
```

---

### ❌ High CPU

```bash
top
ps aux --sort=-%cpu | head
```

---

### ❌ Memory full

```bash
free -m
ps aux --sort=-%mem | head
```

---

### ❌ Disk full

```bash
df -h
du -sh /* | sort -h
```

---

### ❌ Port already in use

```bash
ss -tulnp | grep <port>
kill -9 <PID>
```

---

### ❌ Command not found

```bash
echo $PATH
which <command>
```

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

