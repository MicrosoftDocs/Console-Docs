---
title: Console Control Handlers
description: Each console process has its own list of control handler functions that are called by the system when the process receives a CTRL+C, CTRL+BREAK, or CTRL+CLOSE signal.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, character mode applications, command line applications, terminal applications, console api
MS-HAID:
- '\_win32\_console\_control\_handlers'
- 'base.console\_control\_handlers'
- 'consoles.console\_control\_handlers'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 6480e8ee-d228-4c07-99df-de1e0c3ca250
---

# Console Control Handlers

Each console process has its own list of control handler functions that are called by the system when the process receives a [CTRL+C](ctrl-c-and-ctrl-break-signals.md), [CTRL+BREAK](ctrl-c-and-ctrl-break-signals.md), or [CTRL+CLOSE](ctrl-close-signal.md) signal. Initially, the list of control handlers for each process contains only a default handler function that calls the [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) function. A console process can add or remove additional [**HandlerRoutine**](handlerroutine.md) functions by calling the [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) function. This function does not affect the lists of control handlers for other processes. When a console process receives any of the control signals, it calls the handler functions on a last-registered, first-called basis until one of the handlers returns **TRUE**. If none of the handlers returns **TRUE**, the default handler is called.

The function's *dwCtrlType* parameter identifies which control signal was received, and the return value indicates whether the signal was handled.

A new thread is started inside the command-line client process to run the handler routines. More information on the timeout values and action of this thread can be found in the [**HandlerRoutine**](handlerroutine.md#remarks) function documentation.

For an example of a control handler function, see [Registering a Control Handler Function](registering-a-control-handler-function.md).