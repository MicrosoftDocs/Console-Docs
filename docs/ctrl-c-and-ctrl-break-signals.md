---
title: CTRL+C and CTRL+BREAK Signals
description: The CTRL+C and CTRL+BREAK key combinations receive special handling by console processes.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
ms.localizationpriority: high
keywords: console, character mode applications, command line applications, terminal applications, console api
MS-HAID:
- '\_win32\_ctrl\_c\_and\_ctrl\_break\_signals'
- 'base.ctrl\_c\_and\_ctrl\_break\_signals'
- 'consoles.ctrl\_c\_and\_ctrl\_break\_signals'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 5357ed99-920b-47a0-a922-d5faed7bf23e
---

# CTRL+C and CTRL+BREAK Signals


The <kbd>CTRL</kbd>+<kbd>C</kbd> and <kbd>CTRL</kbd>+<kbd>BREAK</kbd> key combinations receive special handling by console processes. By default, when a console window has the keyboard focus, <kbd>CTRL</kbd>+<kbd>C</kbd> or <kbd>CTRL</kbd>+<kbd>BREAK</kbd> is treated as a signal (SIGINT or SIGBREAK) and not as keyboard input. By default, these signals are passed to all console processes that are attached to the console. (Detached processes are not affected. See [**Creation of a Console**](creation-of-a-console.md).) The system creates a new thread in each client process to handle the event. The thread raises an exception if the process is being debugged. The debugger can handle the exception or continue with the exception unhandled.

<kbd>CTRL</kbd>+<kbd>BREAK</kbd> is always treated as a signal, but an application can change the default <kbd>CTRL</kbd>+<kbd>C</kbd> behavior in two ways that prevent the handler functions from being called:

- The [**SetConsoleMode**](setconsolemode.md) function can disable the **ENABLE\_PROCESSED\_INPUT** input mode for a console's input buffer, so CTRL+C is reported as keyboard input rather than as a signal.
- When [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) is called with **NULL** and **TRUE** values for its parameters, the calling process ignores CTRL+C signals. Normal CTRL+C processing is restored by calling **SetConsoleCtrlHandler** with **NULL** and **FALSE** values. This attribute of ignoring or not ignoring CTRL+C signals is inherited by child processes, but it can be enabled or disabled by any process without affecting existing processes.

For more information on how these signals are processed, including timeouts, please see the [**Handler Routine**](handlerroutine.md) callback documentation.
