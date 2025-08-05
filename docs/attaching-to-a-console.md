---
title: Attaching to a Console
description: A process can use the AttachConsole function to attach to a console. A process can be attached to one console.
author: miniksa
ms.author: miniksa
ms.topic: reference
keywords: console, character mode applications, command line applications, terminal applications, console api
MS-HAID:
- '\_win32\_attaching\_to\_a\_console'
- 'base.attaching\_to\_a\_console'
- 'consoles.attaching\_to\_a\_console'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 348e572f-2448-4384-9822-fab01d4ba255
---

# Attaching to a Console

A process can use the [**AttachConsole**](attachconsole.md) function to attach to a console as a client. A process can be attached to one console.

A console can have many processes attached to it. To retrieve a list of the processes attached to a console, call the [**GetConsoleProcessList**](getconsoleprocesslist.md) function.

To attach as a server, see information about [**Pseudoconsoles**](pseudoconsoles.md).
