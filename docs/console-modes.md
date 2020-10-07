---
title: Console Modes
description: Associated with each console input buffer is a set of input modes that affects input operations.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, character mode applications, command line applications, terminal applications, console api
MS-HAID:
- '\_win32\_console\_modes'
- 'base.console\_modes'
- 'consoles.console\_modes'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: f0dcc123-3b12-44c4-8f94-920203f5198e
---

# Console Modes

Associated with each console input buffer is a set of input modes that affects input operations. Similarly, each console screen buffer has a set of output modes that affects output operations. The input modes can be divided into two groups: those that affect the high-level input functions and those that affect the low-level input functions. The output modes only affect applications that use the high-level output functions.

The [**GetConsoleMode**](getconsolemode.md) function reports the current input mode of a console's input buffer or the current output mode of a screen buffer. The [**SetConsoleMode**](setconsolemode.md) function sets the current mode of either a console input buffer or a screen buffer. If a console has multiple screen buffers, the output modes of each can be different. An application can change I/O modes at any time. For more information about the console modes that affect high-level and low-level I/O operations, see [High-Level Console Modes](high-level-console-modes.md) and [Low-Level Console Modes](low-level-console-modes.md).

A command-line application should expect that other command-line applications may change the console mode at any time and may not restore it to its original form before control is returned. Additionally, we recommend that all command-line applications should capture the initial console mode at startup and attempt to restore it when exiting to ensure minimal impact on other command-line applications attached to the same console.

The [**GetConsoleDisplayMode**](getconsoledisplaymode.md) function reports whether the current console is in full-screen mode.
