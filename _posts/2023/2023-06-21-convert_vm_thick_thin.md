---
title: Convert vSphere VM From Thick to Thin Provisioning
date: 2023-06-21 01:00:00 -0500
categories: [vsphere, hypervisor, virtualization]
tags: [vsphere,hypervisor,virtualization]
---

<img src="/assets/img/posts/2023/convert_vm_thick_thin/convert_vm_thick_thin.png" alt="Convert vSphere VM From Thick to Thin Provisioning" style="height:400px; width:600px;" />


If you're using vSphere and want to optimize storage usage by converting a VM from thick to thin provisioning, this blog post will guide you through the process. Thin provisioning allows you to allocate storage space dynamically, resulting in efficient utilization of your storage resources. We'll walk you through the steps for converting the VM from thick to thin provisioning.

## Prerequisites

Before proceeding, make sure you have the following:

- Access to vSphere management interface.
- Administrative privileges to perform VM-related operations.

## Converting/Cloning to Thin Disk Type

Follow these steps to convert the VM to thin provisioning:

1. Log into the vSphere web UI.
2. Enable the SSH service if it is not already enabled. Go to Actions ≫ Services ≫ Enable Secure Shell (SSH).
3. Shut down the target VM if it is currently running.
4. Select the target VM from the left navigation.
5. Expand the "Hard disk configuration" section.
6. Copy the folder and file name (e.g., WIN10PC/WIN10PC.vmdk) and paste it into a text document for reference at a later time.
7. Click on the virtual disk (.vmdk) file name link.
8. Copy the location path value displayed (e.g., /vmfs/volumes/5a0ce14d-5574951d-af28-4ccc6a87617d) and paste it into the text document.
9. Connect to the ESXi host via SSH.
10. Run the following commands:

```bash
# Change the directory to the datastore (update path as needed)
# (/vmfs/... path from above)
cd /vmfs/volumes/5a0ce14d-5574951d-af28-4ccc6a87617d

# Use vmkfstools to clone the virtual disk to thin provisioned
# Use the folder and file name copied from above
# Syntax:
# vmkfstools -i "<SOURCE FILE.vmdk>" -d thin "<TARGET THIN FILE.vmdk>"
vmkfstools -i "./WIN10PC/WIN10PC.vmdk" -d thin "./WIN10PC/WIN10PC-thin.vmdk"

# After the clone process completes, rename the source (thick) file
mv "./WIN10PC/WIN10PC.vmdk" "./WIN10PC/WIN10PC.vmdk.thick"

# Rename the target (thin) file to the original .vmdk file name
mv "./WIN10PC/WIN10PC-thin.vmdk" "./WIN10PC/WIN10PC.vmdk"
```

## Updating the VM Configuration

Follow these steps to update the VM configuration:

1. Back in the vSphere web UI, right-click on the VM and select "Unregister" and confirm.
2. Select "Virtual Machines" from the left navigation pane and click "Create/Register VM."
3. Select "Register an existing virtual machine" and click "Next."
4. Click the "Select one or more virtual machines, a datastore, or a directory" button and browse to the virtual machine directory.
5. Select the .vmx file and click "Select."
6. Click "Next" and then "Finish."
7. Select the virtual machine and click "Edit."
8. Expand the "Hard disk configuration" section.
9. Verify that the "Type" value now shows "Thin provisioned."
10. Start the VM to ensure it boots and runs without any issues.

## Cleaning Up

Follow these steps to clean up the old thick provisioned files:

1. After fully testing that the VM is functional, select "Storage" from the left navigation pane.
2. Click "Datastore browser" in the main content area.
3. Browse to the virtual machine directory.
4. Select the original thick .vmdk file (WIN10PC.vmdk.thick earlier).
5. Click "Delete" and confirm the action.

<br>

**Alternatively, you can run the following commands from the server's host command:**
```bash
cd /vmfs/volumes/5a0ce14d-5574951d-af28-4ccc6a87617d/WIN10PC
rm -rf WIN10PC.vmdk.thick
```
**VIP: BE CAREFUL ON THE NEXT STEP**
6. Rename the "WIN10PC-flat.vmdk" file:
```bash
mv WIN10PC-flat.vmdk WIN10PC-flat.vmdk.OLD
```
7. Launch the VM to ensure that it turns on successfully. If it does, proceed to the final step.
8. Delete the old "WIN10PC-flat.vmdk.OLD" and keep the "WIN10PC-thin-flat.vmdk" file. If you skip this step, extra storage will be allocated on the storage device.
```bash
rm -rf WIN10PC-flat.vmdk.OLD
```
Congratulations! You have successfully converted a vSphere VM from thick to thin provisioning. By doing so, you have optimized your storage utilization and improved resource efficiency.

