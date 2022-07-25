---
title: ReadConsole function
description: Reads character input from the console input buffer and removes it from the buffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- consoleapi/ReadConsole
- wincon/ReadConsole
- ReadConsole
- consoleapi/ReadConsoleA
- wincon/ReadConsoleA
- ReadConsoleA
- consoleapi/ReadConsoleW
- wincon/ReadConsoleW
- ReadConsoleW
MS-HAID:
- '\_win32\_readconsole'
- 'base.readconsole'
- 'consoles.readconsole'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 1aa9ecac-a9b9-4e6d-9206-7a57013de657

topic_type:
- apiref
api_name:
- ReadConsole
- ReadConsoleA
- ReadConsoleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
---

# ReadConsole function

Reads character input from the console input buffer and removes it from the buffer.

## Syntax

```C
BOOL WINAPI ReadConsole(
  _In_     HANDLE  hConsoleInput,
  _Out_    LPVOID  lpBuffer,
  _In_     DWORD   nNumberOfCharsToRead,
  _Out_    LPDWORD lpNumberOfCharsRead,
  _In_opt_ LPVOID  pInputControl
);
```

## Parameters

*hConsoleInput* \[in\]  
A handle to the console input buffer. The handle must have the **GENERIC\_READ** access right. For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).

*lpBuffer* \[out\]  
A pointer to a buffer that receives the data read from the console input buffer.

*nNumberOfCharsToRead* \[in\]  
The number of characters to be read. The size of the buffer pointed to by the *lpBuffer* parameter should be at least `nNumberOfCharsToRead * sizeof(TCHAR)` bytes.

*lpNumberOfCharsRead* \[out\]  
A pointer to a variable that receives the number of characters actually read.

*pInputControl* \[in, optional\]  
A pointer to a [**CONSOLE\_READCONSOLE\_CONTROL**](console-readconsole-control.md) structure that specifies a control character to signal the end of the read operation. This parameter can be **NULL**.

This parameter requires Unicode input by default. For ANSI mode, set this parameter to **NULL**.

## Return value

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## Remarks

**ReadConsole** reads keyboard input from a console's input buffer. It behaves like the [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) function, except that it can read in either Unicode (wide-character) or ANSI mode. To have applications that maintain a single set of sources compatible with both modes, use **ReadConsole** rather than **ReadFile**. Although **ReadConsole** can only be used with a console input buffer handle, **ReadFile** can be used with other handles (such as files or pipes). **ReadConsole** fails if used with a standard handle that has been redirected to be something other than a console handle.

All of the input modes that affect the behavior of [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) have the same effect on **ReadConsole**. To retrieve and set the input modes of a console input buffer, use the [**GetConsoleMode**](getconsolemode.md) and [**SetConsoleMode**](setconsolemode.md) functions.

If the input buffer contains input events other than keyboard events (such as mouse events or window-resizing events), they are discarded. Those events can only be read by using the [**ReadConsoleInput**](readconsoleinput.md) function.

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

The *pInputControl* parameter can be used to enable intermediate wakeups from the read in response to a file-completion control character specified in a [**CONSOLE\_READCONSOLE\_CONTROL**](console-readconsole-control.md) structure. This feature requires command extensions to be enabled, the standard output handle to be a console output handle, and input to be Unicode.

**Windows Server 2003 and Windows XP/2000:** The intermediate read feature is not supported.

**Cooked Mode** is when **ENABLE_LINE_INPUT** is set with [**SetConsoleMode**](setconsolemode.md) on the console input handle. In cooked mode, the console host will provide an edit line on the command-line application's behalf and calls to **ReadFile** or **ReadConsole** will not return until the enter key is pressed.

**Intermediate Read** is an augmentation to that behavior on the **ReadConsole** call in cooked read mode. Setting a flag in [**dwCtrlWakeupMask**](console-readconsole-control.md) on the [**CONSOLE\_READCONSOLE\_CONTROL**](console-readconsole-control.md) structure and pass it into *pinputControl* as it calls **ReadConsole**, will result in the read will not necessarily waiting for a newline, but returning on a specified character as well.

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows 2000 Professional \[desktop apps only\] |
| Minimum supported server | Windows 2000 Server \[desktop apps only\] |
| Header | ConsoleApi.h (via WinCon.h, include Windows.h) |
| Library | Kernel32.lib |
| DLL | Kernel32.dll |
| Unicode and ANSI names | **ReadConsoleW** (Unicode) and **ReadConsoleA** (ANSI) |

## See also

[Console Functions](console-functions.md)

[**CONSOLE\_READCONSOLE\_CONTROL**](console-readconsole-control.md)

[**GetConsoleMode**](getconsolemode.md)

[Input and Output Methods](input-and-output-methods.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleMode**](setconsolemode.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**WriteConsole**](writeconsole.md)
