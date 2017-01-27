---
title: GetConsoleHistoryInfo function
description: Retrieves the history settings for the calling process's console.
author: miniksa
ms.author: miniksa
ms.HAID:
- 'base.getconsolehistoryinfo'
- 'consoles.getconsolehistoryinfo'
ms.Attr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 145008b3-8a4a-4e6a-9144-ee787ce90ef4
keywords: ["GetConsoleHistoryInfo function Consoles"]
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


Retrieves the history settings for the calling process's console.

Syntax
------

```ManagedCPlusPlus
BOOL WINAPI GetConsoleHistoryInfo(
  _Out_ PCONSOLE_HISTORY_INFO lpConsoleHistoryInfo
);
```

Parameters
----------

*lpConsoleHistoryInfo* \[out\]  
A pointer to a [**CONSOLE\_HISTORY\_INFO**](console-history-info.md) structure that receives the history settings for the calling process's console.

Return value
------------

If the function succeeds the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

Remarks
-------

If the calling process is not a console process, the function fails and sets the last error to **ERROR\_ACCESS\_DENIED**.

Requirements
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Minimum supported client</p></td>
<td><p>Windows Vista [desktop apps only]</p></td>
</tr>
<tr class="even">
<td><p>Minimum supported server</p></td>
<td><p>Windows Server 2008 [desktop apps only]</p></td>
</tr>
<tr class="odd">
<td><p>Header</p></td>
<td>Wincon.h</td>
</tr>
<tr class="even">
<td><p>Library</p></td>
<td>Kernel32.lib</td>
</tr>
<tr class="odd">
<td><p>DLL</p></td>
<td>Kernel32.dll</td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <span id="see_also"></span>See also


[Console Functions](console-functions.md)

[**CONSOLE\_HISTORY\_INFO**](console-history-info.md)

[**SetConsoleHistoryInfo**](setconsolehistoryinfo.md)

 

 




