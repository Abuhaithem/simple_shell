# Simple shell
<a><img src="https://user-images.githubusercontent.com/107338221/188614438-f184a7f0-c87d-4860-a8bb-c0e9226a2075.png" align="middle" width="200" height="200"></a> 


## Table of Contents
* [Description](#description)
* [File Structure](#file-structure)
* [Requirements](#requirements)
* [Installation](#installation)
* [Usage](#usage)
* [Example of Use](#example-of-use)
* [Bugs](#bugs)
* [Authors](#authors)
* [License](#license)

## Description
simple_shell is a command line interpreter, or shell, in the tradition of the first Unix shell written by Ken Thompson in 1971. This shell is intentionally minimalistic, yet includes the basic functionality of a traditional Unix-like command line user interface. 
Standard functions and system calls employed in simple_shell include:
   `access, execve, exit, fork, free, fstat, getline, malloc, perror, signal, stat, wait, write.`

## File Structure
* [AUTHORS](AUTHORS) - List of contributors to this repository
* [shell.h](shell.h) - program header file
* [_atoi.c](_atoi.c) - major builtin functions
  * `interactive` - returns true if shell is interactive mode
  * `is_delim` - checks if character is a delimeter
  * `_isalpha` - checks for alphabetic character
  * `_atoi` - converts a string to an integer
* [builtin.c](builtin.c) - helper functions for the builtins
  * `_myexit` - exits the shell
  * `_mycd` - changes the current directory of the process
  * `_myhelp` - changes the current directory of the process
* [builtin1.c](builtin1.c) - functions related to the environment
  * `_myhistory` - displays the history list, one command by line, preceded
  * `unset_alias` - sets alias to string
  * `set_alias` - sets alias to string
  * `print_alias` - prints an alias string
  * `_myalias` - mimics the alias builtin (man alias)
* [environ.c](environ.c) - functions related to printing errors
  * `_myenv` - prints the current environment
  * `_getenv` - gets the value of an environ variable
  * `_mysetenv` - Initialize a new environment variable or modify an existing one
  * `_myunsetenv` - Remove an environment variable
  * `populate_env_list` - populates env linked list
* [errors.c](errors.c) - memory allocation functions
  * `_eputs` - prints an input string
  *  `_eputchar` - writes the character c to stderr
  *  `_putfd` - writes the character c to given fd
  *  `_putsfd` - prints an input string  
* [errors1.c](errors1.c) - custom strtok and helper functions
  * `_erratoi` - converts a string to an integer
  * `print_error` - prints an error message
  * `print_d` - function prints a decimal (integer) number (base 10)
  * `convert_number` - converter function, a clone of itoa
  * `remove_comments` - function replaces first instance of '#' with '\0'
* [exits.c](exits.c) - functions related to executing commands
  * `*_strncpy` - copies a string
  * `*_strncat` - concatenates two strings
  * `*_strchr` - locates a character in a string
* [getLine.c](getLine.c) - functions related to executing commands
  * `input_buf` - buffers chained commands
  * `get_input` - gets a line minus the newline
  * `read_buf` - reads a buffer
  * `_getline` - gets the next line of input from STDIN
  * `sigintHandler` - blocks ctrl-C
* [getenv.c](getenv.c) - functions related to executing commands
  * `get_environ` - returns the string array copy of our environ
  * `_unsetenv` - Remove an environment variable
  * `_setenv` - Initialize a new environment variable or modify an existing one
* [getinfo.c](getinfo.c) - functions related to executing commands
  * `clear_info` - initializes info_t struct
  * `set_info` - initializes info_t struct
  * `free_info` - frees info_t struct fields
* [history.c](history.c) - functions related to executing commands
  * `get_history_file` - gets the history file
  * `write_history` - creates a file, or appends to an existing file
  * `read_history` - reads history from file
  * `build_history_list` - adds entry to a history linked list
  * `renumber_history` - renumbers the history linked list after changes
* [lists.c](lists.c) - functions related to executing commands
  * `add_node` - adds a node to the start of the list
  * `add_node_end` - adds a node to the end of the list
  * `print_list_str` - prints only the str element of a list_t linked list
  * `delete_node_at_index` - deletes node at given index
  * ` free_list` - frees all nodes of a list
* [lists1.c](lists1.c) - functions related to executing commands
  * `list_len` - determines length of linked list
  * `list_to_strings` - returns an array of strings of the list->str
  * `print_list` - prints all elements of a list_t linked list
  * `node_starts_with` - returns node whose string starts with prefix
  * `get_node_index` - gets the index of a node
* [main.c](main.c) - entry point
* [memory.c](memory.c) - functions related to executing commands
  * `bfree` - frees a pointer and NULLs the address
* [parser.c](parser.c) - functions related to executing commands
  * `is_cmd` - determines if a file is an executable command
  * `dup_chars` - duplicates characters
  * `find_path` - finds this cmd in the PATH string
* [realloc.c](realloc.c) - functions related to executing commands
  * `*_memset` - fills memory with a constant byte
  * `ffree` - frees a string of strings
  * `_realloc` - reallocates a block of memory
* [shell_loop.c](shell_loop.c) - functions related to executing commands
  * `hsh` - main shell loop
  * `find_builtin` - finds a builtin command
  * `find_cmd` - finds a command in PATH
  * `fork_cmd` - forks a an exec thread to run cmd
* [string.c](string.c) - functions related to executing commands
  * `_strlen` - returns the length of a string
  * `_strcmp` - performs lexicogarphic comparison of two strangs.
  * `starts_with` - checks if needle starts with haystack
  * `_strcat` - concatenates two strings
 * [string1.c](string1.c) - functions related to executing commands
   * `_strcpy` - copies a string
   * `_strdup` - duplicates a string
   * `_puts` - prints an input string
   * `_putchar - writes the character c to stdout
 * [tokenizer.c](tokenizer.c) - functions related to executing commands
   * `**strtow` - splits a string into words. Repeat delimiters are ignored
   * `**strtow2` - splits a string into words
 * [vars.c](vars.c) - functions related to executing commands
   * `is_chain` - test if current char in buffer is a chain delimeter
   * `check_chain` - checks we should continue chaining based on last status
   * `replace_alias` - replaces an aliases in the tokenized string
   * `replace_vars` - replaces vars in the tokenized string
   * `replace_string` - replaces string

## Requirements

simple_shell is designed to run in the `Ubuntu 20.04 LTS` linux environment and to be compiled using the GNU compiler collection v. `gcc`, using the options `-Wall -Werror -Wextra -pedantic -std=gnu89`

## Installation

   - Clone this repository: `git clone "https://github.com/AbuhaithemAlthry/simple_shell.git"`
   - Change directories into the repository: `cd simple_shell`
   - Compile: `gcc -Wall -Werror -Wextra -pedantic -std=gnu89 *.c -o hsh`
   - Run the shell in interactive mode: `./hsh`
   - Or run the shell in non-interactive mode: example `echo "pwd" | ./hsh`

## Usage

The simple_shell is designed to execute commands in a similar manner to sh, however with more limited functionality. The development of this shell is ongoing. The below features will be checked as they become available (see man page for complete information on usage):

### Features
- [x] uses the PATH
- [x] implements builtins
- [x] handles command line arguments
- [x] custom strtok function
- [x] uses exit status
- [x] shell continues upon Crtl+C (**^C**)
- [x] handles comments (#)
- [x] handles **;**
- [x] custom getline type function
- [x] handles **&&** and **||**
- [x] aliases
- [x] variable replacement


### Builtins

- [x] exit
- [x] env
- [x] setenv
- [x] unsetenv
- [x] cd
- [x] help
- [x] history

## Example of Use
Run the executable in your terminal after compiling:
```
$ ./hsh
$ # This is our rendition of the shell
$ ls -al
total 100
drwxrwxr-x  3 vagrant vagrant  4096 Jul 19 22:49 .
drwxr-xr-x 14 vagrant vagrant  4096 Jul 17 22:37 ..
-rw-rw-r--  1 vagrant vagrant   144 Jul 19 17:16 AUTHORS
-rw-rw-r--  1 vagrant vagrant  2367 Jul 19 22:33 builtins2.c
-rw-rw-r--  1 vagrant vagrant  2764 Jul 19 22:14 builtins.c
-rw-rw-r--  1 vagrant vagrant   710 Jul 16 01:03 environment.c
-rw-rw-r--  1 vagrant vagrant  1217 Jul 16 03:24 errors.c
drwxrwxr-x  8 vagrant vagrant  4096 Jul 19 22:34 .git
-rwxrwxr-x  1 vagrant vagrant 32287 Jul 19 22:34 hsh
-rw-rw-r--  1 vagrant vagrant  1792 Jul 19 22:12 man_1_simple_shell
-rw-rw-r--  1 vagrant vagrant   484 Jul 15 20:09 memory_allocation.c
-rw-rw-r--  1 vagrant vagrant  1273 Jul 18 21:00 new_strtok.c
-rw-rw-r--  1 vagrant vagrant  3427 Jul 19 22:06 path.c
-rw-rw-r--  1 vagrant vagrant  2347 Jul 19 22:49 README.md
-rw-rw-r--  1 vagrant vagrant  1769 Jul 19 22:04 shell.h
-rw-rw-r--  1 vagrant vagrant  1480 Jul 18 21:15 simple_shell.c
-rw-rw-r--  1 vagrant vagrant  2111 Jul 16 01:10 strfunc.c
-rw-rw-r--  1 vagrant vagrant   719 Jul 19 21:46 tokenize.c
```
## Bugs
At this time, there are no known bugs.

## Authors
Seid Muhammed | [GitHub](https://github.com/AbuhaithemAlthry) | [Twitter](https://twitter.com/Abu_Haithem_)

Selehadin Seid | [GitHub](https://github.com/Saladii) 

## License
simple_shell is open source and therefore free to download and use without permission.
