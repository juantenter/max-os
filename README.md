# 🖥️ MaxOS

**A tiny, from-scratch x86 operating system.**

MaxOS is a hobby operating system project currently in early development. It boots in QEMU and provides a custom terminal environment with its own branding and shell.

```text
 __  __    _    __  __  ___  ____  
|  \/  |  / \  |  \/  |/ _ \/ ___| 
| |\/| | / _ \ | |\/| | | | \___ \ 
| |  | |/ ___ \| |  | | |_| |___) |
|_|  |_/_/   \_\_|  |_|\___/|____/ 
```

## ✨ Features

- Custom x86 operating system
- Custom MaxOS boot screen and ASCII logo
- Command-line shell
- `help` and `fastfetch` commands
- Runs in QEMU without modifying your host operating system

## 📦 Requirements

- [QEMU](https://www.qemu.org/)
- Git
- The `maxos.img` disk image included in this repository

## 🚀 Getting started

### 1. Clone the repository

```bash
git clone https://github.com/juantenter/max-os.git
cd max-os
```

Make sure `maxos.img` exists in the repository directory:

```bash
ls maxos.img
```

On Windows PowerShell, use:

```powershell
Get-Item .\maxos.img
```

If the image is not included in the repository, download it from the project's Releases or other location provided by the maintainer.

### 2. Install QEMU

Choose the instructions for your operating system.

#### Windows 10/11

Open PowerShell and run:

```powershell
winget install --id SoftwareFreedomConservancy.QEMU -e
```

Close and reopen PowerShell after installation.

#### Linux

**Ubuntu / Debian:**

```bash
sudo apt update
sudo apt install qemu-system-x86 git
```

**Arch Linux:**

```bash
sudo pacman -S qemu-system-x86 git
```

**Fedora:**

```bash
sudo dnf install qemu-system-x86 git
```

#### macOS

Install [Homebrew](https://brew.sh/) if necessary, then run:

```bash
brew install qemu git
```

#### FreeBSD

Install QEMU and Git:

```sh
sudo pkg install qemu git
```

If your FreeBSD setup does not have `sudo`, run the package command as root.

## 💻 Boot MaxOS

Run these commands from the repository directory containing `maxos.img`.

### Windows 11

```powershell
& "C:\Program Files\qemu\qemu-system-i386.exe" -drive "file=$((Resolve-Path .\maxos.img).Path),format=raw,if=floppy" -boot a -m 128
```

If QEMU is available through your PATH, you can instead run:

```powershell
qemu-system-i386 -drive "file=$((Resolve-Path .\maxos.img).Path),format=raw,if=floppy" -boot a -m 128
```

### Linux

```bash
qemu-system-i386 -drive file=maxos.img,format=raw,if=floppy -boot a -m 128
```

### macOS

```bash
qemu-system-i386 -drive file=maxos.img,format=raw,if=floppy -boot a -m 128
```

### FreeBSD

```sh
qemu-system-i386 -drive file=maxos.img,format=raw,if=floppy -boot a -m 128
```

These commands launch a virtual x86 machine with 128 MB of RAM and attach `maxos.img` as a virtual floppy disk.

**Note:** These instructions assume the image remains a bootable floppy-style raw image. If the bootloader or image format changes, the QEMU arguments may need updating.

## ⌨️ Using MaxOS

After the system boots, try the commands available in the shell.

```text
help
fastfetch
```

The `help` command lists supported commands. Use it to discover what your version of MaxOS implements.

## 🧪 Troubleshooting

**QEMU command not found**

Check that QEMU is installed and that its executable directory is available through your PATH. On Windows, you can also invoke `qemu-system-i386.exe` using its full installation path.

**Image file not found**

Run the command from the directory containing `maxos.img`, or provide the full path to the image.

**Black screen or boot failure**

The image may be damaged, the bootloader may not be compatible with the selected virtual hardware, or the image format may have changed. Verify the image and check the project's latest instructions.

**QEMU opens but MaxOS does not start**

Check that the image is the expected bootable x86 image and that the selected floppy boot configuration matches the current build.

## 🛠️ Development

MaxOS is an experimental operating system project. Features and requirements may change as development continues.

Contributions, bug reports, and suggestions are welcome.

If you want to contribute, fork the repository, make your changes on a branch, and submit a pull request.

## ⚠️ Disclaimer

MaxOS is experimental software intended for learning and testing.

The commands in this README run MaxOS inside a virtual machine. They do not install it onto your physical hard drive.

Do not write experimental disk images directly to physical disks unless you fully understand the risks and have appropriate backups.

## 📄 License

See the repository's `LICENSE` file. If no license has been added, the project should not be assumed to be open source under a particular license until one is chosen.

---

Made with curiosity, code, and a little bit of terminal magic. 🥀

**MaxOS | Built by Tenter**
