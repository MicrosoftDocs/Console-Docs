---
title: Console Handles
description: A console process uses handles to access the input and screen buffers of its console, including the GetStdHandle, CreateFile, or CreateConsoleScreenBuffer functions.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, character mode applications, command line applications, terminal applications, console api
MS-HAID:
- '\_win32\_console\_handles'
- 'base.console\_handles'
- 'consoles.console\_handles'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: dc723046-b3e9-418a-b386-79be411e5ac8
ms.localizationpriority: high
---

# Console Handles

A console process uses handles to access the input and screen buffers of its console. A process can use the [**GetStdHandle**](getstdhandle.md), [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858), or [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) function to open one of these handles.

The [**GetStdHandle**](getstdhandle.md) function provides a mechanism for retrieving the standard input (`STDIN`), standard output (`STDOUT`), and standard error (`STDERR`) handles associated with a process. During console creation, the system creates these handles. Initially, `STDIN` is a handle to the console's input buffer, and `STDOUT` and `STDERR` are handles of the console's active screen buffer. However, the [**SetStdHandle**](setstdhandle.md) function can redirect the standard handles by changing the handle associated with `STDIN`, `STDOUT`, or `STDERR`. Because the parent's standard handles are inherited by any child process, subsequent calls to **GetStdHandle** return the redirected handle. A handle returned by **GetStdHandle** may, therefore, refer to something other than console I/O. For example, before creating a child process, a parent process can use **SetStdHandle** to set a pipe handle to be the `STDIN` handle that is inherited by the child process. When the child process calls **GetStdHandle**, it gets the pipe handle. This means that the parent process can control the standard handles of the child process. The handles returned by **GetStdHandle** have `GENERIC_READ | GENERIC_WRITE` access unless **SetStdHandle** has been used to set the standard handle to have lesser access.

The value of the handles returned by [**GetStdHandle**](getstdhandle.md) are not 0, 1, and 2, so the standard predefined stream constants in Stdio.h (`STDIN`, `STDOUT`, and `STDERR`) cannot be used in functions that require a console handle.

The [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) function enables a process to get a handle to its console's input buffer and active screen buffer, even if `STDIN` and `STDOUT` have been redirected. To open a handle to a console's input buffer, specify the `CONIN$` value in a call to **CreateFile**. Specify the `CONOUT$` value in a call to **CreateFile** to open a handle to a console's active screen buffer. **CreateFile** enables you to specify the read/write access of the handle that it returns.

The [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) function creates a new screen buffer and returns a handle. This handle can be used in any function that accepts a handle to console output. The new screen buffer is not active (displayed) until its handle is specified in a call to the [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) function. Note that changing the active screen buffer does not affect the handle returned by [**GetStdHandle**](getstdhandle.md). Similarly, using [**SetStdHandle**](setstdhandle.md) to change the `STDOUT` handle does not affect the active screen buffer.

Console handles returned by [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) and [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) can be used in any of the console functions that require a handle to a console's input buffer or of a console screen buffer. Handles returned by [**GetStdHandle**](getstdhandle.md) can be used by the console functions if they have not been redirected to refer to something other than console I/O. If a standard handle has been redirected to refer to a file or a pipe, however, the handle can only be used by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) functions. [**GetFileType**](https://docs.microsoft.com/windows/win32/api/fileapi/nf-fileapi-getfiletype) can assist in determining what device type the handle refers to. A console handle presents as `FILE_TYPE_CHAR`.

A process can use the [**DuplicateHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724251) function to create a duplicate console handle that has different access or inheritability from the original handle. Note, however, that a process can create a duplicate console handle only for its own use. This differs from other handle types (such as file, pipe, or mutex objects), for which **DuplicateHandle** can create a duplicate that is valid for a different process.
Access to a console must be shared during [creation](creation-of-a-console.md) of the other process or may be requested by the other process through the [**AttachConsole**](attachconsole.md) mechanism.

To close a console handle, a process can use the [**CloseHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724211) function.
