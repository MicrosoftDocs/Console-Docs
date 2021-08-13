---
title: GetConsoleHistoryInfo function
description: See reference information about the GetConsoleHistoryInfo function, which retrieves the history settings for the console of the calling process.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- consoleapi3/GetConsoleHistoryInfo
- wincon/GetConsoleHistoryInfo
- GetConsoleHistoryInfo
MS-HAID:
- 'base.getconsolehistoryinfo'
- 'consoles.getconsolehistoryinfo'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 145008b3-8a4a-4e6a-9144-ee787ce90ef4

topic_type:
- apiref
api_name:
- GetConsoleHistoryInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
---

# GetConsoleHistoryInfo function

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Retrieves the history settings for the calling process's console.

## Syntax

```C
BOOL WINAPI GetConsoleHistoryInfo(
  _Out_ PCONSOLE_HISTORY_INFO lpConsoleHistoryInfo
);
```

## Parameters

*lpConsoleHistoryInfo* \[out\]  
A pointer to a [**CONSOLE\_HISTORY\_INFO**](console-history-info.md) structure that receives the history settings for the calling process's console.

## Return value

If the function succeeds the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## Remarks

If the calling process is not a console process, the function fails and sets the last error to **ERROR\_ACCESS\_DENIED**.

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows Vista \[desktop apps only\] |
| Minimum supported server | Windows Server 2008 \[desktop apps only\] |
| Header | ConsoleApi3.h (via WinCon.h, include Windows.h) |
| Library | Kernel32.lib |
| DLL | Kernel32.dll |

## See also

[Console Functions](console-functions.md)

[**CONSOLE\_HISTORY\_INFO**](console-history-info.md)

[**SetConsoleHistoryInfo**](setconsolehistoryinfo.md)