# Linux

- [Linux](#linux)
  - [Bash Shell Scripting](#bash-shell-scripting)
    - [Creating a shell script to provision an nginx web server](#creating-a-shell-script-to-provision-an-nginx-web-server)
      - [Update](#update)
      - [Upgrade](#upgrade)
      - [Install Nginx](#install-nginx)
      - [Start the Nginx service](#start-the-nginx-service)
      - [Check nginx status](#check-nginx-status)
      - [Restart Nginx](#restart-nginx)
      - [Enable Nginx](#enable-nginx)
    - [Creating a custom nginx webpage](#creating-a-custom-nginx-webpage)
      - [Backup the Default Nginx Webpage](#backup-the-default-nginx-webpage)
      - [Replace the default nginx webpage](#replace-the-default-nginx-webpage)
      - [Download image onto the VM](#download-image-onto-the-vm)
      - [Add image to the nginx webpage](#add-image-to-the-nginx-webpage)
    - [Executing the bash script](#executing-the-bash-script)
  - [Additional Linux](#additional-linux)
    - [Commands](#commands)
    - [Environment Variables](#environment-variables)
    - [Piping](#piping)
    - [File Permissions](#file-permissions)
    - [Processes](#processes)
      - [Introduction](#introduction)
      - [What Is a Process?](#what-is-a-process)
      - [Types of Processes](#types-of-processes)
      - [Process Lifecycle](#process-lifecycle)
      - [Managing Processes](#managing-processes)
        - [1. Viewing Processes](#1-viewing-processes)
        - [2. Stoppling/Killing Processes](#2-stopplingkilling-processes)
        - [3. Controlling Processes](#3-controlling-processes)
      - [Key Process Attributes](#key-process-attributes)
      - [States of a Process](#states-of-a-process)
      - [Important Commands for Processes](#important-commands-for-processes)

## Bash Shell Scripting

### Creating a shell script to provision an nginx web server

#### Update

- To fetch latest package list using apt package manager:

```bash
sudo apt update
```

#### Upgrade

- To install the latest package list fetched from update command:

```bash
sudo apt upgrade -y
```

#### Install Nginx

- To install nginx web server:

```bash
sudo apt install nginx
```

#### Start the Nginx service

```bash
sudo systemctl start nginx
```

#### Check nginx status

- To view nginx PID:
  
```bash
sudo systemctl status nginx
```

#### Restart Nginx

- After making any changes to Nginx, need to restart it to activate the changes:

```bash
sudo systemctl restart nginx
```

#### Enable Nginx

- Enabling Nginx refers to automatically turning nginx on whenever the VM itself is turned on:

```bash
sudo systemctl enable nginx"
```

### Creating a custom nginx webpage

#### Backup the Default Nginx Webpage

- The webpage is a html file stored in:
  
```bash
/var/www/html
```

- To backup the webpage you need to create a copy of the file:

```bash
e.g. sudo cp index.html index.html.bak
```

#### Replace the default nginx webpage

- You can amend the contents of the `index.html` file to change the content and layout of the default nginx webpage.
- In my case, I changed it to "welcome to my custom webpage!" greeting, with a farewell message at the end.

#### Download image onto the VM

- cd into the html directory
- Download image onto the VM using wget command

```bash
cd /var/www/html
wget https://example_image.com/path-to-your-image.jpg
```

#### Add image to the nginx webpage

- edit the `index.html` file:

```bash
sudo nano /var/www/html/index.html
```

```html
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
    body {
        width: 35em;
        margin: 0 auto;
        font-family: Tahoma, Verdana, Arial, sans-serif;
    }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```

- add the following image tag inside the body section:

```html
<img src="downloaded_image_name.jpg" alt="My Image" width="500">
```

```html
<!DOCTYPE html>
<html>
<head>
<title>Sameem's Custom Webpage!</title>
<style>
    body {
        width: 35em;
        margin: 0 auto;
        font-family: Tahoma, Verdana, Arial, sans-serif;
    }
</style>
</head>
<body>
<h1>Welcome to my custom webpage!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>
<img src="NGINX-logo-rgb-large-667x224.png" alt="My Image" width="500">
<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thanks for visiting. Take care!.</em></p>
</body>
</html>
```

- save and exit the file. Refresh the page in your browser. It should display the custom content and the downloaded image.

### Executing the bash script

- Give execute permission to the script.

```bash
chmod +x /home/adminsuer/provision.sh
```

- Run the script.

```bash
./provision.sh
```

## Additional Linux

### Commands

- **mv**: Renames or moves files.
  - `mv cat.jpg cat.txt`: Renames `cat.jpg` to `cat.txt`.
  - `mv filename existingFolderName`: Moves a file to a different folder.
  - `mv chicken-joke.txt /home/adminuser/`: Moves a file to the home directory.
  - `mv /home/adminuser/funny-stuff/chicken-joke.txt ~`: Moves a file using full paths.

- **file**: Shows file details (e.g., type).
  - `file cat.jpg`: Displays details about `cat.jpg`.

- **rm**: Deletes files.
  - `rm filename`: Deletes a file.
  - `rm -r directory`: Removes a directory and its contents.
  - `rm -rf directory`: Forcefully deletes a directory and its contents.

- **mkdir**: Creates a folder.
  - `mkdir folderName`: Creates a new folder.
  - Use quotes for folder names with spaces: `mkdir "my pictures"`.

- **rmdir**: Removes an empty directory.
  - `rmdir directory`: Removes an empty directory.

- **touch**: Creates an empty file.
  - `touch filename`: Creates a new empty file.

- **cat**: Displays file contents.
  - `cat filename`: Dumps the contents of a file to the screen.

- **nano**: Opens a file editor.
  - `nano filename`: Opens a file in the nano editor.

- **head**: Displays the first lines of a file.
  - `head -2 filename`: Shows the first 2 lines of a file.

- **tail**: Displays the last lines of a file.
  - `tail -2 filename`: Shows the last 2 lines of a file.

- **nl**: Numbers all lines of a file.
  - `nl filename`: Displays the file with line numbers.

- **grep**: Searches for a specific word in a file.
  - `cat filename | grep word`: Filters the file for specific information.
  - `grep -r word directory`: Recursively searches for a word in files within a directory.

- **tree**: Displays folder and file structure.
  - `sudo apt install tree`: Installs the tree command.
  - `tree`: Shows the structure of files and folders.

- **sudo !!**: Re-runs the previous command with sudo.
  - `sudo !!`: Runs the last command with root permissions.

- **sudo su**: Switches to the root user.
  - `sudo su`: Gains root user access to run multiple commands with root permissions.

- **>>**: Appends to files.
  - `echo "text" >> filename`: Appends text to a file.

### Environment Variables

- **Definition**: Environment variables are dynamic values that affect the processes or programs on a computer. They can store information such as the system path, the current user, and other system settings.

- **Common Commands**:
  - **View Environment Variables**:
    - `printenv`: Displays all environment variables.
    - `echo $VARIABLE_NAME`: Displays the value of a specific environment variable.
  - **Set Environment Variables**:
    - `export VARIABLE_NAME=value`: Sets a new environment variable or updates an existing one for the current session.
  - **Persistent Environment Variables**:
    - Add the `export VARIABLE_NAME=value` line to your shell configuration file (e.g., `~/.bashrc`, `~/.bash_profile`, `~/.zshrc`) to make it persistent across sessions.

- **Examples**:
  - `echo $HOME`: Displays the home directory of the current user.
  - `export PATH=$PATH:/new/path`: Adds a new directory to the existing PATH variable.
  - `export MY_VAR="Hello World"`: Sets a new environment variable `MY_VAR` with the value "Hello World".

- **Usage**:
  - Environment variables are used to configure the behavior of the shell and applications.
  - They can be accessed and modified to customize the user environment.

### Piping

- **Definition**: Piping is a method used to pass the output of one command as input to another command. It allows for the chaining of commands to perform complex tasks efficiently.

- **Syntax**:
  - `command1 | command2`: The output of `command1` is used as the input for `command2`.

- **Common Uses**:
  - **Combining Commands**:
    - `ls -l | grep "txt"`: Lists detailed information of files and filters for those containing "txt".
  - **Filtering Output**:
    - `cat file.txt | grep "search_term"`: Displays lines in `file.txt` that contain "search_term".
  - **Counting Lines**:
    - `cat file.txt | wc -l`: Counts the number of lines in `file.txt`.
  - **Sorting Output**:
    - `cat file.txt | sort`: Sorts the contents of `file.txt`.

- **Examples**:
  - `ps aux | grep "process_name"`: Lists all running processes and filters for "process_name".
  - `dmesg | less`: Displays kernel messages and allows for scrolling through them.
  - `cat file.txt | awk '{print $1}'`: Prints the first column of each line in `file.txt`.

- **Usage**:
  - Piping is used to create powerful command combinations that can process and manipulate data in various ways.
  - It enhances the functionality of individual commands by allowing them to work together.
  
### File Permissions

- **Definition**: File permissions determine the actions that users can perform on a file or directory. Permissions are set for the owner, group, and others.

- **Permission Types**:
  - **Read (r)**: Allows viewing the contents of a file or listing a directory's contents.
  - **Write (w)**: Allows modifying the contents of a file or adding/removing files in a directory.
  - **Execute (x)**: Allows executing a file (if it's a script or program) or accessing a directory.

- **Viewing Permissions**:
  - `ls -l`: Lists files and directories with their permissions.
    - Example output: `-rwxr-xr-- 1 user group 4096 Jan 1 12:34 file.txt`
      - `-rwxr-xr--`: Indicates the permissions for the owner, group, and others.

- **Changing Permissions**:
  - `chmod`: Changes the permissions of a file or directory.
    - **Symbolic Mode**:
      - `chmod u+x file.txt`: Adds execute permission for the owner.
      - `chmod g-w file.txt`: Removes write permission for the group.
      - `chmod o+r file.txt`: Adds read permission for others.
    - **Numeric Mode**:
      - `chmod 755 file.txt`: Sets permissions to `rwxr-xr-x`.
      - `chmod 644 file.txt`: Sets permissions to `rw-r--r--`.

- **Changing Ownership**:
  - `chown`: Changes the owner and group of a file or directory.
    - `chown user:group file.txt`: Changes the owner to `user` and the group to `group`.

- **Examples**:
  - `chmod +x script.sh`: Makes `script.sh` executable.
  - `chmod 600 private.txt`: Sets permissions to `rw-------` (owner can read and write).
  - `chown admin:admin config.cfg`: Changes the owner and group of `config.cfg` to `admin`.

- **Usage**:
  - File permissions are crucial for system security and proper access control.
  - They ensure that only authorized users can perform specific actions on files and directories.

### Processes

#### Introduction

- In Linux, a process is a running instance of a program. It represents the execution of a program in the system's memory, complete with its allocated resources (e.g., CPU, memory, and I/O).

- Processes are at the core of Linux operations, and understanding how to manage them is critical for system administration and DevOps tasks.

#### What Is a Process?

- A process is a program in execution.

- Every process has:
  - Unique ID: Called the Process ID (PID).
  - Parent Process: The process that started it (Parent Process ID or PPID).
  - State: Indicates whether the process is running, sleeping, stopped, or terminated.

#### Types of Processes

1. Foreground Processes
   - Run directly from the terminal and occupy the terminal until they finish.
   - Example: Running python my_script.py.

2. Background Processes
   - Run independently of the terminal and do not block user input.
   - Example: Running ./my_program &.

3. Daemon Processes
   - Background processes that run without user interaction, often started during system boot.
   - Example: sshd (Secure Shell Daemon).

#### Process Lifecycle

A process typically follows these steps:

1. Creation:

   - Created by another process using the fork() system call.
   - Example: The shell creates a new process when you run a command.

2. Execution:

   - Executes the program with its allocated resources.

3. Waiting:

   - A process may wait for I/O or other resources.

4. Termination:

   - Ends its execution and releases resources using the exit() system call.

#### Managing Processes

##### 1. Viewing Processes

- Use commands to see running processes:
  - `ps`: Displays active processes.
  - `top` or `htop`: Interactive tools to monitor processes in real time.
  - `pgrep <name>`: Find the PID of a process by name.

##### 2. Stoppling/Killing Processes

- 3 main levels for `kill` as below:

| Signal Name | Signal Number | Command       | Purpose                        |
|-------------|---------------|---------------|--------------------------------|
| SIGTERM     | 15            | `kill <PID>`    | Graceful termination.          |
| SIGKILL     | 9             | `kill -9 <PID>` | Immediate/forced termination.  |
| SIGHUP      | 1             | `kill -1 <PID>` | Reload configuration/restart.  |

- `killall <name>`: Kills all processes by name.

##### 3. Controlling Processes

- Pause a Process: `kill -STOP <PID>`
- Resume a Process: `kill -CONT <PID>`
- Move a Foreground Process to the Background:
  - Press `Ctrl+Z` to pause, then type `bg` to resume it in the background.

#### Key Process Attributes

- **PID**: Process ID (unique identifier for a process).
- **PPID**: Parent Process ID (the PID of the process that created it).
- **UID/GID**: User ID and Group ID that own the process.
- **Priority**: Determines how much CPU time a process gets (controlled with `nice` and `renice`).

#### States of a Process

- **Running (R)**: Actively using the CPU.
- **Sleeping (S)**: Waiting for a resource (e.g., I/O or user input).
- **Stopped (T)**: Suspended, often by a signal like SIGSTOP.
- **Zombie (Z)**: Completed execution but still listed in the process table because its parent hasn’t read its exit status.

#### Important Commands for Processes

| Command        | Description                                   |
|----------------|-----------------------------------------------|
| `ps`           | Displays a snapshot of currently running processes. |
| `top`          | Interactive tool to monitor system performance and processes in real-time. |
| `htop`         | User-friendly version of `top` with a better interface. |
| `pgrep`        | Finds the process ID (PID) by matching the process name. |
| `kill`         | Sends a signal to terminate or control a process by its PID. |
| `killall`      | Sends a signal to all processes matching a specific name. |
| `jobs`         | Lists background jobs in the current shell session. |
| `fg`           | Brings a background job to the foreground.          |
| `bg`           | Resumes a paused job and runs it in the background. |
| `nice`         | Starts a process with a specific priority.          |
| `renice`       | Changes the priority of a running process.          |
| `pkill`        | Sends a signal to terminate processes by name.      |
| `nohup`        | Runs a process that continues after the terminal is closed. |
| `systemctl`    | Starts, stops, enables, or disables services (for systemd). |
| `service`      | Manages services for older init systems.            |
| `strace`       | Traces system calls and signals for a process (useful for debugging). |
| `lsof`         | Lists open files by processes.                      |
| `free`         | Displays memory usage information.                  |
| `uptime`       | Shows how long the system has been running and load averages. |
