---
title: GetConsoleFontSize function
description: Retrieves the size of the font used by the specified console screen buffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- consoleapi3/GetConsoleFontSize
- wincon/GetConsoleFontSize
- GetConsoleFontSize
MS-HAID:
- '\_win32\_getconsolefontsize'
- 'base.getconsolefontsize'
- 'consoles.getconsolefontsize'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 51b1f58d-b3fb-4e09-8398-671b3959bb01

topic_type:
- apiref
api_name:
- GetConsoleFontSize
api_location:
- Kernel32.dll
api_type:
- DllExport
---

# GetConsoleFontSize function

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Retrieves the size of the font used by the specified console screen buffer.

## Syntax

```C
COORD WINAPI GetConsoleFontSize(
  _In_ HANDLE hConsoleOutput,
  _In_ DWORD  nFont
);
```

## Parameters

*hConsoleOutput* \[in\]  
A handle to the console screen buffer. The handle must have the `GENERIC\_READ` access right. For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).

*nFont* \[in\]  
The index of the font whose size is to be retrieved. This index is obtained by calling the [`GetCurrentConsoleFont`](getcurrentconsolefont.md) function.

## Return value

If the function succeeds, the return value is a [`COORD`](coord-str.md) structure that contains the width and height of each character in the font, in logical units. The `X` member contains the width, while the `Y` member contains the height.

If the function fails, the width and the height are zero. To get extended error information, call [`GetLastError`](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## Remarks

To compile an application that uses this function, define `\_WIN32\_WINNT` as 0x0500 or later. For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows XP \[desktop apps only\] |
| Minimum supported server | Windows Server 2003 \[desktop apps only\] |
| Header | ConsoleApi3.h (via WinCon.h, include Windows.h) |
| Library | Kernel32.lib |
| DLL | Kernel32.dll |

## See also

[Console Functions](console-functions.md)

[Console Screen Buffers](console-screen-buffers.md)

[`COORD`](coord-str.md)

[`GetCurrentConsoleFont`](getcurrentconsolefont.md)
