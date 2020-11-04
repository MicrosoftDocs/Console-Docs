---
title: Scrolling a Screen Buffer's Contents
description: The ScrollConsoleScreenBuffer function moves a block of character cells from one part of a screen buffer to another part of the same screen buffer.
author: miniksa
ms.author: miniksa
ms.topic: sample
keywords: console, character mode applications, command line applications, terminal applications, console api
MS-HAID:
- '\_win32\_scrolling\_a\_screen\_buffer\_s\_contents'
- 'base.scrolling\_a\_screen\_buffer\_s\_contents'
- 'consoles.scrolling\_a\_screen\_buffer\_s\_contents'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/desktop'
ms.assetid: 288c6a0f-fbaa-4eee-895e-a25884b7b70a
---

# Scrolling a Screen Buffer's Contents

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

The [`ScrollConsoleScreenBuffer`](scrollconsolescreenbuffer.md) function moves a block of character cells from one part of a screen buffer to another part of the same screen buffer. The function specifies the upper left and lower right cells of the source rectangle to be moved and the destination coordinates of the new location for the upper left cell. The character and color data in the source cells is moved to the new location, and any cells left empty by the move are filled in with a specified character and color. If a clipping rectangle is specified, the cells outside of it are left unchanged.

[`ScrollConsoleScreenBuffer`](scrollconsolescreenbuffer.md) can be used to delete a line by specifying coordinates of the first cell in the line as the destination coordinates and specifying a scrolling rectangle that includes all the rows below the line.

The following example shows the use of a clipping rectangle to scroll only the bottom 15 rows of the console screen buffer. The rows in the specified rectangle are scrolled up one line at a time, and the top row of the block is discarded. The contents of the console screen buffer outside the clipping rectangle are left unchanged.

```C
#include <windows.h>
#include <stdio.h>

int main( void )
{
    HANDLE hStdout;
    CONSOLE_SCREEN_BUFFER_INFO csbiInfo;
    SMALL_RECT srctScrollRect, srctClipRect;
    CHAR_INFO chiFill;
    COORD coordDest;
    int i;

    printf("\nPrinting 20 lines for reference. ");
    printf("Notice that line 6 is discarded during scrolling.\n");
    for(i=0; i<=20; i++)
        printf("%d\n", i);

    hStdout = GetStdHandle(STD_OUTPUT_HANDLE);

    if (hStdout == INVALID_HANDLE_VALUE)
    {
        printf("GetStdHandle failed with %d\n", GetLastError());
        return 1;
    }

    // Get the screen buffer size.

    if (!GetConsoleScreenBufferInfo(hStdout, &csbiInfo))
    {
        printf("GetConsoleScreenBufferInfo failed %d\n", GetLastError());
        return 1;
    }

    // The scrolling rectangle is the bottom 15 rows of the
    // screen buffer.

    srctScrollRect.Top = csbiInfo.dwSize.Y - 16;
    srctScrollRect.Bottom = csbiInfo.dwSize.Y - 1;
    srctScrollRect.Left = 0;
    srctScrollRect.Right = csbiInfo.dwSize.X - 1;

    // The destination for the scroll rectangle is one row up.

    coordDest.X = 0;
    coordDest.Y = csbiInfo.dwSize.Y - 17;

    // The clipping rectangle is the same as the scrolling rectangle.
    // The destination row is left unchanged.

    srctClipRect = srctScrollRect;

    // Fill the bottom row with green blanks.

    chiFill.Attributes = BACKGROUND_GREEN | FOREGROUND_RED;
    chiFill.Char.AsciiChar = (char)' ';

    // Scroll up one line.

    if(!ScrollConsoleScreenBuffer(  
        hStdout,         // screen buffer handle
        &srctScrollRect, // scrolling rectangle
        &srctClipRect,   // clipping rectangle
        coordDest,       // top left destination cell
        &chiFill))       // fill character and color
    {
        printf("ScrollConsoleScreenBuffer failed %d\n", GetLastError());
        return 1;
    }
return 0;
}
```

## Related topics

[Scrolling a Screen Buffer's Window](scrolling-a-screen-buffer-s-window.md)

[Scrolling the Screen Buffer](scrolling-the-screen-buffer.md)
