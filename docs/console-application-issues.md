---
title: Console Application Issues
description: Review console application issues, such as functions that take or return OEM character set strings vs. functions that take or return ANSI character set strings.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
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

The best long-term solution for a console application is to use **[Unicode](/windows/win32/intl/unicode)**. The console will accept UTF-16 encoding on the W variant of the APIs or UTF-8 encoding on the A variant of the APIs after using **[SetConsoleCP](setconsolecp.md)** and **[SetConsoleOutputCP](setconsoleoutputcp.md)** to `65001` (`CP_UTF8` constant) for the UTF-8 code page.

Barring that solution, a console application should use the [SetFileApisToOEM](/windows/win32/api/fileapi/nf-fileapi-setfileapistooem) function. That function changes relevant file functions so that they produce OEM character set strings rather than ANSI character set strings.

The following are file functions:

:::row:::
    :::column:::
        [CopyFile](/windows/win32/api/winbase/nf-winbase-copyfile)  
        [CreateDirectory](/windows/win32/api/fileapi/nf-fileapi-createdirectorya)  
        [CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilea)  
        [CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa)  
        [DeleteFile](/windows/win32/api/fileapi/nf-fileapi-deletefilea)  
        [FindFirstFile](/windows/win32/api/fileapi/nf-fileapi-findfirstfilea)  
        [FindNextFile](/windows/win32/api/fileapi/nf-fileapi-findnextfilea)  
        [GetCurrentDirectory](/windows/win32/api/winbase/nf-winbase-getcurrentdirectory)  
        [GetDiskFreeSpace](/windows/win32/api/fileapi/nf-fileapi-getdiskfreespacea)  
        [GetDriveType](/windows/win32/api/fileapi/nf-fileapi-getdrivetypea)  
    :::column-end:::
    :::column:::
        [GetFileAttributes](/windows/win32/api/fileapi/nf-fileapi-getfileattributesa)  
        [GetFullPathName](/windows/win32/api/fileapi/nf-fileapi-getfullpathnamea)  
        [GetModuleFileName](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamea)  
        [GetModuleHandle](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulehandlea)  
        [GetSystemDirectory](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getsystemdirectorya)  
        [GetTempFileName](/windows/win32/api/fileapi/nf-fileapi-gettempfilenamea)  
        [GetTempPath](/windows/win32/api/fileapi/nf-fileapi-gettemppatha)  
        [GetVolumeInformation](/windows/win32/api/fileapi/nf-fileapi-getvolumeinformationa)  
        [GetWindowsDirectory](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getwindowsdirectorya)  
        [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibrarya)  
    :::column-end:::
    :::column:::
        [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexa)  
        [MoveFile](/windows/win32/api/winbase/nf-winbase-movefile)  
        [MoveFileEx](/windows/win32/api/winbase/nf-winbase-movefileexa)  
        [OpenFile](/windows/win32/api/winbase/nf-winbase-openfile)  
        [RemoveDirectory](/windows/win32/api/fileapi/nf-fileapi-removedirectorya)  
        [SearchPath](/windows/win32/api/processenv/nf-processenv-searchpatha)  
        [SetCurrentDirectory](/windows/win32/api/winbase/nf-winbase-setcurrentdirectory)  
        [SetFileAttributes](/windows/win32/api/fileapi/nf-fileapi-setfileattributesa)  
    :::column-end:::
:::row-end:::

When dealing with command lines, a console application should obtain the command line in Unicode form and convert it to OEM form, using the relevant character-to-OEM functions. Note, also, that *argv* uses the ANSI character set.