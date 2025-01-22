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




