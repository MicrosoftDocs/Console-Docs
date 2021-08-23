---
title: Registering a Control Handler Function
description: This is an example of the SetConsoleCtrlHandler function that is used to install a control handler.
author: miniksa
ms.author: miniksa
ms.topic: sample
keywords: console, character mode applications, command line applications, terminal applications, console api
MS-HAID:
- '\_win32\_registering\_a\_control\_handler\_function'
- 'base.registering\_a\_control\_handler\_function'
- 'consoles.registering\_a\_control\_handler\_function'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: f1c72277-f06c-4147-a74c-6aaf6feb730e
---

# Registering a Control Handler Function

## Basic Control Handler Example

This is an example of the [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) function that is used to install a control handler.

When a CTRL+C signal is received, the control handler returns **TRUE**, indicating that it has handled the signal. Doing this prevents other control handlers from being called.

When a **CTRL\_CLOSE\_EVENT** signal is received, the control handler returns **TRUE** and the process terminates.

When a **CTRL\_BREAK\_EVENT**, **CTRL\_LOGOFF\_EVENT**, or **CTRL\_SHUTDOWN\_EVENT** signal is received, the control handler returns **FALSE**. Doing this causes the signal to be passed to the next control handler function. If no other control handlers have been registered or none of the registered handlers returns **TRUE**, the default handler will be used, resulting in the process being terminated.

> [!NOTE]
> Calling [**AttachConsole**](attachconsole.md), [**AllocConsole**](allocconsole.md), or [**FreeConsole**](freeconsole.md) will reset the table of control handlers in the client process to its initial state. Handlers must be registered again when the attached console session changes.

```C
// CtrlHandler.cpp : This file contains the 'main' function. Program execution begins and ends there.
//

#include <windows.h>
#include <stdio.h>

BOOL WINAPI CtrlHandler(DWORD fdwCtrlType)
{
    switch (fdwCtrlType)
    {
        // Handle the CTRL-C signal.
    case CTRL_C_EVENT:
        printf("Ctrl-C event\n\n");
        Beep(750, 300);
        return TRUE;

        // CTRL-CLOSE: confirm that the user wants to exit.
    case CTRL_CLOSE_EVENT:
        Beep(600, 200);
        printf("Ctrl-Close event\n\n");
        return TRUE;

        // Pass other signals to the next handler.
    case CTRL_BREAK_EVENT:
        Beep(900, 200);
        printf("Ctrl-Break event\n\n");
        return FALSE;

    case CTRL_LOGOFF_EVENT:
        Beep(1000, 200);
        printf("Ctrl-Logoff event\n\n");
        return FALSE;

    case CTRL_SHUTDOWN_EVENT:
        Beep(750, 500);
        printf("Ctrl-Shutdown event\n\n");
        return FALSE;

    default:
        return FALSE;
    }
}

int main(void)
{
    if (SetConsoleCtrlHandler(CtrlHandler, TRUE))
    {
        printf("\nThe Control Handler is installed.\n");
        printf("\n -- Now try pressing Ctrl+C or Ctrl+Break, or");
        printf("\n    try logging off or closing the console...\n");
        printf("\n(...waiting in a loop for events...)\n\n");

        while (1) {}
    }
    else
    {
        printf("\nERROR: Could not set control handler");
        return 1;
    }
    return 0;
}
```

## Listen with Hidden Window Example

Per the remarks, if the gdi32.dll or user32.dll library are loaded,  **SetConsoleCtrlHandler** does not get called for the **CTRL\_LOGOFF\_EVENT** and **CTRL\_SHUTDOWN\_EVENT** events. The workaround specified is to create a hidden window, if no window already exists, by calling the [**CreateWindowEx**](/windows/win32/api/winuser/nf-winuser-createwindowexa) method with the *dwExStyle* parameter set to 0 and listen for the  [**WM\_QUERYENDSESSION**](/windows/win32/shutdown/wm-queryendsession) and [**WM\_ENDSESSION**](/windows/win32/shutdown/wm-endsession) window messages. If a window already exists, add the two messages to the existing [Window Procedure](/windows/win32/winmsg/using-window-procedures).

More information on setting up a window and its messaging loop can be found at [Creating a Window](/windows/win32/learnwin32/creating-a-window).

```C++
// CtrlHandler.cpp : This file contains the 'main' function. Program execution begins and ends there.
//

#include <Windows.h>
#include <stdio.h>

BOOL WINAPI CtrlHandler(DWORD fdwCtrlType)
{
    switch (fdwCtrlType)
    {
        // Handle the CTRL-C signal.
    case CTRL_C_EVENT:
        printf("Ctrl-C event\n\n");
        Beep(750, 300);
        return TRUE;

        // CTRL-CLOSE: confirm that the user wants to exit.
    case CTRL_CLOSE_EVENT:
        Beep(600, 200);
        printf("Ctrl-Close event\n\n");
        return TRUE;

        // Pass other signals to the next handler.
    case CTRL_BREAK_EVENT:
        Beep(900, 200);
        printf("Ctrl-Break event\n\n");
        return FALSE;

    case CTRL_LOGOFF_EVENT:
        Beep(1000, 200);
        printf("Ctrl-Logoff event\n\n");
        return FALSE;

    case CTRL_SHUTDOWN_EVENT:
        Beep(750, 500);
        printf("Ctrl-Shutdown event\n\n");
        return FALSE;

    default:
        return FALSE;
    }
}

LRESULT CALLBACK WindowProc(HWND hwnd, UINT uMsg, WPARAM wParam, LPARAM lParam)
{
    switch (uMsg)
    {
    case WM_QUERYENDSESSION:
    {
        // Check `lParam` for which system shutdown function and handle events.
        // See https://docs.microsoft.com/windows/win32/shutdown/wm-queryendsession
        return TRUE; // Respect user's intent and allow shutdown.
    }
    case WM_ENDSESSION:
    {
        // Check `lParam` for which system shutdown function and handle events.
        // See https://docs.microsoft.com/windows/win32/shutdown/wm-endsession
        return 0; // We have handled this message.
    }
    default:
        return DefWindowProc(hwnd, uMsg, wParam, lParam);
    }
}

int main(void)
{
    WNDCLASS sampleClass{ 0 };
    sampleClass.lpszClassName = TEXT("CtrlHandlerSampleClass");
    sampleClass.lpfnWndProc = WindowProc;

    if (!RegisterClass(&sampleClass))
    {
        printf("\nERROR: Could not register window class");
        return 2;
    }

    HWND hwnd = CreateWindowEx(
        0,
        sampleClass.lpszClassName,
        TEXT("Console Control Handler Sample"),
        0,
        CW_USEDEFAULT,
        CW_USEDEFAULT,
        CW_USEDEFAULT,
        CW_USEDEFAULT,
        nullptr,
        nullptr,
        nullptr,
        nullptr
    );

    if (!hwnd)
    {
        printf("\nERROR: Could not create window");
        return 3;
    }

    ShowWindow(hwnd, SW_HIDE);

    if (SetConsoleCtrlHandler(CtrlHandler, TRUE))
    {
        printf("\nThe Control Handler is installed.\n");
        printf("\n -- Now try pressing Ctrl+C or Ctrl+Break, or");
        printf("\n    try logging off or closing the console...\n");
        printf("\n(...waiting in a loop for events...)\n\n");

        // Pump message loop for the window we created.
        MSG msg{};
        while (GetMessage(&msg, nullptr, 0, 0) > 0)
        {
            TranslateMessage(&msg);
            DispatchMessage(&msg);
        }
        return 0;
    }
    else
    {
        printf("\nERROR: Could not set control handler");
        return 1;
    }
}
```
