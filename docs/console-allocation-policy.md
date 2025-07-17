---
title: Console Allocation Policy
description: Learn more about the Console Allocation Policy, allowing you to create hybrid graphical/console applications.
author: lhecker
ms.author: lhecker
ms.topic: conceptual
keywords: console, character mode applications, command line applications, terminal applications, console api
---

# Console Allocation Policy

> [!NOTE]
> This feature requires Windows 11 24H2 (build 26100) or later.

Most applications on Windows are either of the **IMAGE_SUBSYSTEM_WINDOWS_GUI** or **IMAGE_SUBSYSTEM_WINDOWS_CUI** type.
The former is a typical graphical, windowed application, whereas the latter is what's commonly called a console or terminal application.
When running an application marked as **IMAGE_SUBSYSTEM_WINDOWS_CUI** it'll be allocated a console, unless it's executed inside an existing console session.
Additionally, executing such an application inside a shell like CMD or PowerShell will block until the application has finished executing.
Neither of these are true for **IMAGE_SUBSYSTEM_WINDOWS_GUI** applications.
It'll neither be allocated a console, nor block execution inside a shell.

Now what if you want to write an application that seems like a graphical application when run from Explorer, but you can also write debug output to the console, if run inside an existing console session?
To achieve this, build your application as an **IMAGE_SUBSYSTEM_WINDOWS_CUI** one (for instance with **/SUBSYSTEM:CONSOLE** in MSVC) and add the following application manifest:

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
  <application>
    <windowsSettings>
      <consoleAllocationPolicy xmlns="http://schemas.microsoft.com/SMI/2024/WindowsSettings">detached</consoleAllocationPolicy>
    </windowsSettings>
  </application>
</assembly>
```

The **IMAGE_SUBSYSTEM_WINDOWS_CUI** type informs shells that they need to block until your application has finished executing, while the application manifest informs the operating system to skip allocating a console.

## Requirements

| &nbsp; | &nbsp; |
|-|-|
| Minimum supported client | Windows 11 24H2 (build 26100) \[desktop apps only\] |
| Minimum supported server | Windows Server 2025 (build 26100) |

## See also

[**AllocConsoleWithOptions**](allocconsolewithoptions.md)
