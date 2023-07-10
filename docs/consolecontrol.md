---
title: ConsoleControl function
description: Performs special control operations for console.
author: zadjii-msft
ms.author: migrie
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- consoleapi/ConsoleControl
- wincon/ConsoleControl
- ConsoleControl
MS-HAID:
- '\_win32\_consolecontrol'
- 'base.consolecontrol'
- 'consoles.consolecontrol'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 5a9f7b18-cdea-4041-a377-5532d30e0105

topic_type:
- apiref
api_name:
- ConsoleControl
api_location:
- User32.dll
api_type:
- DllExport
---

# ConsoleControl function

Performs special kernel operations for console host applications. This includes: reparenting the console window, allowing the console to give launched applications foreground rights, and terminating attached processes. 

<div class="alert"><b>Note</b> This function has no associated import library. This function is available as the resources named <b>ConsoleControl</b> in User32.dll. You must use the <a href="/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibrarya">LoadLibrary</a> and <a href="/windows/desktop/api/libloaderapi/nf-libloaderapi-getprocaddress">GetProcAddress</a> functions to dynamically link to User32.dll.</div><div> </div>

## Syntax

```C

typedef enum _CONSOLECONTROL
{
    Reserved1,
    ConsoleNotifyConsoleApplication,
    Reserved2,
    ConsoleSetCaretInfo,
    Reserved3,
    ConsoleSetForeground,
    ConsoleSetWindowOwner,
    ConsoleEndTask,
} CONSOLECONTROL;

typedef struct _CONSOLEENDTASK
{
    HANDLE ProcessId;
    HWND hwnd;
    ULONG ConsoleEventCode;
    ULONG ConsoleFlags;
} CONSOLEENDTASK, *PCONSOLEENDTASK;

typedef struct _CONSOLEWINDOWOWNER
{
    HWND hwnd;
    ULONG ProcessId;
    ULONG ThreadId;
} CONSOLEWINDOWOWNER, *PCONSOLEWINDOWOWNER;

typedef struct _CONSOLESETFOREGROUND
{
    HANDLE hProcess;
    BOOL bForeground;
} CONSOLESETFOREGROUND, *PCONSOLESETFOREGROUND;


NTSTATUS ConsoleControl(
  _In_ CONSOLECONTROL Command,
  _In_reads_bytes_(ConsoleInformationLength) PVOID ConsoleInformation,
  _In_ DWORD ConsoleInformationLength
);
```

## Parameters

*Command* \[in\]  
One of the `CONSOLECONTROL` values indicating which console control function should be executed. 

*ConsoleInformation* \[in\]  
A pointer to one of the `CONSOLEENDTASK`, `CONSOLEWINDOWOWNER`, or `CONSOLESETFOREGROUND` structures specifying additional data for the requested console control function. 

*ConsoleInformationLength* \[in\]  
The size of the structure pointed to by the *ConsoleInformation* parameter.

## Return value

If the function succeeds, the return value is `STATUS_SUCCESS`.

If the function fails, the return value is an `NTSTATUS` indicating the reason for the failure. 

## Remarks

This function is not defined in an SDK header and must be declared by the caller. This function is exported from user32.dll

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows 7 \[desktop apps only\] |
| Minimum supported server | Windows Server 2003 \[desktop apps only\] |
| Header | none, see remarks |
| Library | none, see remarks |
| DLL | User32.dll |

