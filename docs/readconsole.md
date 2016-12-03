---
title: ReadConsole function
description: Reads character input from the console input buffer and removes it from the buffer.
MS-HAID:
- '\_win32\_readconsole'
- 'base.readconsole'
- 'consoles.readconsole'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 1aa9ecac-a9b9-4e6d-9206-7a57013de657
keywords: ["ReadConsole function Consoles"]
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

Syntax
------

```ManagedCPlusPlus
BOOL WINAPI ReadConsole(
  _In_     HANDLE  hConsoleInput,
  _Out_    LPVOID  lpBuffer,
  _In_     DWORD   nNumberOfCharsToRead,
  _Out_    LPDWORD lpNumberOfCharsRead,
  _In_opt_ LPVOID  pInputControl
);
```

Parameters
----------

*hConsoleInput* \[in\]  
A handle to the console input buffer. The handle must have the **GENERIC\_READ** access right. For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).

*lpBuffer* \[out\]  
A pointer to a buffer that receives the data read from the console input buffer.

The storage for this buffer is allocated from a shared heap for the process that is 64 KB in size. The maximum size of the buffer will depend on heap usage.

*nNumberOfCharsToRead* \[in\]  
The number of characters to be read. The size of the buffer pointed to by the *lpBuffer* parameter should be at least `nNumberOfCharsToRead * sizeof(TCHAR)` bytes.

*lpNumberOfCharsRead* \[out\]  
A pointer to a variable that receives the number of characters actually read.

*pInputControl* \[in, optional\]  
A pointer to a [**CONSOLE\_READCONSOLE\_CONTROL**](console-readconsole-control.md) structure that specifies a control character to signal the end of the read operation. This parameter can be **NULL**.

This parameter requires Unicode input by default. For ANSI mode, set this parameter to **NULL**.

Return value
------------

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

Remarks
-------

**ReadConsole** reads keyboard input from a console's input buffer. It behaves like the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) function, except that it can read in either Unicode (wide-character) or ANSI mode. To have applications that maintain a single set of sources compatible with both modes, use **ReadConsole** rather than **ReadFile**. Although **ReadConsole** can only be used with a console input buffer handle, **ReadFile** can be used with other handles (such as files or pipes). **ReadConsole** fails if used with a standard handle that has been redirected to be something other than a console handle.

All of the input modes that affect the behavior of [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) have the same effect on **ReadConsole**. To retrieve and set the input modes of a console input buffer, use the [**GetConsoleMode**](getconsolemode.md) and [**SetConsoleMode**](setconsolemode.md) functions.

If the input buffer contains input events other than keyboard events (such as mouse events or window-resizing events), they are discarded. Those events can only be read by using the [**ReadConsoleInput**](readconsoleinput.md) function.

This function uses either Unicode characters or 8-bit characters from the console's current code page. The console's code page defaults initially to the system's OEM code page. To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.

The *pInputControl* parameter can be used to enable intermediate wakeups from the read in response to a file-completion control character specified in a [**CONSOLE\_READCONSOLE\_CONTROL**](console-readconsole-control.md) structure. This feature requires command extensions to be enabled, the standard output handle to be a console output handle, and input to be Unicode.

**Windows Server 2003 and Windows XP/2000:  **The intermediate read feature is not supported.

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
<td><p>Windows 2000 Professional [desktop apps only]</p></td>
</tr>
<tr class="even">
<td><p>Minimum supported server</p></td>
<td><p>Windows 2000 Server [desktop apps only]</p></td>
</tr>
<tr class="odd">
<td><p>Header</p></td>
<td>Wincon.h (include Windows.h)</td>
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
<td><p>Unicode and ANSI names</p></td>
<td><p><strong>ReadConsoleW</strong> (Unicode) and <strong>ReadConsoleA</strong> (ANSI)</p></td>
</tr>
<tr class="odd">
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

[**CONSOLE\_READCONSOLE\_CONTROL**](console-readconsole-control.md)

[**GetConsoleMode**](getconsolemode.md)

[Input and Output Methods](input-and-output-methods.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleMode**](setconsolemode.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**WriteConsole**](writeconsole.md)

 

 




