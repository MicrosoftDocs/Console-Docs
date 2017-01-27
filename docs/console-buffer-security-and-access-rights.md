---
title: Console Buffer Security and Access Rights
description: The Windows security model enables you to control access to console input buffers and console screen buffers. For more information about security, see Access-Control Model.
author: miniksa
ms.author: miniksa
ms.assetid: f9a50063-8fc8-4cd1-8f24-9ae3946d3119
keywords: ["consoles", "consoles, security and access rights"]
---

# Console Buffer Security and Access Rights


The Windows security model enables you to control access to console input buffers and console screen buffers. For more information about security, see [Access-Control Model](https://msdn.microsoft.com/library/windows/desktop/aa374876).

You can specify a [security descriptor](https://msdn.microsoft.com/library/windows/desktop/aa379563) for the console input and console screen buffers when you call the [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) or [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) function. If you specify **NULL**, the object gets a default security descriptor. The ACLs in the default security descriptor for a console buffer come from the primary or impersonation token of the creator.

The handles returned by [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858), [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md), and [**GetStdHandle**](getstdhandle.md) have the **GENERIC\_READ** and **GENERIC\_WRITE** access rights.

The valid access rights include the **GENERIC\_READ** and **GENERIC\_WRITE**[generic access rights](https://msdn.microsoft.com/library/windows/desktop/aa446632).

| Value                            | Meaning                                                                                               |
|----------------------------------|-------------------------------------------------------------------------------------------------------|
| **GENERIC\_READ** (0x80000000L)  | Requests read access to the console screen buffer, enabling the process to read data from the buffer. |
| **GENERIC\_WRITE** (0x40000000L) | Requests write access to the console screen buffer, enabling the process to write data to the buffer. |

 

 

 




