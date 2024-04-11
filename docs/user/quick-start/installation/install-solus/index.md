---
title: Install Solus to your computer
summary: Overview of the partitioning that the installer can perform
sidebar_position: 4
---

# Install Solus to your computer

:::danger[Warning]

Installing Solus to your computer might cause permanent data loss.

When you install Solus, make sure you select the appropriate drive or backup your files beforehand.

:::

## Welcome screen
![Welcome screen](welcome-screen.png)

The **Welcome** screen lets you select the language the installer uses during the installation process.

If your system does not meet the minimum requirements, the welcome screen displays the issues that you need to fix to install Solus.

## Location
![Location screen](location.png)

The **Location** screen lets you configure:

- Your region.
- Your time zone.
- The system language.
- The locales of your system (date and number formatting, character encoding settings, and so on).

## Keyboard
![Keyboard screen](keyboard.png)
The **Keyboard** screen lets you configure:

- The physical distribution of your keyboard.
- The keyboard layout Solus will use.

Use the text area on screen to test your keyboard settings.

## Partitions
![Partitions screen](partitions.png)
The **Partitions** screen lets you configure:

- The drive that will be used as the installation target for Solus.
- Whether Solus will use the entire drive or share space with another operating system (dual-boot).
- The partitioning scheme of the drives.
- Whether you want to encrypt your Solus install.
- The filesystem Solus will use.
- Whether Solus will use a swap partition.

### Installation options
The partitions screen provides multiple ways to install Solus on your computer.

- **Install alongside**: Shrinks the largest partition in the target drive and install Solus there.
- **Replace a partition**: Installs solus in the partition you select. This is useful if you already created a partition for Solus.
- **Erase disk**: Deletes the contents of the selected drive and installs Solus as the only operating system.
- **Manual partitioning**: If you are an advanced user, you can define your preferred partition scheme to install Solus.

   **Note:** Legacy (BIOS) must use MBR partition table while Unified EFI (UEFI) must use GPT partition table.

## UEFI

If you are using a system with UEFI, you may need to create a EFI System Partition, also referred to as an ESP. This is not necessary if you are enabling Solus to install onto the entire disk.

To create an EFI System Partition, open up GParted and create a FAT32 partition that is 1GB in size. Next, right-click on the partition and click Manage Flags. On the Manage Flags section, enable the `boot` and `esp` flags.

**Notes:**

- Your system must be booted using Unified EFI (UEFI) mode, as opposed to a "legacy (BIOS) mode".
- Your disk is required to be GPT formatted.
- If you cannot see your SSD drive, set the SATA configuration to AHCI.

## Install Solus alongside your current operating system (dual-boot)
