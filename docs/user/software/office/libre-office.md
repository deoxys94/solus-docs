---
title: LibreOffice
summary: A guide to the default applications included with Solus.
---

# LibreOffice

Solus has LibreOffice pre-installed. LibreOffice is an is an open-source office suite capable of replacing commercial programs like Microsoft Office and Apple iWork. 

LibreOffice provides a set of tools for all office needs needs, including word processing, spreadsheets, presentations, and databases. LibreOffice is compatible with the Microsoft Office and iWork file formats.

## Spell checker

By default, LibreOffice only includes spellchecking dictionaries for English. To enable spellchecking in other languages: 

- Install `libreoffice-common-dictionaries` from the software center.

### Finnish language

To enable spell checking for the finnish language:

1. Install `libreoffice-voikko` from the software center.
1. Open LibreOffice Writer,
1. Go to **Tools** > **Options**.
    The **Options** screen opens.
1. In the **Options** screen, go to **Languages and Locales** > **Writing Aids**.
1. Under **Available Language Modules**, ensure the following modules are selected:
    - Spellchecker (Voikko)
    - Grammar checker (Voikko)
    - Hyphenator (Voikko)
1. Under **Languages and Locales**, click **Voikko**.
1. Ensure **standard: suomi (perussanasto)** is selected.
1. Click **OK**.
