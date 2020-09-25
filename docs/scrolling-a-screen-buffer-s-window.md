---
title: Scrolling a Screen Buffer's Window
description: The SetConsoleWindowInfo function can be used to scroll the contents of a screen buffer in the console window.
author: miniksa
ms.author: miniksa
ms.topic: sample
keywords: console, character mode applications, command line applications, terminal applications, console api
MS-HAID:
- '\_win32\_scrolling\_a\_screen\_buffer\_s\_window'
- 'base.scrolling\_a\_screen\_buffer\_s\_window'
- 'consoles.scrolling\_a\_screen\_buffer\_s\_window'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: bc300349-9bfa-4417-92ad-57a05a658ce5
---

# Scrolling a Screen Buffer's Window

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

The [**SetConsoleWindowInfo**](setconsolewindowinfo.md) function can be used to scroll the contents of a screen buffer in the console window. This function can also change the window size. The function can either specify the new upper left and lower right corners of the console screen buffer's window as absolute screen buffer coordinates or specify the changes from the current window coordinates. The function fails if the specified window coordinates are outside the boundaries of the console screen buffer.

The following example scrolls the view of the console screen buffer up by modifying the window coordinates returned by the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function. The `ScrollByAbsoluteCoord` function demonstrates how to specify absolute coordinates, while the `ScrollByRelativeCoord` function demonstrates how to specify relative coordinates.

```C
#include <windows.h>
#include <stdio.h>
#include <conio.h>

HANDLE hStdout; 

int ScrollByAbsoluteCoord(int iRows)
{
    CONSOLE_SCREEN_BUFFER_INFO csbiInfo; 
    SMALL_RECT srctWindow; 
 
    // Get the current screen buffer size and window position. 
 
    if (! GetConsoleScreenBufferInfo(hStdout, &csbiInfo)) 
    {
        printf("GetConsoleScreenBufferInfo (%d)\n", GetLastError()); 
        return 0;
    }
 
    // Set srctWindow to the current window size and location. 
 
    srctWindow = csbiInfo.srWindow; 
 
    // Check whether the window is too close to the screen buffer top
 
    if ( srctWindow.Top >= iRows ) 
    { 
        srctWindow.Top -= (SHORT)iRows;     // move top up
        srctWindow.Bottom -= (SHORT)iRows;  // move bottom up

        if (! SetConsoleWindowInfo( 
                   hStdout,          // screen buffer handle 
                   TRUE,             // absolute coordinates 
                   &srctWindow))     // specifies new location 
        {
            printf("SetConsoleWindowInfo (%d)\n", GetLastError()); 
            return 0;
        }
        return iRows;
    }
    else
    {
        printf("\nCannot scroll; the window is too close to the top.\n");
        return 0;
    }
}

int ScrollByRelativeCoord(int iRows)
{
    CONSOLE_SCREEN_BUFFER_INFO csbiInfo; 
    SMALL_RECT srctWindow; 

    // Get the current screen buffer window position. 
 
    if (! GetConsoleScreenBufferInfo(hStdout, &csbiInfo)) 
    {
        printf("GetConsoleScreenBufferInfo (%d)\n", GetLastError()); 
        return 0;
    }
 
    // Check whether the window is too close to the screen buffer top
 
    if (csbiInfo.srWindow.Top >= iRows) 
    { 
        srctWindow.Top =- (SHORT)iRows;     // move top up
        srctWindow.Bottom =- (SHORT)iRows;  // move bottom up 
        srctWindow.Left = 0;         // no change 
        srctWindow.Right = 0;        // no change 
 
        if (! SetConsoleWindowInfo( 
                   hStdout,          // screen buffer handle 
                   FALSE,            // relative coordinates
                   &srctWindow))     // specifies new location 
        {
            printf("SetConsoleWindowInfo (%d)\n", GetLastError()); 
            return 0;
        }
        return iRows;
    }
    else
    {
        printf("\nCannot scroll; the window is too close to the top.\n");
        return 0;
    }
}

int main( void )
{
    int i;

    printf("\nPrinting twenty lines, then scrolling up five lines.\n");
    printf("Press any key to scroll up ten lines; ");
    printf("then press another key to stop the demo.\n");
    for(i=0; i<=20; i++)
        printf("%d\n", i);

    hStdout = GetStdHandle(STD_OUTPUT_HANDLE); 

    if(ScrollByAbsoluteCoord(5))
        _getch();
    else return 0;

    if(ScrollByRelativeCoord(10))
        _getch();
    else return 0;
}
```

## <span id="related_topics"></span>Related topics


[Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md)

[Scrolling the Screen Buffer](scrolling-the-screen-buffer.md)
