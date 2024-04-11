---
title: Secure boot
summary: Instructions for enrolling the Solus Certificate when Secure Boot is enabled.
sidebar_position: 2
---

# Secure boot in Solus

Secure Boot is a security feature enabled by default on most modern computers. Secure Boot helps ensure only trusted software can launch at startup.

Solus supports secure boot since version 4.4. 

## Why is enrolling the Solus certificate necessary?

To enable compatibility with secure boot, Solus uses a third-party component called "shim". Solus's shim is already signed by Microsoft, but it doesn't include Solus's certificate by default. 

Because of that, you need to enroll the Solus certificate during your first boot.

## Why doesn't Solus have its own signed shim?

To avoid the one-time step of enrolling the Solus certificate, Solus would have to get it's own shim EFI executable signed by Microsoft. To get one, Solus would need to:

- Obtain an expensive EV Certificate
- Register for the Microsoft Windows Hardware Developer Program.
- Implement any additional security requirements as required by the [shim-review](https://github.com/rhboot/shim-review/) process.

We understand enrolling the certificate might be confusing, but obtaining our own signed shim is not practical at this time.

Thanks to our supporters on [OpenCollective](https://opencollective.com/getsolus), obtaining an EV certificate in the future is a possibility. This would eliminate the need for manual enrollment.

## Useful Links for Additional Reading

- https://learn.microsoft.com/windows-hardware/drivers/dashboard/file-signing-reqs
- https://github.com/rhboot/shim-review/
- https://github.com/rhboot/shim/
