---
title: Character Mode Applications
description: Consoles manage input and output (I/O) for character-mode applications (applications that do not provide their own graphical user interface).
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, character mode applications, command line applications, terminal applications, console api
MS-HAID:
- '_win32_character_mode_applications'
- 'base.character_mode_applications'
- 'consoles.character_mode_applications'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: ea3ea214-892c-4953-bc22-7905efbc173f
---

# Character Mode Applications

Consoles manage input and output (I/O) for character-mode applications (applications that do not provide their own graphical user interface).

The console functions enable different levels of access to a console. The high-level console I/O functions enable an application to read from standard input to retrieve keyboard input stored in a console's input buffer. The functions also enable an application to write to standard output or standard error to display text in the console's screen buffer. The high-level functions also support redirection of standard handles and control of console modes for different I/O functionality. The low-level console I/O functions enable applications to receive detailed input about keyboard and mouse events, as well as events involving user interactions with the console window. The low-level functions also enable greater control of output to the screen.

This overview describes support for character-mode applications.

- [About Consoles](about-character-mode-applications.md)
- [Using the Console](using-the-console.md)
- [Console Reference](console-reference.md)
