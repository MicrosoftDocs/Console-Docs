---
title: Creation of a Console
description: The system creates a new console when it starts a console process, a character-mode process whose entry point is the main function.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, character mode applications, command line applications, terminal applications, console api
MS-HAID:
- '_win32_creation_of_a_console'
- 'base.creation_of_a_console'
- 'consoles.creation_of_a_console'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 84ec2559-cade-447e-8594-5b824d3d3e81
---

# Creation of a Console

The system creates a new console when it starts a *console process*, a character-mode process whose entry point is the `main` function. For example, the system creates a new console when it starts the command processor `cmd.exe`. When the command processor starts a new console process, the user can specify whether the system creates a new console for the new process or whether it inherits the command processor's console.

A process can create a console by using one of the following methods:

- A graphical user interface (GUI) or console process can use the [`CreateProcess`](https://msdn.microsoft.com/library/windows/desktop/ms682425) function with `CREATE_NEW_CONSOLE` to create a console process with a new console. (By default, a console process inherits its parent's console, and there is no guarantee that input is received by the process for which it was intended.)
- A GUI or console process that is not currently attached to a console can use the [`AllocConsole`](allocconsole.md) function to create a new console. (GUI processes are not attached to a console when they are created. Console processes are not attached to a console if they are created using [`CreateProcess`](https://msdn.microsoft.com/library/windows/desktop/ms682425) with `DETACHED_PROCESS`.)

Typically, a process uses [`AllocConsole`](allocconsole.md) to create a console when an error occurs requiring interaction with the user. For example, a GUI process can create a console when an error occurs that prevents it from using its normal graphical interface, or a console process that does not normally interact with the user can create a console to display an error.

A process can also create a console by specifying the `CREATE_NEW_CONSOLE` flag in a call to [`CreateProcess`](https://msdn.microsoft.com/library/windows/desktop/ms682425). This method creates a new console that is accessible to the child process but not to the parent process. Separate consoles enable both parent and child processes to interact with the user without conflict. If this flag is not specified when a console process is created, both processes are attached to the same console, and there is no guarantee that the correct process will receive the input intended for it. Applications can prevent confusion by creating child processes that do not inherit handles of the input buffer, or by enabling only one child process at a time to inherit an input buffer handle while preventing the parent process from reading console input until the child has finished.

Creating a new console results in a new console window, as well as separate I/O screen buffers. The process associated with the new console uses the [`GetStdHandle`](getstdhandle.md) function to get the handles of the new console's input and screen buffers. These handles enable the process to access the console.

When a process uses [`CreateProcess`](https://msdn.microsoft.com/library/windows/desktop/ms682425), it can specify a [`STARTUPINFO`](https://msdn.microsoft.com/library/windows/desktop/ms686331) structure, whose members control the characteristics of the first new console (if any) created for the child process. The `STARTUPINFO` structure specified in the call to `CreateProcess` affects a console created if the `CREATE_NEW_CONSOLE` flag is specified. It also affects a console created if the child process subsequently uses [`AllocConsole`](allocconsole.md). The following console characteristics can be specified:

- Size of the new console window, in character cells
- Location of the new console window, in screen pixel coordinates
- Size of the new console's screen buffer, in character cells
- Text and background color attributes of the new console's screen buffer
- Display name for the title bar of the new console's window

The system uses default values if the [`STARTUPINFO`](https://msdn.microsoft.com/library/windows/desktop/ms686331) values are not specified. A child process can use the [`GetStartupInfo`](https://msdn.microsoft.com/library/windows/desktop/ms683230) function to determine the values in its `STARTUPINFO` structure.

A process cannot change the location of its console window on the screen, but the following console functions are available to set or retrieve the other properties specified in the [`STARTUPINFO`](https://msdn.microsoft.com/library/windows/desktop/ms686331) structure.

| Function | Description |
|-|-|
| [`GetConsoleScreenBufferInfo`](getconsolescreenbufferinfo.md) | Retrieves the window size, screen buffer size, and color attributes. |
| [`SetConsoleWindowInfo`](setconsolewindowinfo.md)  | Changes the size of the console window.  |
| [`SetConsoleScreenBufferSize`](setconsolescreenbuffersize.md) | Changes the size of the console screen buffer. |
| [`SetConsoleTextAttribute`](setconsoletextattribute.md) | Sets the color attributes.  |
| [`SetConsoleTitle`](setconsoletitle.md)  | Sets the console window title. |
| [`GetConsoleTitle`](getconsoletitle.md)  | Retrieves the console window title.  |

A process can use the [`FreeConsole`](freeconsole.md) function to detach itself from an inherited console or from a console created by [`AllocConsole`](allocconsole.md).

A process can use the [`AttachConsole`](attachconsole.md) function to attach itself to another existing console session after using [`FreeConsole`](freeconsole.md) to detach from its own session (or if there is otherwise no attached session).
