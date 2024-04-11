---
title: Windows
summary: Download and verify the ISO file Solus provides.
---

import BeforeYouBegin from '../../../snippets/_createMedia_beforeYouBegin.md'
import USBDataLossWarning from '../../../snippets/_createMedia_dataLossWarning.md'
import BalenaEtcherInstructions from '../../../snippets/_createMedia_balenaEtcher.md'

# Create bootable media - Windows

<BeforeYouBegin />

## DVD

Since Windows 7, you can use the built-in system tools to create a bootable DVD.

1. Insert a blank DVD into your DVD writer.

   Either DVD-R or DVD+RW are ok.
1. From the start menu, open **File Explorer**.
1. Go to the folder that contains the Solus ISO file.
1. If you use Windows 11, right-click the Solus ISO file and click **Show more options** > **Burn disc image**.
1. If you use previous versions of Windows (Windows 7-10), right-click the Solus ISO file and click **Burn disc image**.
1. Select your DVD drive in the **Disc burner** list.
1. Click **Burn**.

## USB

<USBDataLossWarning />

<BalenaEtcherInstructions os="Windows" />