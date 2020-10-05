---
title: Legacy Console Mode – Windows Desktop 
description: Legacy console mode is a compatibility tool to assist with running command-line applications that may not work with the Windows 10 console host
author: miniksa
ms.author: miniksa
ms.topic: conceptual
ms.prod: console
keywords: console, character mode applications, command line applications, terminal applications, console api, compatibility

---

# Legacy Console mode

Legacy Console mode is a compatibility tool designed to help users of older command-line tools on Windows 10. For any command-line tool that is not displaying or operating correctly in the default Windows 10 console experience, this mode provides a coarse-grained solution to stepping the system back to an older version of the console hosting experience.

## Using Legacy Console Mode

To use Legacy Console mode, first open any console hosting window. This is typically done by launching one of the command interpreters [CMD](https://docs.microsoft.com/windows-server/administration/windows-commands/cmd) or [PowerShell](https://docs.microsoft.com/powershell/scripting/install/installing-windows-powershell).

Right-click on the application title bar and choose the `Properties` menu option. Choose the first tab, `Options`. Then check the box at the bottom of the page describing `Use legacy console`. Press the `OK` button to apply.

The setting can be reverted by returning to the same property sheet menu and unchecking the box then pressing `OK`.

> [!NOTE]
>This setting is globally applied to all sessions that start after the preference is changed. Sessions that are already open will not be changed.

## Differences between modes

The Console Host team strives to minimize differences between the Legacy and current modes of the console to ensure that as many customers as possible can run the most up-to-date version. If you experience an issue that requires you to use the legacy console that is not documented here, please contact the team on the [Microsoft/Terminal](https://github.com/microsoft/terminal/) GitHub repository or via the [Feedback Hub](https://docs.microsoft.com/windows-insider/feedback-hub/feedback-hub-app) for assistance.

### 16-bit applications on 32-bit Windows

Some 16-bit applications on 32-bit Windows use a virtual machine technology to operate called [NTVDM](https://docs.microsoft.com/windows/compatibility/ntvdm-and-16-bit-app-support). Often these applications use a graphical screen buffering mode in conjunction with the console hosting environment to operate. Only the legacy console experience supports these graphical buffering modes and the additional console API support required to power these applications. The system will automatically select the legacy console environment when one of these applications is launched.

### IME Embedding

The legacy Console Host embedded the suggestion portion of the IME inside the hosting window by reserving a line at the bottom of the screen for suggestions. The current Console Host environment instead delegates this activity to the IME subsystem to display an overlay window above the console host with suggestions. In an environment where overlay windows are not possible (like with certain remoting tools), the legacy console host may be required.

### API Differences

The major known difference between legacy and current is the implementation of UTF-8. The legacy host has extremely rudimentary and often incorrect support of UTF-8 with [code page 65001](https://docs.microsoft.com/windows/win32/intl/code-pages). The current console host contains incremental improvements release-over-release of Windows 10 to improve this support. Applications that are attempting to rely on predicting "known incorrect" interpretations of UTF-8 from the legacy console will find themselves receiving different answers as support is improved.

Other differences experienced with APIs should be reported to [Microsoft/Terminal](https://github.com/microsoft/terminal/) GitHub repository or via the [Feedback Hub](https://docs.microsoft.com/windows-insider/feedback-hub/feedback-hub-app) for triage and possible remediation.
