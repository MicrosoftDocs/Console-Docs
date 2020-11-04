---
title: SetConsoleActiveScreenBuffer function
description: Sets the specified screen buffer to be the currently displayed console screen buffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- consoleapi2/SetConsoleActiveScreenBuffer
- wincon/SetConsoleActiveScreenBuffer
- SetConsoleActiveScreenBuffer
MS-HAID:
- '\_win32\_setconsoleactivescreenbuffer'
- 'base.setconsoleactivescreenbuffer'
- 'consoles.setconsoleactivescreenbuffer'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: c026cb94-c8ec-44ee-b432-3870ae3006c2

topic_type:
- apiref
api_name:
- SetConsoleActiveScreenBuffer
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
---

# SetConsoleActiveScreenBuffer function

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Sets the specified screen buffer to be the currently displayed console screen buffer.

## Syntax

```C
BOOL WINAPI SetConsoleActiveScreenBuffer(
  _In_ HANDLE hConsoleOutput
);
```

## Parameters

*hConsoleOutput* \[in\]  
A handle to the console screen buffer.

## Return value

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [`GetLastError`](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## Remarks

A console can have multiple screen buffers. `SetConsoleActiveScreenBuffer` determines which one is displayed. You can write to an inactive screen buffer and then use `SetConsoleActiveScreenBuffer` to display the buffer's contents.

[!INCLUDE [no-vt-equiv-alt-buf](./includes/no-vt-equiv-alt-buf.md)]

## Examples

For an example, see [Reading and Writing Blocks of Characters and Attributes](reading-and-writing-blocks-of-characters-and-attributes.md).

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

[Console Screen Buffers](console-screen-buffers.md)

[`CreateConsoleScreenBuffer`](createconsolescreenbuffer.md)
