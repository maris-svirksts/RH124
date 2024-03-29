# Linux Command Cheat Sheet

## File and Directory Operations

- `cd [directory]` - Changes the current directory.
  - `-` : Moves to the previous directory.
  - `.` : Represents the current directory.
  - `..` : Moves to the parent directory.
  - `/` : Moves to the root directory.
- `ls [options] [directory]` - Lists directory contents.
  - `-al` : Lists detailed information including hidden files.
- `mkdir [options] directory` - Creates a directory.
  - `-p` : Creates parent directories as needed.
- `rmdir [directory]` - Removes empty directories.
- `touch [file]` - Creates an empty file or updates the timestamp of an existing file.

## File Viewing and Manipulation

- `cat [options] [file...]` - Concatenates and displays the content of one or more files.
  - `-n` : Numbers all output lines.
  - `-b` : Numbers non-blank output lines.
  - `-s` : Suppresses repeated empty output lines.
- `head [options] [file]` - Displays the first 10 lines of a file.
  - `-n [number]` : Specifies the number of lines to display.
- `tail [options] [file]` - Displays the last 10 lines of a file.
  - `-n [number]` : Specifies the number of lines to display.
- `wc [options] [file]` - Counts lines, words, and characters in a file.
  - `-l` : Counts only the number of lines.
  - `-w` : Counts only the number of words.
  - `-c` : Counts only the number of characters.
  - `-m` : Counts the number of characters (multibyte support).
  - `-L` : Prints the length of the longest line.


## System Information and Management

- `date [options]` - Displays the current date and time.
  - `+%R` : Displays the current time in 24-hour notation (HH:MM).
  - `+%x` : Displays the current date in the local format.
- `df [options]` - Displays disk space usage.
- `file [file or directory]` - Determines the type of a file or directory.
- `passwd [user]` - Changes the password for the user.
- `whoami` - Displays the current user name.

## User and Group Management

- `useradd [options] username` - Adds a user account.
- `whereis [command]` - Locates the binary, source, and manual page files for a command.

## Linking and Finding Files

- `find [directory] [criteria] [action]` - Searches for files in a directory hierarchy.
- `ln [options] source [destination]` - Creates a hard or symbolic link.
  - `-s` : Creates a symbolic link.
  - Without any options, creates a hard link by default.

To view the number of hard links to a file, use the `ls -l` command which displays the link count in the second column of the output. For example:

```bash
ls -l filename

## Command History and Navigation

- `history [options]` - Displays the command history.
- `!number` - Re-executes the command with the specified history number.

## Variables and Environment

- `VARIABLENAME=value` - Sets a variable.

- `set` : Lists all local shell variables, environment variables, and shell functions.
- To view the value of the `PATH` environment variable, you can use `echo $PATH`.
- To list all environment variables, simply type `env` or `printenv` in the shell.

- `echo [options] [string or variable]` - Displays a message or variable value.
  - `echo $VARIABLENAME` : Displays the value of the variable.
  - `echo "Text $VARIABLENAME more text"` : Displays a string with the variable value embedded within it.
  - `echo "Text ${VARIABLENAME} more text"` : Displays a string with the variable value, using braces for clear variable boundary.
  - `echo "$VARIABLENAME1 $VARIABLENAME2"` : Displays the values of multiple variables.
  - `echo -n [string or variable]` : Displays the message without a trailing newline.
  - `echo -e [string with escape sequences]` : Enables interpretation of backslash escapes (like `\n` for new line, `\t` for tab, etc.).

Examples:
- `echo "Hello, $USER!"` : Displays a greeting message including the current user’s name.
- `echo "Path: $PATH"` : Displays the system’s PATH environment variable.
- `echo -e "Line1\nLine2"` : Displays two lines, using newline character.

## Manual and Help

- `man [options] [command]` - Displays the manual for commands.
  - `-k [keyword]` : Searches for a keyword in command descriptions.
  - `-K [string]` : Searches for a string in all manual pages.

## Multiline Command Example

```bash
head -n 3 \
    /usr/share/dict/words \
    /usr/share/dict/linux.words
```

## Links and File Types

- `ln [source] [destination]` - Creates a hard link.
- `ln -s [source] [destination]` - Creates a symbolic link.

### Hard Links and their Limitations

- Hard links cannot link directories.
- Hard links cannot cross filesystem boundaries.

### Symbolic Links

- Symbolic links can link to directories.
- Symbolic links can cross filesystem boundaries.

## Quoting in Shell

- Double quotes (`"`) allow variable expansion.
- Single quotes (`'`) do not allow variable expansion.

## File and Text Processing

- `cp [options] source [destination]` - Copies files or directories.
  - `-r` : Recursively copies directories.
- `mv [options] source [destination]` - Moves or renames files or directories.
- `rm [options] file` - Removes files or directories.
  - `-r` : Recursively removes directories.

# Useful Command-line Editing Shortcuts

| Shortcut          | Description                                                |
| ----------------- | ---------------------------------------------------------- |
| `Ctrl+A`          | Jump to the beginning of the command line.                 |
| `Ctrl+E`          | Jump to the end of the command line.                       |
| `Ctrl+U`          | Clear from the cursor to the beginning of the command line.|
| `Ctrl+K`          | Clear from the cursor to the end of the command line.      |
| `Ctrl+LeftArrow`  | Jump to the beginning of the previous word on the command line. |
| `Ctrl+RightArrow` | Jump to the end of the next word on the command line.      |
| `Ctrl+R`          | Search the history list of commands for a pattern.         |

# Significant Red Hat Enterprise Linux Directories

| Location | Purpose                                                                                           |
| -------- | ------------------------------------------------------------------------------------------------- |
| `/boot`  | Files to start the boot process.                                                                 |
| `/dev`   | Special device files that the system uses to access hardware.                                    |
| `/etc`   | System-specific configuration files.                                                             |
| `/home`  | Home directory, where regular users store their data and configuration files.                    |
| `/root`  | Home directory for the administrative superuser, root.                                           |
| `/run`   | Runtime data for processes that started since the last boot.                                     |
| `/tmp`   | A world-writable space for temporary files.                                                      |
| `/usr`   | Installed software, shared libraries, including files, and read-only program data.               |
| `/var`   | System-specific variable data should persist between boots.                                      |

# Table of Metacharacters and Matches

| Pattern          | Matches                                                            |
| ---------------- | ------------------------------------------------------------------ |
| `*`              | Any string of zero or more characters                              |
| `?`              | Any single character                                               |
| `[abc…​]`         | Any one character in the enclosed class                            |
| `[!abc…​]`        | Any one character not in the enclosed class                        |
| `[^abc…​]`        | Any one character not in the enclosed class                        |
| `[[:alpha:]]`    | Any alphabetic character                                           |
| `[[:lower:]]`    | Any lowercase character                                            |
| `[[:upper:]]`    | Any uppercase character                                            |
| `[[:alnum:]]`    | Any alphabetic character or digit                                  |
| `[[:punct:]]`    | Any printable character that is not a space or alphanumeric        |
| `[[:digit:]]`    | Any single digit from 0 to 9                                       |
| `[[:space:]]`    | Any single white space character                                   |

# Navigate man Pages

| Command   | Result                                                   |
| --------- | -------------------------------------------------------- |
| `Spacebar`| Scroll forward (down) one screen.                        |
| `PageDown`| Scroll forward one screen.                               |
| `PageUp`  | Scroll backward (up) one screen.                         |
| `DownArrow` | Scroll forward one line.                                |
| `UpArrow` | Scroll backward one line.                                |
| `D`       | Scroll forward one half-screen.                          |
| `U`       | Scroll backward one half-screen.                         |
| `/string` | Search forward for string in the man page.               |
| `N`       | Repeat previous search forward in the man page.          |
| `Shift+N` | Repeat previous search backward in the man page.         |
| `G`       | Go to the start of the man page.                         |
| `Shift+G` | Go to the end of the man page.                           |
| `Q`       | Exit man and return to the command shell prompt.         |
                                                        