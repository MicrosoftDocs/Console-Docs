---
title: SetConsoleTitle function
description: See reference information about the SetConsoleTitle function, which sets the title for the current console window.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- consoleapi2/SetConsoleTitle
- wincon/SetConsoleTitle
- SetConsoleTitle
- consoleapi2/SetConsoleTitleA
- wincon/SetConsoleTitleA
- SetConsoleTitleA
- consoleapi2/SetConsoleTitleW
- wincon/SetConsoleTitleW
- SetConsoleTitleW
MS-HAID:
- '\_win32\_setconsoletitle'
- 'base.setconsoletitle'
- 'consoles.setconsoletitle'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: f1db449b-0dd0-4d61-bb79-b7da9a5168f4

topic_type:
- apiref
api_name:
- SetConsoleTitle
- SetConsoleTitleA
- SetConsoleTitleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-0.dll
- kernel32legacy.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-1.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-2.dll
- API-MS-Win-DownLevel-Kernel32-l2-1-0.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-3.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-4.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-5.dll
api_type:
- DllExport
---

# SetConsoleTitle function

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Sets the title for the current console window.

## Syntax

```C
BOOL WINAPI SetConsoleTitle(
  _In_ LPCTSTR lpConsoleTitle
);
```

## Parameters

*lpConsoleTitle* \[in\]  
The string to be displayed in the title bar of the console window. The total size must be less than 64K.

## Return value

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## Remarks

When the process terminates, the system restores the original console title.

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[window title](console-virtual-terminal-sequences.md#window-title)** sequences. _Virtual terminal sequences_ are recommended for all new and ongoing development.

## Examples

The following example shows how to retrieve and modify the console title.

```C
#include <windows.h>
#include <tchar.h>
#include <conio.h>
#include <strsafe.h>

int main( void )
{
   TCHAR szOldTitle[MAX_PATH];
   TCHAR szNewTitle[MAX_PATH];

   // Save current console title.

   if( GetConsoleTitle(szOldTitle, MAX_PATH) )
   {
      // Build new console title string.

      StringCchPrintf(szNewTitle, MAX_PATH, TEXT("TEST: %s"), szOldTitle);

      // Set console title to new title
      if( !SetConsoleTitle(szNewTitle) )
      {
         _tprintf(TEXT("SetConsoleTitle failed (%d)\n"), GetLastError());
         return 1;
      }
      else
      {
         _tprintf(TEXT("SetConsoleTitle succeeded.\n"));
      }
   }
   return 0;
}
```

## Requirements

| | |
|-|-|
| Minimum supported client | Windows 2000 Professional \[desktop apps only\] |
| Minimum supported server | Windows 2000 Server \[desktop apps only\] |
| Header | ConsoleApi2.h (via WinCon.h, include Windows.h) |
| Library | Kernel32.lib |
| DLL | Kernel32.dll |
| Unicode and ANSI names | **SetConsoleTitleW** (Unicode) and **SetConsoleTitleA** (ANSI) |

## See also

[Console Functions](console-functions.md)

[**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md)

[**GetConsoleTitle**](getconsoletitle.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)
