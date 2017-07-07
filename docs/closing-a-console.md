---
title: Closing a Console
description: A process can use the FreeConsole function to detach itself from its console.
author: bitcrazed
ms.author: richturn
ms.topic: article
ms.prod: console
keywords: console, character mode applications, command line applications, terminal applications, console api
---

# Closing a Console


A process can use the [**FreeConsole**](freeconsole.md) function to detach itself from its console. If other processes share the console, the console is not destroyed, but the process that called **FreeConsole** cannot refer to it. After calling **FreeConsole**, the process can use [**AllocConsole**](allocconsole.md) to create a new console or [**AttachConsole**](attachconsole.md) to attach to another console.

A console is closed when the last process attached to it terminates or calls [**FreeConsole**](freeconsole.md).

 

 




