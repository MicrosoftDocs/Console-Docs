---
title: Closing a Console
description: A process can use the FreeConsole function to detach itself from its console.
author: miniksa
ms.author: miniksa
ms.topic: reference
keywords: console, character mode applications, command line applications, terminal applications, console api
MS-HAID:
- '\_win32\_closing\_a\_console'
- 'base.closing\_a\_console'
- 'consoles.closing\_a\_console'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 254b7cfc-4dee-452f-a409-4fc90d20d4c1
---

# Closing a Console

A process can use the [**FreeConsole**](freeconsole.md) function to detach itself from its console. If other processes share the console, the console is not destroyed, but the process that called **FreeConsole** cannot refer to it. After calling **FreeConsole**, the process can use [**AllocConsole**](allocconsole.md) to create a new console or [**AttachConsole**](attachconsole.md) to attach to another console.

A console is closed when the last process attached to it terminates or calls [**FreeConsole**](freeconsole.md).
