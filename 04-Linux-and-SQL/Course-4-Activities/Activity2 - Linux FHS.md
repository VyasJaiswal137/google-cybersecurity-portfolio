  # Activity 2: File Navigation, Editing, Log Filtering, and Search Operations

## Scenario & Objective

This activity focused on practicing fundamental Linux terminal operations essential for day-to-day security analysis. The primary goal was to gain hands-on experience navigating the file system, creating and modifying files, redirecting data streams, inspecting system logs, and searching for specific files or indicators using command-line tools.

## Commands Used

`pwd`, `ls`, `cd`, `mkdir`, `rmdir`, `touch`, `nano`, `>`, `>>`, `rm`, `cat`, `head`, `tail`, `less`, `grep`, `|` (pipe), `find`

## Key Tasks Completed

### Navigation & Directory Management

* Checked the current working directory path using `pwd` to maintain awareness of the active location within the file tree.
* Navigated between directories using both absolute paths (e.g., `/home/analyst/logs`) and relative paths (e.g., `../projects`) via the `cd` command.
* Created new directories using `mkdir` to organize workspace files and cleaned up unused directories with `rmdir`.

### File Creation & Text Editing

* Generated new, empty files using `touch` to prepare for logging data.
* Created and modified file contents directly within the terminal using the `nano` text editor.
* Utilized standard output redirection operators:
* Overwrote file contents with standard output using `>`.
* Appended log entries to existing files without overwriting prior data using `>>`.


* Safely removed unneeded files from the system using `rm`.

### Log Reading & File Inspection

* Outputted entire file contents to standard output using `cat` for quick viewing.
* Inspected the top portion of log files using `head` (and customized line counts with `-n`) to preview headers.
* Viewed the most recent log entries at the bottom of files using `tail`.
* Browsed through large, multi-page log files efficiently using `less` to scroll backward and forward.

### Searching & Filtering Data

* Extracted specific security strings and error patterns from log files using `grep`.
* Combined commands using the pipe operator (`|`) to send standard output from one tool directly into `grep` for filtering.
* Located files across complex directory structures using `find` with various options:
* Applied `-name` for case-sensitive file name matches.
* Applied `-iname` for case-insensitive matches.
* Used `-mtime` to locate files modified within specific timeframes.

