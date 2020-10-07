---
title: SetConsoleHistoryInfo function
description: Sets the history settings for the Windows Console of the calling process.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- consoleapi3/SetConsoleHistoryInfo
- wincon/SetConsoleHistoryInfo
- SetConsoleHistoryInfo
MS-HAID:
- 'base.setconsolehistoryinfo'
- 'consoles.setconsolehistoryinfo'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: db180f53-aa3c-4a91-bc3e-9f3f0bb7ab01

topic_type:
- apiref
api_name:
- SetConsoleHistoryInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
---

# SetConsoleHistoryInfo function

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Sets the history settings for the calling process's console.

## Syntax

```C
BOOL WINAPI SetConsoleHistoryInfo(
  _In_ PCONSOLE_HISTORY_INFO lpConsoleHistoryInfo
);
```

## Parameters

*lpConsoleHistoryInfo* \[in\]  
A pointer to a [**CONSOLE\_HISTORY\_INFO**](console-history-info.md) structure that contains the history settings for the process's console.

## Return value

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## Remarks

If the calling process is not a console process, the function fails and sets the last error code to **ERROR\_ACCESS\_DENIED**.

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

[**GetConsoleHistoryInfo**](getconsolehistoryinfo.md)
