---
title: Reading Input Buffer Events
description: The ReadConsoleInput function can be used to directly access a console's input buffer.
author: miniksa
ms.author: miniksa
ms.assetid: 57570f3b-4a37-4789-bf6c-474fae60171d
---

# Reading Input Buffer Events


The [**ReadConsoleInput**](readconsoleinput.md) function can be used to directly access a console's input buffer. When a console is created, mouse input is enabled and window input is disabled. To ensure that the process receives all types of events, this example uses the [**SetConsoleMode**](setconsolemode.md) function to enable window and mouse input. Then it goes into a loop that reads and handles 100 console input events. For example, the message "Keyboard event" is displayed when the user presses a key and the message "Mouse event" is displayed when the user interacts with the mouse.

```C++
#include <windows.h>
#include <stdio.h>

HANDLE hStdin; 
DWORD fdwSaveOldMode;

VOID ErrorExit(LPSTR);
VOID KeyEventProc(KEY_EVENT_RECORD); 
VOID MouseEventProc(MOUSE_EVENT_RECORD); 
VOID ResizeEventProc(WINDOW_BUFFER_SIZE_RECORD); 
 
int main(VOID) 
{ 
    DWORD cNumRead, fdwMode, i; 
    INPUT_RECORD irInBuf[128]; 
    int counter=0;
 
    // Get the standard input handle. 
 
    hStdin = GetStdHandle(STD_INPUT_HANDLE); 
    if (hStdin == INVALID_HANDLE_VALUE) 
        ErrorExit("GetStdHandle"); 
 
    // Save the current input mode, to be restored on exit. 
 
    if (! GetConsoleMode(hStdin, &amp;fdwSaveOldMode) ) 
        ErrorExit("GetConsoleMode"); 

    // Enable the window and mouse input events. 
 
    fdwMode = ENABLE_WINDOW_INPUT | ENABLE_MOUSE_INPUT; 
    if (! SetConsoleMode(hStdin, fdwMode) ) 
        ErrorExit("SetConsoleMode"); 
 
    // Loop to read and handle the next 100 input events. 
 
    while (counter++ <= 100) 
    { 
        // Wait for the events. 
 
        if (! ReadConsoleInput( 
                hStdin,      // input buffer handle 
                irInBuf,     // buffer to read into 
                128,         // size of read buffer 
                &amp;cNumRead) ) // number of records read 
            ErrorExit("ReadConsoleInput"); 
 
        // Dispatch the events to the appropriate handler. 
 
        for (i = 0; i < cNumRead; i++) 
        {
            switch(irInBuf[i].EventType) 
            { 
                case KEY_EVENT: // keyboard input 
                    KeyEventProc(irInBuf[i].Event.KeyEvent); 
                    break; 
 
                case MOUSE_EVENT: // mouse input 
                    MouseEventProc(irInBuf[i].Event.MouseEvent); 
                    break; 
 
                case WINDOW_BUFFER_SIZE_EVENT: // scrn buf. resizing 
                    ResizeEventProc( irInBuf[i].Event.WindowBufferSizeEvent ); 
                    break; 
 
                case FOCUS_EVENT:  // disregard focus events 
 
                case MENU_EVENT:   // disregard menu events 
                    break; 
 
                default: 
                    ErrorExit("Unknown event type"); 
                    break; 
            } 
        }
    } 

    // Restore input mode on exit.

    SetConsoleMode(hStdin, fdwSaveOldMode);
 
    return 0; 
}

VOID ErrorExit (LPSTR lpszMessage) 
{ 
    fprintf(stderr, "%s\n", lpszMessage); 

    // Restore input mode on exit.

    SetConsoleMode(hStdin, fdwSaveOldMode);

    ExitProcess(0); 
}

VOID KeyEventProc(KEY_EVENT_RECORD ker)
{
    printf("Key event: ");

    if(ker.bKeyDown)
        printf("key pressed\n");
    else printf("key released\n");
}

VOID MouseEventProc(MOUSE_EVENT_RECORD mer)
{
#ifndef MOUSE_HWHEELED
#define MOUSE_HWHEELED 0x0008
#endif
    printf("Mouse event: ");
    
    switch(mer.dwEventFlags)
    {
        case 0:

            if(mer.dwButtonState == FROM_LEFT_1ST_BUTTON_PRESSED)
            {
                printf("left button press \n");
            }
            else if(mer.dwButtonState == RIGHTMOST_BUTTON_PRESSED)
            {
                printf("right button press \n");
            }
            else
            {
                printf("button press\n");
            }
            break;
        case DOUBLE_CLICK:
            printf("double click\n");
            break;
        case MOUSE_HWHEELED:
            printf("horizontal mouse wheel\n");
            break;
        case MOUSE_MOVED:
            printf("mouse moved\n");
            break;
        case MOUSE_WHEELED:
            printf("vertical mouse wheel\n");
            break;
        default:
            printf("unknown\n");
            break;
    }
}

VOID ResizeEventProc(WINDOW_BUFFER_SIZE_RECORD wbsr)
{
    printf("Resize event\n");
    printf("Console screen buffer is %d columns by %d rows.\n", wbsr.dwSize.X, wbsr.dwSize.Y);
}
```

 

 




