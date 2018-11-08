---
title: Registering a Control Handler Function
description: This is an example of the SetConsoleCtrlHandler function that is used to install a control handler.
author: bitcrazed
ms.author: richturn
ms.topic: article
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


This is an example of the [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) function that is used to install a control handler.

When a CTRL+C signal is received, the control handler returns **TRUE**, indicating that it has handled the signal. Doing this prevents other control handlers from being called.

When a **CTRL\_CLOSE\_EVENT** signal is received, the control handler returns **TRUE** and the process terminates.

When a **CTRL\_BREAK\_EVENT**, **CTRL\_LOGOFF\_EVENT**, or **CTRL\_SHUTDOWN\_EVENT** signal is received, the control handler returns **FALSE**. Doing this causes the signal to be passed to the next control handler function. If no other control handlers have been registered or none of the registered handlers returns **TRUE**, the default handler will be used, resulting in the process being terminated.

```C
#include <windows.h> 
#include <stdio.h> 
 
BOOL CtrlHandler( DWORD fdwCtrlType ) 
{ 
  switch( fdwCtrlType ) 
  { 
    // Handle the CTRL-C signal. 
    case CTRL_C_EVENT: 
      printf( "Ctrl-C event\n\n" );
      Beep( 750, 300 ); 
      return( TRUE );
 
    // CTRL-CLOSE: confirm that the user wants to exit. 
    case CTRL_CLOSE_EVENT: 
      Beep( 600, 200 ); 
      printf( "Ctrl-Close event\n\n" );
      return( TRUE ); 
 
    // Pass other signals to the next handler. 
    case CTRL_BREAK_EVENT: 
      Beep( 900, 200 ); 
      printf( "Ctrl-Break event\n\n" );
      return FALSE; 
 
    case CTRL_LOGOFF_EVENT: 
      Beep( 1000, 200 ); 
      printf( "Ctrl-Logoff event\n\n" );
      return FALSE; 
 
    case CTRL_SHUTDOWN_EVENT: 
      Beep( 750, 500 ); 
      printf( "Ctrl-Shutdown event\n\n" );
      return FALSE; 
 
    default: 
      return FALSE; 
  } 
} 
 
int main( void ) 
{ 
  if( SetConsoleCtrlHandler( (PHANDLER_ROUTINE) CtrlHandler, TRUE ) ) 
  { 
    printf( "\nThe Control Handler is installed.\n" ); 
    printf( "\n -- Now try pressing Ctrl+C or Ctrl+Break, or" ); 
    printf( "\n    try logging off or closing the console...\n" ); 
    printf( "\n(...waiting in a loop for events...)\n\n" ); 
 
    while( 1 ){ } 
  } 
  else 
  {
    printf( "\nERROR: Could not set control handler"); 
    return 1;
  }
return 0;
}
```

 

 




