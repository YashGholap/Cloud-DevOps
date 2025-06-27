
## What is `/dev` ?
- **What it is**: A directory containing **device files**.    
- **Used for**: Interacting with hardware devices (disks, USB, serial ports, etc.) as if they were regular files.
- **Examples**:
    
    - `/dev/sda` → a hard disk
        
    - `/dev/ttyUSB0` → a USB serial device
        
    - `/dev/null`, `/dev/zero` → pseudo-devices

**Key idea**: In Unix-like systems, _everything is a file_, including devices.

## What is `/sys` ?
- **What it is**: A **virtual filesystem** (sysfs) that exposes **kernel objects and device information**.
- **Used for**: Reading and modifying kernel and hardware parameters from userspace.
- **Examples**:
    
    - `/sys/class/net/` → info about network interfaces
        
    - `/sys/block/sda/size` → size of disk
        
    - `/sys/devices/` → full device tree

**Key idea**: It shows the **structure of the device tree** and allows **configuration or monitoring** of kernel internals.

## what is `udev` ?
- **What it is**: A **userspace daemon** that manages `/dev`.
- **Used for**:
    - Dynamically creating/removing device files in `/dev`
        
    - Assigning persistent names (e.g., `/dev/disk/by-label`)
        
    - Triggering actions (e.g., automount USB, start services)

**Key idea**: It’s the **manager** that watches hardware events and makes `/dev` reflect real connected devices.

## lsusb, lspci & lsscsi

- Just like we would use the ls command to list files and directories, we can use similar tools that list information about devices.

### **Listing USB Devices**

```bash
lsusb
```

**Listing PCI Devices**

```bash
lspci
```

**Listing SCSI Devices**

```bash
lsscsi
```

*Note: To be able to use we need to install the `usbutils` , `pciutils` & `lsscsi`*

## dd

`dd` is a low-level Unix utility for copying and converting data byte-for-byte. You specify:

- **`if=`** (input file/device)
- **`of=`** (output file/device)
- **`bs=`** (block size)
- **`count=`** (number of blocks)

It’s commonly used to:

- Clone disks or partitions
- Create or restore raw disk images
- Generate files filled with a pattern (e.g., zeros or random data from `/dev/zero` or `/dev/urandom`)

Example—make a 100 MiB zero-filled file:
```bash
dd if=/dev/zero of=zero.img bs=1M count=100
```

