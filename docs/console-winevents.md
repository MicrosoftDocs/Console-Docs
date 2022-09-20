---
title: Console WinEvents
description: The following event constants are used in the event parameter of the WinEventProc callback function. For more information, see WinEvents.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
f1_keywords:
- winuser/EVENT_CONSOLE_CARET
- winuser/EVENT_CONSOLE_END_APPLICATION
- winuser/EVENT_CONSOLE_LAYOUT
- winuser/EVENT_CONSOLE_START_APPLICATION
- winuser/EVENT_CONSOLE_UPDATE_REGION
- winuser/EVENT_CONSOLE_UPDATE_SCROLL
- winuser/EVENT_CONSOLE_UPDATE_SIMPLE
- EVENT_CONSOLE_CARET
- EVENT_CONSOLE_END_APPLICATION
- EVENT_CONSOLE_LAYOUT
- EVENT_CONSOLE_START_APPLICATION
- EVENT_CONSOLE_UPDATE_REGION
- EVENT_CONSOLE_UPDATE_SCROLL
- EVENT_CONSOLE_UPDATE_SIMPLE
MS-HAID:
- '\_win32\_console\_winevents'
- 'base.console\_winevents'
- 'consoles.console\_winevents'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: b7078b2d-5508-4e42-bac2-34b70f1856e2
topic_type:
- apiref
api_name:
- EVENT_CONSOLE_CARET
- EVENT_CONSOLE_END_APPLICATION
- EVENT_CONSOLE_LAYOUT
- EVENT_CONSOLE_START_APPLICATION
- EVENT_CONSOLE_UPDATE_REGION
- EVENT_CONSOLE_UPDATE_SCROLL
- EVENT_CONSOLE_UPDATE_SIMPLE
api_location:
- Winuser.h
api_type:
- HeaderDef
---

# Console WinEvents

> [!IMPORTANT]
> WinEvents are part of the legacy **[Microsoft Active Accessibility](/windows/win32/winauto/microsoft-active-accessibility)** framework. Development using these events is strongly discouraged in favor of the **[Microsoft UI Automation](/windows/win32/winauto/entry-uiauto-win32)** framework which provides a more robust and comprehensive suite of interfaces for accessibility and automation applications to interact with the console. 

> [!WARNING]
> Registering for these events is a global activity and will significantly impact performance of all command-line applications running on a system at the same time, including services and background utilities. The **Microsoft UI Automation** framework is console session specific and overcomes this limitation.

The following event constants are used in the *event* parameter of the [*WinEventProc*](/windows/win32/api/winuser/nc-winuser-wineventproc) callback function. For more information, see [WinEvents](/windows/win32/winauto/winevents-infrastructure).

| Constant/value | Description |
|-|-|
| **EVENT_CONSOLE_CARET** 0x4001 | The console caret has moved. The *idObject* parameter is one or more of the following values: **CONSOLE_CARET_SELECTION** or **CONSOLE_CARET_VISIBLE**. The *idChild* parameter is a **[COORD](coord-str.md)** structure that specifies the cursor's current position. |
| **EVENT_CONSOLE_END_APPLICATION** 0x4007 | A console process has exited. The *idObject* parameter contains the process identifier of the terminated process. |
| **EVENT_CONSOLE_LAYOUT** 0x4005 | The console layout has changed. |
| **EVENT_CONSOLE_START_APPLICATION** 0x4006 | A new console process has started. The *idObject* parameter contains the process identifier of the newly created process. If the application is a 16-bit application, the *idChild* parameter is **CONSOLE_APPLICATION_16BIT** and *idObject* is the process identifier of the NTVDM session associated with the console. |
|**EVENT_CONSOLE_UPDATE_REGION** 0x4002 | More than one character has changed. The  *idObject* parameter is a **[COORD](coord-str.md)** structure that specifies the start of the changed region. The *idChild* parameter is a **COORD** structure that specifies the end of the changed region. |
|**EVENT_CONSOLE_UPDATE_SCROLL** 0x4004 | The console has scrolled. The *idObject* parameter is the horizontal distance the console has scrolled. The *idChild* parameter is the vertical distance the console has scrolled. |
|**EVENT_CONSOLE_UPDATE_SIMPLE** 0x4003 | A single character has changed. The *idObject* parameter is a **[COORD](coord-str.md)** structure that specifies the character that has changed. The *idChild* parameter specifies the character in the low word and the **[character attributes](console-screen-buffers.md#character-attributes)** in the high word. |

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows 2000 Professional \[desktop apps only\] |
| Minimum supported server | Windows 2000 Server \[desktop apps only\] |
| Header | Winuser.h |
