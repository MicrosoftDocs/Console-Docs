---
title: GetConsoleWindow function
description: Retrieves the window handle used by the console associated with the calling process.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- consoleapi3/GetConsoleWindow
- wincon/GetConsoleWindow
- GetConsoleWindow
MS-HAID:
- '\_win32\_getconsolewindow'
- 'base.getconsolewindow'
- 'consoles.getconsolewindow'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: a5ab0b37-45ac-4413-b6ff-73876556ad38

topic_type:
- apiref
api_name:
- GetConsoleWindow
api_location:
- Kernel32.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-0.dll
- kernel32legacy.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-1.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-2.dll
- API-MS-Win-DownLevel-Kernel32-l2-1-0.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-3.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-4.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-5.dll
- api-ms-win-core-console-l3-2-0.dll
api_type:
- DllExport
---

# GetConsoleWindow function

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Retrieves the window handle used by the console associated with the calling process.

## Syntax

```C
HWND WINAPI GetConsoleWindow(void);
```

## Parameters

This function has no parameters.

## Return value

The return value is a handle to the window used by the console associated with the calling process or **NULL** if there is no such associated console.

## Remarks

To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later. For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).


[!INCLUDE [no-vt-equiv-local-context](./includes/no-vt-equiv-local-context.md)]

For an application that is hosted inside a [**pseudoconsole**](pseudoconsoles.md) session, this function returns a window handle for message queue purposes only. The associated window is not displayed locally as the _pseudoconsole_ is serializing all actions to a stream for presentation on another terminal window elsewhere.

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows 2000 Professional \[desktop apps only\] |
| Minimum supported server | Windows 2000 Server \[desktop apps only\] |
| Header | ConsoleApi3.h (via WinCon.h, include Windows.h) |
| Library | Kernel32.lib |
| DLL | Kernel32.dll |

</table>

## See also

[Console Functions](console-functions.md)
