## fpick

`fpick` is a file-picker program that lets you select a subset of files
in a folder using a curses-based GUI. `fpick` outputs your selection in
the form of an `rsync` exclude file that can be used to move or copy 
the files you selected. `fpick` will also display the total size of
the fileset you've selected. 

I mainly use `fpick` to select files to sync to my mp3 player. I wrote 
`fpick` because I was annoyed that most file-pickers don't show you a
running total of the fileset, so it's hard to estimate whether a particular
selection of files can be loaded onto an mp3 player.

### Usage

    $ fpick /path/to/root

### Key Bindings

`fpick` is a modal program, there are two modes: "Command Mode", and 
"Selection Mode". Selection mode is used to select files from the
main window, while command mode is used to enter special command or exit
the program.  

#### Mode Switching

| Key | Action |
|-----|--------|
| `:` | Switch from selection mode to command mode. |
| `ESC` | Switch from command mode to selection mode. |

#### Selection Mode Bindings

| Key | Action |
|-----|--------|
| `j` | Highlight the next element in the list. (Move Down) | 
| `k` | Highlight the previous element in the list. (Move Up) | 
| `f` | Scroll to the next page of elements. |
| `b` | Scroll to the previous page of elements. |
| `e` | Expand the currently highlighted element. (Expand Folder) |
| `c` | Collapse the currently highlighted element. (Collapse Folder) |
| `s` | Toggle the selection of the current element. |
| `g` | Scroll to and highlight the first element of the list. |
| `G` | Scroll to and highlight the last element of the list. |
| `D` | Dump the current selections to stderr as an rsync exclude file. |

#### Command Mode Commands

To enter these commands, press `:`, type the entire command into the prompt
and then press `ENTER`. You will be automatically switched back to selection
mode if the command is executed successfully. The `Key` column is the
selection-mode key binding for the command. All selection-mode keys are
just bindings to command-mode commands.

| Command | Key | Action |
|---------|-----|--------|
| `quit` |  | Exit the program.|
| `dump` | `D` | Dump the current selections to stderr as an rsync exclude file. |
| `next` | `j` | Highlight the next element in the list. |
| `prev` | `k` | Highlight the previous element in the list. |
| `next_page` | `f` | Scroll to the next page of elements. |
| `prev_page` | `b` | Scroll to the previous page of elements. |
| `top` | `g` | Scroll to, and highlight, the first element of the list. |
| `bottom` | `G` | Scroll to, and highlight, the last element of the list. |
| `expand_current` | `e` | Expand the currently-highlighted element. |
| `collapse_current` | `c` | Collapse the currently-highlighted element. |
| `toggle_select_current` | `s` | Toggle the selection of the currently-highlighted element. |

If you're unhappy with any of the key bindings, you may want to look around
[line 518][bind] of the code which contains the key-bindings. You can
change those bindings to be whatever you want. Any method of the `Screen`
class can be bound to a key using that dictionary.

  [bind]: https://github.com/Joshkunz/fpick/blob/master/fpick#L518

