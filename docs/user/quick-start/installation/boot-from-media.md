---
title: Boot the media and test Solus
summary: A step-by-step guide on how to install Solus on your device
sidebar_position: 3
---

import BiosSpecificInstructions from '../../snippets/secureBoot/_biosSpecificInstructions.md'
import EnrollCertificateGuide from '../../snippets/secureBoot/_enrollCertificateInstructions.md'

# Boot the media and test solus

After you [prepare the bootable DVD or USB](/docs/category/create-bootable-media/) for Solus, use that media to boot into the Solus live environment. 

1. Insert your bootable DVD or USB drive into your computer.
1. Restart your computer to boot the DVD or USB. 

    Some computers automatically boot from DVDs and USB. If you experience issues booting the media, configure your computer to boot from DVD or USB.

    <BiosSpecificInstructions />

    Common ways to configure your computer to boot from media include:
	- Pressing the `F9`, `F12`, `DEL` or `ESC` keys right after turning on your computer (right after the manufacturer logo appears).
	- Pressing the `OPTION` key in some Mac computers.

2. If your computer has UEFI firmware and _secure boot_ is turned on, enroll the Solus certificate. 

    :::tip

	For instructions on how to enroll the Solus certificate in existing installations, see .

	:::

    <EnrollCertificateGuide />

3. Test Solus.

	The Solus live environment lets you test Solus before installing it on your computer.  Explore Solus's features and verify that all your hardware works properly.

If everything works properly, install Solus on your computer.