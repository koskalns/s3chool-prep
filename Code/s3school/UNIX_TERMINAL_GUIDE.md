# Unix Terminal Essentials Guide

## What is the Unix Terminal?
The terminal is a text-based interface to your operating system. On Windows, you can use Git Bash or PowerShell. On Mac/Linux, it's the native Terminal.

---

## Core Concepts

### File System Navigation
The file system is organized as a tree with directories (folders) and files.

**Key paths:**
- `/` - Root directory (top of the file system)
- `~` - Home directory (your user directory)
- `.` - Current directory
- `..` - Parent directory (one level up)

---

## Essential Commands

### Navigation
```bash
pwd                    # Print working directory - shows where you are
cd path/to/directory   # Change directory
cd ~                   # Go to home directory
cd ..                  # Go up one directory level
ls                     # List files and directories in current folder
ls -la                 # Detailed list with hidden files (files starting with .)
```

### File Operations
```bash
touch filename.txt           # Create an empty file
mkdir foldername             # Create a directory
rm filename.txt              # Delete a file (WARNING: permanent!)
rm -r foldername             # Delete a directory and all contents
cp source.txt dest.txt       # Copy a file
cp -r source_dir dest_dir    # Copy a directory
mv oldname.txt newname.txt   # Rename or move a file
```

### Viewing Files
```bash
cat filename.txt             # Display entire file contents
less filename.txt            # View file page by page (press q to quit)
head -n 5 filename.txt       # Show first 5 lines
tail -n 5 filename.txt       # Show last 5 lines
```

### Searching
```bash
grep "search_term" filename.txt    # Find lines containing text
find . -name "*.py"                # Find all Python files in current directory
```

### Useful Utilities
```bash
echo "Hello"              # Print text
man command_name         # Show manual for a command (press q to quit)
whoami                   # Show current user
date                     # Show current date and time
clear                    # Clear the screen
history                  # Show command history
```

---

## Pipes and Redirection

Pipes chain commands together:
```bash
ls -la | grep ".py"      # List files, then filter for .py files
cat file.txt | head -n 5 # Show first 5 lines of file
```

Redirection sends output to files:
```bash
ls > files.txt           # Save output to file (overwrites)
ls >> files.txt          # Append output to file
cat < input.txt          # Use file as input
```

---

## Wildcards and Patterns

```bash
*.txt         # All files ending with .txt
file?.txt     # file1.txt, file2.txt, etc. (? = any single character)
test*         # Any file starting with "test"
```

---

## Environment Variables

```bash
echo $PATH               # Show search paths for commands
echo $HOME               # Show home directory path
export VAR_NAME="value"  # Set a variable
```

---

## Common Workflows

### Create and navigate to a project
```bash
mkdir my_project
cd my_project
pwd
```

### List and examine files
```bash
ls -la
cat README.md
head config.json
```

### Create multiple files
```bash
touch file1.py file2.py file3.py
```

### Move back through directories
```bash
cd ..
cd ../..
```

---

## Tips & Tricks

- **Tab completion**: Press Tab to auto-complete paths and commands
- **Arrow keys**: Use up/down arrows to navigate command history
- **Ctrl+C**: Stop a running command
- **Ctrl+L**: Clear the screen (alternative to `clear`)
- **Command history**: Type `!` followed by letters to run recent commands (e.g., `!ls` runs last `ls` command)

---

## Practice Exercises

1. Navigate to your home directory and list all contents with details
2. Create a folder structure: `projects/python/practice`
3. Create files: `README.md`, `script.py`, `config.json`
4. View the contents of one file
5. Copy a file to a new location
6. Find all `.py` files in your current directory
7. Use pipes to count lines in a file: `wc -l < filename.txt`

---

## Windows-Specific Notes

- **Git Bash**: Provides Unix-like commands on Windows
- **PowerShell**: Windows native shell (similar concepts, different syntax)
- **Path separator**: Unix uses `/`, Windows uses `\` (but Git Bash uses `/`)
- **Drives**: Access C: drive with `/c/` in Git Bash (e.g., `/c/Users/YourName`)

