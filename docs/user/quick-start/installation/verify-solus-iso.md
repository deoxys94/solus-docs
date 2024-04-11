---
title: Verify the Solus ISO file
summary: Confirm the integrity and authenticity of your ISO file
sidebar_position: 1
---

# Verify the Solus ISO file

## Linux and macOS
1. Open a terminal.
2. Verify the file signature of the SHA256SUM file:
    1. Import Solus's public key:

    ```bash
    cd ~/path/to/download/directory
    gpg --import solus-releng-pub.gpg
    ```
    2. Verify the SHA256SUM file:

    ```bash
    gpg --verify Solus-4.5-Budgie.iso.sha256sum.sign Solus-4.5-Budgie.iso.sha256sum
    ```

    If the checksum file is authentic, the terminal displays the following:

    ```bash
    gpg: Signature made Tue 09 Jan 2024 02:35:10 CST
    gpg:                using RSA key F5F6685CAF5559771D9CCB92618EB3600BD32D59
    gpg: Good signature from "Solus (Release & Engineering) <releng@getsol.us>" [unknown]
    ```
3. Verify the integrity of the Solus ISO file.

    ```bash
    sha256sum -c Solus-4.5-Budgie.iso.sha256sum | grep OK
    ```

    If the ISO file is OK, the terminal displays:

    ```bash
    Solus-4.5-Budgie.iso: OK
    ```

## Windows

1. Install [gpg4win](https://www.gpg4win.org/).
2. Verify the file signature of the SHA256SUM file:
    1. Open Powershell
    2. Import Solus's public key:

    ```powershell
    cd ~/path/to/download/directory
    gpg --import solus-releng-pub.gpg
    ```
    2. Verify the SHA256SUM file:

    ```powershell
    gpg --verify Solus-4.5-Budgie.iso.sha256sum.sign Solus-4.5-Budgie.iso.sha256sum
    ```

    If the checksum file is authentic, the terminal displays the following:

    ```powershell
    gpg: Signature made Tue 09 Jan 2024 02:35:10 CST
    gpg:                using RSA key F5F6685CAF5559771D9CCB92618EB3600BD32D59
    gpg: Good signature from "Solus (Release & Engineering) <releng@getsol.us>" [unknown]
    ```
3. Verify the integrity of the Solus ISO file.
   1. Execute the following powershell command:
    ```powershell
    Get-FileHash C:\path\to\Solus-4.5-Budgie.iso
    ```

    Powershell displays the SHA256 hash of your ISO file.
    ```powershell
    Algorithm       Hash                                                                   Path
    ---------       ----                                                                   ----
    SHA256          E3B0C44298FC1C149AFBF4C8996FB92427AE41E4649B934CA495991B7852B855       C:\path\to\Solus-4.5-Budgie.iso
    ```

    2. Compare the output with the contents of the SHA256SUM file. 
    
        The contents of the SHA256SUM file must match the hash value in Powershell.

After verifying the Solus's ISO file, you can [create bootable media](/docs/category/create-bootable-media/).