---
title: CTRL+CLOSE Signal
description: The system generates a CTRL+CLOSE signal when the user closes a console.
author: bitcrazed
ms.author: richturn
ms.topic: article
ms.prod: console
keywords: console, character mode applications, command line applications, terminal applications, console api
---

# CTRL+CLOSE Signal


The system generates a CTRL+CLOSE signal when the user closes a console. All processes attached to the console receive the signal, giving each process an opportunity to clean up before termination. When a process receives this signal, the handler function can take one of the following actions after performing any cleanup operations:

-   Call [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) to terminate the process.
-   Return **FALSE**. If none of the registered handler functions returns **TRUE**, the default handler terminates the process.
-   Return **TRUE**. In this case, no other handler functions are called and the process terminates.

 

 




