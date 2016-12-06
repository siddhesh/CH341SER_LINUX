CH341 USB Serial Driver for Linux
=================================

The original code is available for download from:

http://www.wch.cn/download/CH341SER_LINUX_ZIP.html

However, the code does not build since this commit and another commit that
cleaned up wait_interrupt:

    commit 1143832eca8f1d64da7d85642c956ae9d25c69e1
    Author: Greg Kroah-Hartman <gregkh@linuxfoundation.org>
    Date:   Thu Jun 6 10:32:00 2013 -0700
    
        USB: serial: ports: add minor and port number
    
    and another set of commits that dropped the use of
    interruptible_sleep_on since it is racy.  Here's one such commit:
    
    commit 106fd892bc714a9b7c28daba98a3623a41c32f1a
    Author: Arnd Bergmann <arnd@arndb.de>
    Date:   Wed Feb 26 12:01:44 2014 +0100
    
        swim3: fix interruptible_sleep_on race
    
I have patched the code for these changes and verified that it works
correctly on 4.x kernels for my RGUNO, which is an Indian clone of the
Arduino UNO with the CH341 chip.  My patches (past, present and
future) to this code are licensed as GPLv2 (to match the kernel) but I
have no idea what the original code is licensed as, since there is no
indication in the code or the website.
