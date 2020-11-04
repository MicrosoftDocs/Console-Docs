---
title: GetLargestConsoleWindowSize function
description: Retrieves the size of the largest possible console window, based on the current font and the size of the display.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- consoleapi2/GetLargestConsoleWindowSize
- wincon/GetLargestConsoleWindowSize
- GetLargestConsoleWindowSize
MS-HAID:
- '\_win32\_getlargestconsolewindowsize'
- 'base.getlargestconsolewindowsize'
- 'consoles.getlargestconsolewindowsize'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 3e5897f3-4987-4a82-ab19-06c0b231ba67

topic_type:
- apiref
api_name:
- GetLargestConsoleWindowSize
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
---

# GetLargestConsoleWindowSize function

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Retrieves the size of the largest possible console window, based on the current font and the size of the display.

## Syntax

```C
COORD WINAPI GetLargestConsoleWindowSize(
  _In_ HANDLE hConsoleOutput
);
```

## Parameters

*hConsoleOutput* \[in\]  
A handle to the console screen buffer.

## Return value

If the function succeeds, the return value is a [`COORD`](coord-str.md) structure that specifies the number of character cell columns (`X` member) and rows (`Y` member) in the largest possible console window. Otherwise, the members of the structure are zero.

To get extended error information, call [`GetLastError`](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## Remarks

The function does not take into consideration the size of the console screen buffer, which means that the window size returned may be larger than the size of the console screen buffer. The [`GetConsoleScreenBufferInfo`](getconsolescreenbufferinfo.md) function can be used to determine the maximum size of the console window, given the current screen buffer size, the current font, and the display size.

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows 2000 Professional \[desktop apps only\] |
| Minimum supported server | Windows 2000 Server \[desktop apps only\] |
| Header | ConsoleApi2.h (via WinCon.h, include Windows.h) |
| Library | Kernel32.lib |
| DLL | Kernel32.dll |

## See also

[Console Functions](console-functions.md)

[`COORD`](coord-str.md)

[`GetConsoleScreenBufferInfo`](getconsolescreenbufferinfo.md)

[`SetConsoleWindowInfo`](setconsolewindowinfo.md)

[Window and Screen Buffer Size](window-and-screen-buffer-size.md)
