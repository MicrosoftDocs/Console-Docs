---
title: Console Process Groups
description: When a process uses the CreateProcess function to create a new console process, it can specify the CREATE\_NEW\_PROCESS\_GROUP flag to make the new process the root process of a console process group.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
MS-HAID:
- '\_win32\_console\_process\_groups'
- 'base.console\_process\_groups'
- 'consoles.console\_process\_groups'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 6cfe5b4b-d677-4747-bbf2-c7243db2346e
---

# Console Process Groups


When a process uses the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) function to create a new console process, it can specify the **CREATE\_NEW\_PROCESS\_GROUP** flag to make the new process the root process of a console process group. The process group includes all processes that are descendants of the root process.

A process can use the [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) function to send a CTRL+C or CTRL+BREAK signal to all processes in a console process group. The signal is only received by those processes in the group that are attached to the same console as the process that called **GenerateConsoleCtrlEvent**.

 

 




