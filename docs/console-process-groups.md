---
title: Console Process Groups
description: When a process uses the CreateProcess function to create a new console process, it can specify the CREATE\_NEW\_PROCESS\_GROUP flag to make the new process the root process of a console process group.
author: bitcrazed
ms.author: richturn
ms.topic: article
ms.prod: console
keywords: console, character mode applications, command line applications, terminal applications, console api
---

# Console Process Groups


When a process uses the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) function to create a new console process, it can specify the **CREATE\_NEW\_PROCESS\_GROUP** flag to make the new process the root process of a console process group. The process group includes all processes that are descendants of the root process.

A process can use the [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) function to send a CTRL+C or CTRL+BREAK signal to all processes in a console process group. The signal is only received by those processes in the group that are attached to the same console as the process that called **GenerateConsoleCtrlEvent**.

 

 




