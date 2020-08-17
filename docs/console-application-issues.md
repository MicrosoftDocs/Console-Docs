---
title: Console Application Issues
description: Review console application issues, such as functions that take or return OEM character set strings vs. functions that take or return ANSI character set strings.
author: bitcrazed
ms.author: richturn
ms.topic: article
keywords: console, character mode applications, command line applications, terminal applications, console api
MS-HAID:
- '\_win32\_console\_application\_issues'
- 'base.console\_application\_issues'
- 'consoles.console\_application\_issues'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: a561fbdd-b50d-4687-92d7-735377a7991d
---

# Console Application Issues

The 8-bit console functions use the OEM code page. All other functions use the ANSI code page by default. This means that strings returned by the console functions may not be processed correctly by the other functions and vice versa. For example, if **FindFirstFileA** returns a string that contains certain extended ANSI characters, **WriteConsoleA** will not display the string properly.

The best long-term solution for a console application is to use Unicode. Barring that solution, a console application should use the [SetFileApisToOEM](https://msdn.microsoft.com/library/windows/desktop/aa365534) function. That function changes relevant file functions so that they produce OEM character set strings rather than ANSI character set strings.

The following are file functions:

:::row:::
    :::column:::
        [CopyFile](https://msdn.microsoft.com/library/windows/desktop/aa363851)  
        [CreateDirectory](https://msdn.microsoft.com/library/windows/desktop/aa363855)  
        [CreateFile](https://msdn.microsoft.com/library/windows/desktop/aa363858)  
        [CreateProcess](https://msdn.microsoft.com/library/windows/desktop/ms682425)  
        [DeleteFile](https://msdn.microsoft.com/library/windows/desktop/aa363915)  
        [FindFirstFile](https://msdn.microsoft.com/library/windows/desktop/aa364418)  
        [FindNextFile](https://msdn.microsoft.com/library/windows/desktop/aa364428)  
        [GetCurrentDirectory](https://msdn.microsoft.com/library/windows/desktop/aa364934)  
        [GetDiskFreeSpace](https://msdn.microsoft.com/library/windows/desktop/aa364935)  
        [GetDriveType](https://msdn.microsoft.com/library/windows/desktop/aa364939)  
    :::column-end:::
    :::column:::
        [GetFileAttributes](https://msdn.microsoft.com/library/windows/desktop/aa364944)  
        [GetFullPathName](https://msdn.microsoft.com/library/windows/desktop/aa364963)  
        [GetModuleFileName](https://msdn.microsoft.com/library/windows/desktop/ms683197)  
        [GetModuleHandle](https://msdn.microsoft.com/library/windows/desktop/ms683199)  
        [GetSystemDirectory](https://msdn.microsoft.com/library/windows/desktop/ms724373)  
        [GetTempFileName](https://msdn.microsoft.com/library/windows/desktop/aa364991)  
        [GetTempPath](https://msdn.microsoft.com/library/windows/desktop/aa364992)  
        [GetVolumeInformation](https://msdn.microsoft.com/library/windows/desktop/aa364993)  
        [GetWindowsDirectory](https://msdn.microsoft.com/library/windows/desktop/ms724454)  
        [LoadLibrary](https://msdn.microsoft.com/library/windows/desktop/ms684175)  
    :::column-end:::
    :::column:::
        [LoadLibraryEx](https://msdn.microsoft.com/library/windows/desktop/ms684179)  
        [MoveFile](https://msdn.microsoft.com/library/windows/desktop/aa365239)  
        [MoveFileEx](https://msdn.microsoft.com/library/windows/desktop/aa365240)  
        [OpenFile](https://msdn.microsoft.com/library/windows/desktop/aa365430)  
        [RemoveDirectory](https://msdn.microsoft.com/library/windows/desktop/aa365488)  
        [SearchPath](https://msdn.microsoft.com/library/windows/desktop/aa365527)  
        [SetCurrentDirectory](https://msdn.microsoft.com/library/windows/desktop/aa365530)  
        [SetFileAttributes](https://msdn.microsoft.com/library/windows/desktop/aa365535)  
    :::column-end:::
:::row-end:::

When dealing with command lines, a console application should obtain the command line in Unicode form and convert it to OEM form, using the relevant character-to-OEM functions. Note, also, that *argv* uses the ANSI character set.
