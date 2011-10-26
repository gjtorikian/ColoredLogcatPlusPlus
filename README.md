# Introduction

ColoredLogcat++ is an extension of [Jeff Sharkey's excellent ColoredLogcat](http://jsharkey.org/blog/2009/04/22/modifying-the-android-logcat-stream-for-full-color-debugging/) terminal hack for Android development. So far, the only difference it contains is the ability to filter the log based on text. This text currently does _not_ support regular expressions, though if interest is there I can certainly implement it.

Eventually, I'd like to support [all the new logcat features available in the r14 Android SDK release](http://tools.android.com/recent/updatedlogcatviewer). Time permitting, naturally.

# Usage

This is an expansion on Jeff's original documentation. It also changes the format somewhat.

You must run ColoredLogcat++ by piping content directly using `adb`:

	adb logcat | ~/coloredlogcatpp.py

While piping the text, you can pass the the `-f` switch to filter text from your log.

For example:

	adb logcat | ~/coloredlogcatpp.py -f Nyan

Will only show log messages with the (case-sensitive) string of "Nyan" anywhere within them, be it the tag or the message itself.

You can string together as many `-f` filters as you like:

	adb logcat | ~/coloredlogcatpp.py -f Nyan -f Meow -f Hiss -f urr

Some of the original logcat paramters remain. For example:

	adb logcat *:I | ~/coloredlogcatpp.py -f arfield

Will show any "Info" messages (or higher) that contains the "arfield" string.

# Future

I hope to be able to implement more of the standard logcat parameters in upcoming iterations. Also, I'm pretty sure this only works on *nix machines, and haven't tried it on Cygwin.