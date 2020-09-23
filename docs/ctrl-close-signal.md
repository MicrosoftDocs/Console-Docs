---
title: CTRL+CLOSE Signal
description: The system generates a CTRL+CLOSE signal when the user closes a console.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: console, character mode applications, command line applications, terminal applications, console api
MS-HAID:
- '\_win32\_ctrl\_close\_signal'
- 'base.ctrl\_close\_signal'
- 'consoles.ctrl\_close\_signal'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: a327dd55-3250-40ee-b1c4-6ba3b80984a8
---

# CTRL+CLOSE Signal


The system generates a CTRL+CLOSE signal when the user closes a console. All processes attached to the console receive the signal, giving each process an opportunity to clean up before termination. When a process receives this signal, the handler function can take one of the following actions after performing any cleanup operations:

- Call [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) to terminate the process.
- Return **FALSE**. If none of the registered handler functions returns **TRUE**, the default handler terminates the process.
- Return **TRUE**. In this case, no other handler functions are called and the process terminates.

 

 




