# 🐧 Linux for DevOps - Complete Learning Notes

---

## 📌 1. What is Operating System?

An Operating System (OS) is software that acts as a bridge between user and hardware.

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

Shell is a command-line interface that allows users to interact with the OS by sending commands to the kernel.

👉 Example:

```bash
ls
cd
pwd
```

---

## 🧠 4. Linux Architecture

Flow:

User → Shell → Kernel → Hardware

* Shell takes input from user
* Kernel executes using hardware

---

# 🧠 5. System Resources (Interview + Real Understanding)

---

## 🔹 CPU (Processor)

👉 Definition (Interview):
CPU is responsible for executing instructions and running programs.

👉 Kid version:
CPU is like the **brain** that does all thinking and work.

👉 Check:

```bash
top
```

👉 Healthy:

* Idle (id) > 60%

👉 Problem:

* CPU usage high → system slow

---

## 🔹 Memory (RAM)

👉 Definition (Interview):
Memory stores temporary data of running applications.

👉 Kid version:
RAM is like a **table** where you keep things while working.

👉 Check:

```bash
free -m
```

👉 Problem:

* If full → system may kill apps (OOM Killer)

---

## 🔹 Disk (Storage)

👉 Definition (Interview):
Disk stores permanent data like files, logs, and applications.

👉 Kid version:
Disk is like a **cupboard** where you store everything.

👉 Check:

```bash
df -h
```

👉 Problem:

* If full → apps crash, logs stop writing

---

## 🔹 Network

👉 Definition (Interview):
Network allows communication between applications and systems using ports.

👉 Kid version:
Network is like a **road** connecting houses (apps).

👉 Check:

```bash
ss -tulnp
```

👉 Problem:

* If port not open → app not reachable

---

## 🔹 Process

👉 Definition (Interview):
A process is a running instance of a program.

👉 Kid version:
Process is a **working person doing a task**.

👉 Check:

```bash
ps aux
```

👉 Problem:

* If process not running → app is down

---

## 🧠 6. Important Concepts

### 🔹 OOM Killer

* Triggered when memory is full
* Kernel kills processes automatically

```bash
dmesg | grep -i kill
```

---

### 🔹 Disk Naming

* /dev/sda, /dev/sdd → disks
* /dev/sda1 → partition

---

### 🔹 Ports

* Apps run on ports

Examples:

* 6379 → Redis
* 5432 → PostgreSQL

---

## 🔄 7. Process Lifecycle

1. Program exists
2. Executed
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

## 📘 9. Debugging Mindset (MOST IMPORTANT)

1. Check process → ps aux
2. Check logs → /var/log
3. Check CPU → top
4. Check memory → free -m
5. Check disk → df -h
6. Check network → ss -tulnp

---

## 🔥 10. Real Scenarios

### ❌ App not running

```bash
ps aux | grep app
```

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

Always ask:

* Is process running?
* Is CPU overloaded?
* Is memory full?
* Is disk full?
* Is port open?

---

## 🚀 Key Takeaway

Linux is not about commands — it is about understanding system behavior and debugging efficiently.
