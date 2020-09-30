---
title: Clearing the Screen
description: How to clear the screen of the Windows Console using the system function or programmatically using public API functions.
author: miniksa
ms.author: miniksa
ms.topic: sample
keywords: console, character mode applications, command line applications, terminal applications, console api
MS-HAID:
- '\_win32\_clearing\_the\_screen'
- 'base.clearing\_the\_screen'
- 'consoles.clearing\_the\_screen'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 2097cc53-13b9-4f29-9d2c-feea56a27cb8
---

# Clearing the Screen


There are four ways to clear the screen in a console application.

## <span id="Example_1"></span><span id="example_1"></span><span id="EXAMPLE_1"></span>Example 1

> [!TIP]
> This is the recommended method using **[virtual terminal sequences](console-virtual-terminal-sequences.md)** for all new development. For more information, see the discussion of **[classic console APIs versus virtual terminal sequences](classic-vs-vt.md)**.

The first method is to set your application up for virtual terminal output sequences and then call the "clear screen" command.

```C

#include <windows.h>

int main( void )
{
    HANDLE hStdout;

    hStdout = GetStdHandle(STD_OUTPUT_HANDLE);

    // Fetch existing console mode so we correctly add a flag and not turn off others
    DWORD mode = 0;
    if (!GetConsoleMode(hStdOut, &mode))
    {
        return ::GetLastError();
    }

    // Hold original mode to restore on exit to be cooperative with other command-line apps.
    const DWORD originalMode = mode;
    mode |= ENABLE_VIRTUAL_TERMINAL_PROCESSING;

    // Try to set the mode.
    if (!SetConsoleMode(hStdOut, mode))
    {
        return ::GetLastError();
    }

    // Write the sequence for clearing the display.
    DWORD written = 0;
    PCWSTR sequence = L"\x1b[2J";
    if (!WriteConsoleW(hStdOut, sequence, ARRAYSIZE(sequence), &written, NULL))
    {
        // If we fail, try to restore the mode on the way out.
        SetConsoleMode(hStdOut, originalMode);
        return ::GetLastError();
    }
    
    // Restore the mode on the way out to be nice to other command-line applications.
    SetConsoleMode(hStdOut, originalMode);

    return 0;
}

```

A variation on this command is to use the "clear buffer" command to remove all history scrolling up and down, not just what is visible within the window.

```C
...

PCWSTR sequence = L"\x1b[3J";

...
```

You can find additional variations on this command in the virtual terminal sequences documentation on **[Erase In Display](console-virtual-terminal-sequences.md#text-modification)**.

## <span id="Example_2"></span><span id="example_2"></span><span id="EXAMPLE_2"></span>Example 2

The second method is to write a function to scroll the contents of the screen or buffer and set a fill for the revealed space.

This matches the behavior of (CMD OR POWERSHELL, WHICH WAS IT)

```C
```

## <span id="Example_3"></span><span id="example_3"></span><span id="EXAMPLE_3"></span>Example 3


The third method is to write a function to programmatically clear the screen using the [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md) and [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md) functions. 

This matches the behavior of (CMD OR POWERSHELL, WHICH WAS IT)

The following sample code demonstrates this technique.

```C
#include <windows.h>

void cls( HANDLE hConsole )
{
   COORD coordScreen = { 0, 0 };    // home for the cursor 
   DWORD cCharsWritten;
   CONSOLE_SCREEN_BUFFER_INFO csbi; 
   DWORD dwConSize;

// Get the number of character cells in the current buffer. 

   if( !GetConsoleScreenBufferInfo( hConsole, &csbi ))
   {
      return;
   }

   dwConSize = csbi.dwSize.X * csbi.dwSize.Y;

   // Fill the entire screen with blanks.

   if( !FillConsoleOutputCharacter( hConsole,        // Handle to console screen buffer 
                                    (TCHAR) ' ',     // Character to write to the buffer
                                    dwConSize,       // Number of cells to write 
                                    coordScreen,     // Coordinates of first cell 
                                    &cCharsWritten ))// Receive number of characters written
   {
      return;
   }

   // Get the current text attribute.

   if( !GetConsoleScreenBufferInfo( hConsole, &csbi ))
   {
      return;
   }

   // Set the buffer's attributes accordingly.

   if( !FillConsoleOutputAttribute( hConsole,         // Handle to console screen buffer 
                                    csbi.wAttributes, // Character attributes to use
                                    dwConSize,        // Number of cells to set attribute 
                                    coordScreen,      // Coordinates of first cell 
                                    &cCharsWritten )) // Receive number of characters written
   {
      return;
   }

   // Put the cursor at its home coordinates.

   SetConsoleCursorPosition( hConsole, coordScreen );
}

int main( void )
{
    HANDLE hStdout;

    hStdout = GetStdHandle(STD_OUTPUT_HANDLE);

    cls(hStdout);
    
    return 0;
}
```

## <span id="Example_4"></span><span id="example_4"></span><span id="EXAMPLE_4"></span>Example 4

The fourth method is to use the C run-time **system** function. The **system** function invokes the **cls** command provided by the command interpreter `cmd.exe` to clear the screen.

```C
#include <stdlib.h>

int main( void )
{
    system("cls");
    return 0;
}
```
