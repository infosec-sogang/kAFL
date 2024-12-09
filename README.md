<h1 align="center">
  <br>kAFL</br>
</h1>

<h3 align="center">
HW-assisted Feedback Fuzzer for x86 VMs
</h3>

<p align="center">
  <a href="https://github.com/IntelLabs/kAFL/actions/workflows/CI.yml">
    <img src="https://github.com/IntelLabs/kAFL/actions/workflows/CI.yml/badge.svg" alt="CI">
  </a>
  <a href="https://github.com/IntelLabs/kAFL/releases">
    <img alt="GitHub release (latest by date)" src="https://img.shields.io/github/v/release/IntelLabs/kAFL">
  </a>
  <a href="https://hub.docker.com/r/intellabs/kafl">
    <img alt="Docker Image Version (latest by date)" src="https://img.shields.io/docker/v/intellabs/kafl?label=Docker%20Image">
  </a>
  <a href="https://hub.docker.com/r/intellabs/kafl">
    <img alt="Docker Pulls" src="https://img.shields.io/docker/pulls/intellabs/kafl">
  </a>
  <a href="https://github.com/IntelLabs/kAFL/blob/master/LICENSE.md">
    <img alt="GitHub" src="https://img.shields.io/github/license/IntelLabs/kafl">
  </a>
</p>
<p align="center">
  <a href="https://IntelLabs.github.io/kAFL/">
    <img src="https://img.shields.io/badge/Online-Documentation-green?style=for-the-badge&logo=gitbook" alt="online_docs"/>
  </a>
</p>
kAFL/Nyx is a fast guided fuzzer for the x86 VM. It is great for anything that
executes as QEMU/KVM guest, in particular x86 firmware, kernels and full-blown
operating systems.

# Installation Guide

Run all commands as the root user.



## 0. Install dependencies

```BASH
apt-get install -y python3-dev python3-venv git build-essential
```

## 1. Install kAFL 

```BASH
git clone https://github.com/infosec-sogang/kAFL.git
cd kAFL
make deploy
reboot
```

## 2.  Build the Windows VM Template

```bash
cd kAFL
make deploy -- --tags examples,examples-template-windows
cd kAFL/kafl/examples/templates/windows
make build
make import
cd ../../windows_x86_64
make setup
make init
```

## 3. Provision the guest VM

```BASH
make provision_driver
```

## 4. Run Fuzz

```bash
kafl fuzz
```

