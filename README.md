# Proxmox-Based Home Server

This repository documents the steps to configure a home server using Proxmox, a powerful open-source platform for server virtualization.

---

## Proxmox Setup

After installing Proxmox, some configurations are needed to optimize storage before creating virtual machines (VMs).

### Adjusting Storage: Deleting `local-lvm` to Increase Storage

Follow these steps to reallocate space from the default `local-lvm`:

1. **Access Storage Settings:**
   - Navigate to `Datacenter > Storage` in the Proxmox web interface.
   - Delete the `local-lvm` storage entry (`local-lvm (proxmox)`).

2. **Resize Logical Volumes via Shell:**
   Open the Proxmox shell and execute the following commands:
   ```bash
   lvremove /dev/pve/data
   lvresize -l +100%FREE /dev/pve/root
   resize2fs /dev/mapper/pve-root

 ## TrueNAS Setup  
1. **Add data storage to VMs(TrueNAS)
   Go to Datacenter>pve>disks and wipe the required disk. Initialize it as GPT
   Go to LVM-thin and create the thin pool. Add the disk to LVM-thin
   Go to created VM(TrueNAS)>Hardware and add a hard disk. Check details and add the required storage disk

2. **Set static IP for TrueNAS
   Go to TrueNAS WebGUI>Network>Interfaces and add the required static IP using the add button




