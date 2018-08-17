---
title: CTRL+C and CTRL+BREAK Signals
description: The CTRL+C and CTRL+BREAK key combinations receive special handling by console processes.
author: bitcrazed
ms.author: richturn
ms.topic: article
ms.prod: console
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


The CTRL+C and CTRL+BREAK key combinations receive special handling by console processes. By default, when a console window has the keyboard focus, CTRL+C or CTRL+BREAK is treated as a signal (SIGINT or SIGBREAK) and not as keyboard input. By default, these signals are passed to all console processes that are attached to the console. (Detached processes are not affected.) The system creates a new thread in each client process to handle the event. The thread raises an exception if the process is being debugged. The debugger can handle the exception or continue with the exception unhandled.

CTRL+BREAK is always treated as a signal, but an application can change the default CTRL+C behavior in two ways that prevent the handler functions from being called:

- The [**SetConsoleMode**](setconsolemode.md) function can disable the **ENABLE\_PROCESSED\_INPUT** input mode for a console's input buffer, so CTRL+C is reported as keyboard input rather than as a signal.
- When [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) is called with **NULL** and **TRUE** values for its parameters, the calling process ignores CTRL+C signals. Normal CTRL+C processing is restored by calling **SetConsoleCtrlHandler** with **NULL** and **FALSE** values. This attribute of ignoring or not ignoring CTRL+C signals is inherited by child processes, but it can be enabled or disabled by any process without affecting existing processes.

 

 




