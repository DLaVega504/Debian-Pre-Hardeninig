# Universal Interactive Turn-Key Linux Pre-Hardening Framework (Stage 1)

A foundational system orchestration framework designed to deploy an advanced, fully encrypted base storage architecture prior to applying active host-hardening policies. This framework guarantees raw partition security, builds optimized volume management layers, and prepares the operational substrate across **Arch Linux**, **Debian**, **Fedora**, and **openSUSE** deployment targets.

## 🚀 Purpose & Architecture

This framework establishes physical and foundational data security from a clean slate or fresh install scenario. It focuses strictly on storage layout containment, cryptographic volume constraints, and system bootstrap preparation.

### Core Foundation Layers
* **Layer 1: Partition & Hard Drive Layout** — Structures raw hardware devices, establishing primary, boot, and extended operational boundaries cleanly.
* **Layer 2: Cryptographic Containerization (LUKS)** — Provisions robust, full-disk encryption algorithms (utilizing `argon2id` iterations) to safeguard raw data layers from physical extraction attempts.
* **Layer 3: Logical Volume Management (LVM)** — Abstracts the underlying encrypted space into isolated, dynamically resizable volume pools to optimize resource tracking.
* **Layer 4: Advanced Subvolume Hierarchy** — Establishes secure storage containment parameters, including granular tracking paths like `@secure=/vault` for absolute host containment.
* **Layer 5: Hybrid Memory Allocation** — Calculates and mounts standardized system swap layers aligned with custom biometric guidelines (RAM < 8GB maps to RAM × 2; RAM ≥ 8GB maps to RAM × 1.5).

---

## 📋 System Blueprint & Storage Layout

Stage 1 maps out strict partition boundaries on physical hardware arrays (e.g., your primary hard drive `/dev/sda`) to balance boot validation compatibility with data isolation rules:

### Standard Hardware Allocation
1. **`/dev/sda1` (Secure Boot Bootloader)** — A 1GB standalone, password-protected `/boot` layout paired with custom bootloader markers (`grub-mkpasswd`) for structural authentication.
2. **`/dev/sda2` (Encrypted Core Partition)** — The primary workspace containing an encapsulated LUKS container which unifies your system volumes, subvolumes, and swap assets under a single master boot passphrase challenge.
3. **`/dev/sda3` (Sensitive Data Vault)** — An optional, completely detached 30GB storage vault or secondary partition block dedicated entirely to containing independent cryptographic keys and high-security file trees.

---

## 🛠️ Usage & Verification Protocols

### 1. Pre-Flight Storage Check (Simulation Mode)
Before writing block modifications or initializing filesystems on raw hardware devices, validate playbook structural paths, drive identification strings, and variable logic arrays using standard execution arguments:
```bash
ansible-playbook bootstrap-debian-storage.yml --check
```
* *Caution: Dry-running tasks that manage raw disks or disk partitioning configurations will skip underlying filesystem writes, allowing safe structure parsing checks before commit loops.*

### 2. Live Bootstrapping Initialization
To permanently commit partition sectors, execute cryptographic containerization scripts, and mount target filesystem hierarchies on deployment hosts:
```bash
ansible-playbook bootstrap-debian-storage.yml --ask-become-pass
```

---

## 🔄 Next Steps in the Lifecycle

Once Stage 1 successfully completes and verifies your baseline storage encryption architecture, the system is prepared to pass control cleanly onto the next phase of deployment:

* **Stage 1 (This Step):** Physical boundary layout, LUKS container construction, and volume mapping.
* **Stage 2 (Next Step):** Automated execution of your **Universal Zero-Trust Linux Hardening Framework** to apply kernel optimization baselines, host daemon shielding, and defensive system configurations.

