# EMACS

## Buffers, Files, and Windows

Every file has one buffer. EMACS edits buffers. Saving with `C-x C-s`
flushes buffer to file.

- Some special buffers don't correspond to any file (e.g. scratch,
  shell, messages)

Windows and buffers separate. Can have multiple windows viewing
different parts of the same buffer, or buffers not shown in any
window. In particular, closing a window does not close the buffer
associated to that window.

Window manipulation commands: `C-x 0`, `C-x 1`, `C-x 2`, `C-x 3`, `C-x
o`

Buffer manipulation commands: `C-x b`, `C-x k`, `C-x C-f` (creates a
buffer for selected file)

The very last line on the screen that displays stuff like currently
typed commands is called the "mini-buffer".

## Modes

Every buffer has a major mode (dependent on type of file it
corresponds to) and possibly multiple minor modes. When in different
modes, possibly have some different key-bindings and different
features.

Every window has a status bar at the bottom, telling the mode of the
buffer the window is viewing (as well as the position of the cursor
and other infomation). The status bar is also called the mode line.

## Elisp

Emacs = Elisp interpreter written in C + editor written in Elisp.
Thus, by programming in Elisp, we can virtually change anything about
the editing functionality which is extremely powerful.
