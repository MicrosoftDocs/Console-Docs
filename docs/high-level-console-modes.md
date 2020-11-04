---
title: High-Level Console Modes
description: The behavior of the high-level console functions is affected by the console input and output modes.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, character mode applications, command line applications, terminal applications, console api
MS-HAID:
- '\_win32\_high\_level\_console\_modes'
- 'base.high\_level\_console\_modes'
- 'consoles.high\_level\_console\_modes'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 3ec915eb-333d-484d-a14d-46377b503ecc
---

# High-Level Console Modes

The behavior of the high-level console functions is affected by the console input and output modes. All of the following console input modes are enabled for a console's input buffer when a console is created:

- Line input mode
- Processed input mode
- Echo input mode

Both of the following console output modes are enabled for a console screen buffer when it is created:

- Processed output mode
- Wrapping at EOL output mode

All three input modes, along with processed output mode, are designed to work together. It is best to either enable or disable all of these modes as a group. When all are enabled, the application is said to be in "cooked" mode, which means that most of the processing is handled for the application. When all are disabled, the application is in "raw" mode, which means that input is unfiltered and any processing is left to the application.

An application can use the [`GetConsoleMode`](getconsolemode.md) function to determine the current mode of a console's input buffer or screen buffer. You can enable or disable any of these modes by using the following values in the [`SetConsoleMode`](setconsolemode.md) function. Note that setting the output mode of one screen buffer does not affect the output mode of other screen buffers.

[!INCLUDE [console-mode-flags](./includes/console-mode-flags.md)]
