# Multi-Process Command Pipeline System

## Overview

The Multi-Process Command Pipeline System is a Linux-based project developed using the C programming language. It demonstrates **inter-process communication (IPC)** by executing two Linux commands as separate child processes and transferring the output of the first command to the input of the second command using a pipe.

The project illustrates how Linux processes can communicate with each other and how system calls such as `fork()`, `pipe()`, `dup2()`, `exec()`, and `wait()` are used in process management.

## Problem Statement

To design and implement a Multi-Process Command Pipeline System that accepts two commands, executes them as separate stages, and passes the output of the first stage as the input of the second through a pipe. The system demonstrates inter-process communication between processes in Linux.

## Objectives

- Accept two Linux commands from the user.
- Create child processes using `fork()`.
- Establish a communication channel using `pipe()`.
- Redirect standard output and standard input using `dup2()`.
- Execute commands using `execlp()`.
- Synchronize the parent process using `wait()`.
- Demonstrate how output flows from one process to another.

## Technologies Used

- **Programming Language:** C
- **Operating System:** Linux / Ubuntu
- **Concepts:** Process Management, Inter-Process Communication (IPC), Pipes, File Descriptors, Command Execution

## System Workflow

1. The user enters the first and second Linux commands.
2. The program creates a pipe for communication.
3. The first child process executes the first command and sends its standard output into the pipe.
4. The second child process reads from the pipe as its standard input and executes the second command.
5. The parent process closes its unused pipe descriptors and waits for both child processes to finish.

### Architecture

```text
          User Input
               |
       Two Linux Commands
               |
          Parent Process
               |
          Create Pipe
               |
        -----------------
        |               |
   Child Process 1  Child Process 2
        |               ^
    First Command       |
        |               |
    Standard Output     |
        |               |
        +---- PIPE -----+
                        |
                  Standard Input
                        |
                  Second Command
                        |
                   Final Output
```

## System Calls Used

| System Call | Purpose |
|---|---|
| `pipe()` | Creates a communication channel between processes. |
| `fork()` | Creates a child process. |
| `dup2()` | Redirects standard input or output to a pipe. |
| `execlp()` | Executes a command through the Linux shell. |
| `close()` | Closes unused file descriptors. |
| `wait()` | Waits for child processes to finish. |

## How to Run the Project



###  Compile the C Program

If your source file is named `pipeline.c`, run:

```bash
gcc pipeline.c 
```

###  Execute the Program

```bash
./a.out
```

###  Enter Commands

Example:

```text
Enter first command: ls
Enter second command: wc -l
```

The output of `ls` is passed through the pipe to `wc -l`, which counts the lines it receives

website link:
 https://vishnupriya-255.github.io/os_hackathon_Multi-Process-Command-Pipeline-System/
