---
title: Input and Output Methods
description: There are two different approaches to console I/O, the choice of which depends on how much flexibility and control an application needs.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, character mode applications, command line applications, terminal applications, console api
MS-HAID:
- '\_win32\_input\_and\_output\_methods'
- 'base.input\_and\_output\_methods'
- 'consoles.input\_and\_output\_methods'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 55a86d5d-d0b1-4d0c-b42f-7342809289ad
---

# Input and Output Methods

There are two different approaches to console I/O, the choice of which depends on how much flexibility and control an application needs. The high-level approach enables simple character stream I/O, but it limits access to a console's input and screen buffers. The low-level approach requires that developers write more code and choose among a greater range of functions, but it also gives an application more flexibility.

> [!NOTE]
> The low-level approach is not recommended for new and ongoing development. Applications needing functionality from the low-level console I/O functions are encouraged to use **[virtual terminal sequences](console-virtual-terminal-sequences.md)** and explore our documentation on both **[classic functions versus virtual terminal](classic-vs-vt.md)** and **[the ecosystem roadmap](ecosystem-roadmap.md)**.

An application can use the file I/O functions, [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747), and the console functions, [**ReadConsole**](readconsole.md) and [**WriteConsole**](writeconsole.md), for high-level I/O that provides indirect access to a console's input and screen buffers. The high-level input functions filter and process the data in a console's input buffer to return input as a stream of characters, discarding mouse and buffer-resizing input. Similarly, the high-level output functions write a stream of characters that are displayed at the current cursor location in a screen buffer. An application controls the way these functions work by setting a console's I/O modes.

The low-level I/O functions provide direct access to a console's input and screen buffers, enabling an application to access mouse and buffer-resizing input events and extended information for keyboard events. Low-level output functions enable an application to read from or write to a specified number of consecutive character cells in a screen buffer, or to read or write to rectangular blocks of character cells at a specified location in a screen buffer. A console's input modes affect low-level input by enabling the application to determine whether mouse and buffer-resizing events are placed in the input buffer. A console's output modes have no effect on low-level output.

The high-level and low-level I/O methods are not mutually exclusive, and an application can use any combination of these functions. Typically, however, an application uses one approach or the other exclusively and we recommend focusing on one particular paradigm for optimal results.

> [!TIP]
> The ideal forward looking application will focus on the high-level methods and augment further needs with **[virtual terminal sequences](console-virtual-terminal-sequences.md)** through the high-level I/O methods when necessary avoiding the use of low-level I/O functions entirely.

The following topics describe the console modes and the high-level and low-level I/O functions.

- [Console Modes](console-modes.md)
- [High-Level Console I/O](high-level-console-i-o.md)
- [High-Level Console Modes](high-level-console-modes.md)
- [High-Level Console Input and Output Functions](high-level-console-input-and-output-functions.md)
- [Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)
- [Classic Functions versus Virtual Terminal Sequences](classic-vs-vt.md)
- [Ecosystem Roadmap](ecosystem-roadmap.md)
- [Low-Level Console I/O](low-level-console-i-o.md)
- [Low-Level Console Modes](low-level-console-modes.md)
- [Low-Level Console Input Functions](low-level-console-input-functions.md)
- [Low-Level Console Output Functions](low-level-console-output-functions.md)
