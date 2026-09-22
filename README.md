==========================================================
 TELEGRAM HELLO
 Opens Telegram Desktop, jumps to a pinned chat, types
 "hello" and presses Enter.
==========================================================

HOW TO RUN (PowerShell)
-----------------------
Open PowerShell and run:

    & "$env:USERPROFILE\Documents\telegram-hello\telegram-hello.exe"

Or from inside the folder:

    cd $HOME\Documents\telegram-hello
    .\telegram-hello.exe

That's it. If Telegram is not running, the script starts it first.

OPTIONS
-------
    -msg  "text"     message to send            (default: hello)
    -pin  N          which pinned chat, 1 to 8  (default: 1)
    -dry             select the pinned chat but do not type anything
    -exe  "path"     explicit path to Telegram.exe
    -wait N          seconds to wait for Telegram to open (default: 20)

EXAMPLES
--------
    .\telegram-hello.exe -pin 2 -msg "hi there"
    .\telegram-hello.exe -dry
    .\telegram-hello.exe -exe "F:\balls\Telegram Desktop\Telegram.exe"

HOW IT WORKS
------------
Telegram Desktop binds Ctrl+1..Ctrl+8 to "jump to pinned chat 1..8".
The script focuses the Telegram window and sends that key combination,
then types your message with simulated keyboard input. No mouse clicks,
no screen coordinates.

NOTES AND CAVEATS
-----------------
- Do not click away while it runs: keystrokes go to whatever window has
  focus at that moment.
- Needs an unlocked interactive desktop (works over RDP only while the
  session is open and visible).
- Works with Telegram Desktop only, not the Microsoft Store version or
  Telegram Web.
- Only pinned chats 1-8 are reachable.

REBUILDING FROM SOURCE
----------------------
Source: main.go in this folder. Requires Go (installed via winget):

    cd $HOME\Documents\telegram-hello
    go build -o telegram-hello.exe .
