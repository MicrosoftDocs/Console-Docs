---
title: GetNumberOfConsoleMouseButtons function
description: Retrieves the number of buttons on the mouse used by the current console.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- consoleapi3/GetNumberOfConsoleMouseButtons
- wincon/GetNumberOfConsoleMouseButtons
- GetNumberOfConsoleMouseButtons
MS-HAID:
- '\_win32\_getnumberofconsolemousebuttons'
- 'base.getnumberofconsolemousebuttons'
- 'consoles.getnumberofconsolemousebuttons'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 78a6a3be-b42f-4a7a-a612-b6a2019cfec2

topic_type:
- apiref
api_name:
- GetNumberOfConsoleMouseButtons
api_location:
- Kernel32.dll
api_type:
- DllExport
---

# GetNumberOfConsoleMouseButtons function

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Retrieves the number of buttons on the mouse used by the current console.

## Syntax

```C
BOOL WINAPI GetNumberOfConsoleMouseButtons(
  _Out_ LPDWORD lpNumberOfMouseButtons
);
```

## Parameters

*lpNumberOfMouseButtons* \[out\]  
A pointer to a variable that receives the number of mouse buttons.

## Return value

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## Remarks

When a console receives mouse input, an [**INPUT\_RECORD**](input-record-str.md) structure containing a [**MOUSE\_EVENT\_RECORD**](mouse-event-record-str.md) structure is placed in the console's input buffer. The **dwButtonState** member of **MOUSE\_EVENT\_RECORD** has a bit indicating the state of each mouse button. The bit is 1 if the button is down and 0 if the button is up. To determine the number of bits that are significant, use **GetNumberOfConsoleMouseButtons**.

> [!TIP]
> This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent. This decision intentionally aligns the Windows platform with other operating systems. This state is only relevant to the local user, session, and privilege context. Applications remoting via cross-platform utilities and transports like SSH may not work as expected if using this API.

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows 2000 Professional \[desktop apps only\] |
| Minimum supported server | Windows 2000 Server \[desktop apps only\] |
| Header | ConsoleApi3.h (via WinCon.h, include Windows.h) |
| Library | Kernel32.lib |
| DLL | Kernel32.dll |

## See also

[Console Functions](console-functions.md)

[Console Input Buffer](console-input-buffer.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**INPUT\_RECORD**](input-record-str.md)

[**MOUSE\_EVENT\_RECORD**](mouse-event-record-str.md)