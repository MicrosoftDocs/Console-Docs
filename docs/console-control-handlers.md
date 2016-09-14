---
title: Console Control Handlers
description: Each console process has its own list of control handler functions that are called by the system when the process receives a CTRL+C, CTRL+BREAK, or CTRL+CLOSE signal.
MS-HAID:
- '\_win32\_console\_control\_handlers'
- 'base.console\_control\_handlers'
- 'consoles.console\_control\_handlers'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 6480e8ee-d228-4c07-99df-de1e0c3ca250
keywords: ["consoles", "consoles,control handlers", "control handler functions"]
---

# Console Control Handlers


Each console process has its own list of control handler functions that are called by the system when the process receives a [CTRL+C](ctrl-c-and-ctrl-break-signals.md), [CTRL+BREAK](ctrl-c-and-ctrl-break-signals.md), or [CTRL+CLOSE](ctrl-close-signal.md) signal. Initially, the list of control handlers for each process contains only a default handler function that calls the [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) function. A console process can add or remove additional [**HandlerRoutine**](handlerroutine.md) functions by calling the [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) function. This function does not affect the lists of control handlers for other processes. When a console process receives any of the control signals, it calls the handler functions on a last-registered, first-called basis until one of the handlers returns **TRUE**. If none of the handlers returns **TRUE**, the default handler is called.

The function's *dwCtrlType* parameter identifies which control signal was received, and the return value indicates whether the signal was handled.

For an example of a control handler function, see [Registering a Control Handler Function](registering-a-control-handler-function.md).

 

 




