---
title: What is a shell? 🐚
date: 2021-01-25 11:58:47 +07:00
modified: 2021-02-02 16:49:47 +07:00
tags: [unix/linux, cli]
description: Before the existence of GUI, the way users interacted with computers using CLI was typing command lines on an interface in the form of text lines such as.
image: "/apa-itu-shell/shell_evolution.png"
---

<a href="http://www.youtube.com/watch?v=tc4ROCJYbm0&t=70" target="_blank" rel="noopener">Dulu</a> Sebelum adanya <abbr title="Graphical User Interface">GUI</abbr> how users interact with computers using <abbr title="Command Line Interface">CLI</abbr> typing command lines on an interface in the form of lines of text such as 👇.

<figure>
<img src="/apa-itu-shell/terminal_nginx.gif" alt="installing nginx in ubuntu">
<figcaption>Fig 1. Terminal emulator, package installation and check service.</figcaption>
</figure>

If you have ever used unix/linux, you may have used the above program, maybe even use it every day to execute a command through <a href="http://en.wikipedia.org/wiki/List_of_terminal_emulators" target="_blank" rel="noopener">terminal emulator</a>.

User<sup id="user">[[1]](#user-ref)</sup> cannot directly communicate with a computer hardware, therefore we need an operating system; **Kernel** is a program that is the main core of a computer operating system.

<figure>
<img src="/apa-itu-shell/kernel.png" alt="kernel central of operating system">
<figcaption>Fig 2. kernel chart.</figcaption>
</figure>

The kernel facilitates the interaction between hardware and software components, its role is to handle input/output requests from software, then translate them into data processing to be instructed to the CPU, so that Hardware (cpu, memory, devices) understands the intended command from the user.

When we input a command on the terminal emulator, the kernel does not immediately understand the command we type, we need an interface as an intermediary to the kernel, namely **Shell**.

<figure>
<img src="/apa-itu-shell/shell.png" alt="shell">
<figcaption>Fig 3. shell communication chart.</figcaption>
</figure>

<mark>Shell is a command-line interpreter; a program that acts as a translator of commands inputted by the user through the terminal.</mark>, so that the command can be understood by the Kernel.

The login shell is usually set by the local System Administrator when your user is first created, you can see the login shell that you are using with the command below.

```bash
$ echo $SHELL
# atau
$ echo $0
```

Every shell has a default prompt. some of the most common shells:

```bash
$ (dollar sign)   # sh, ksh, bash
% (percent sign)  # csh, tcsh
```

##### Shell prompt terminology

The shell prompt is where we write a command, here is the terminology this helps, if you want to know the parts.

<figure>
<img src="/apa-itu-shell/term_shell_prompt.png" alt="shell">
<figcaption>Fig 4. parts of the shell prompt.</figcaption>
</figure>

Below is an example of a simple command to display a CPU architecture of the computer I am using.

<figure>
<img src="/apa-itu-shell/terminal_lscpu.gif" alt="installing nginx in ubuntu">
<figcaption>Fig 5. displays information about the CPU architecture.</figcaption>
</figure>

From the command example, when the user types a command input in the terminal and presses <kbd>ENTER</kbd>, then the shell will convert user commands into a language that can be understood by the kernel, and the Kernel translates it into data processing to be instructed to the Hardware so as to produce output in accordance with user commands.

Shell has several kinds and derivatives, here are the most common ones.

<figure>
<img src="/apa-itu-shell/shell_evolution.png" alt="shell evolution">
<figcaption>Fig 6. shell evaluation from year to year.</figcaption>
</figure>

A little explanation of the picture above.

- Bourne shell `sh`
  Developed by Stephen Bourne at Bell Labs, then a replacement for the Thompson shell (created by Ken Thompson), many unix-like systems still have `/bin/sh` - which becomes a symbolic link or hard link, even when other shells are used but `sh` is the base, for command compatibility.
- Korn shell `ksh` Unix shell developed by David Korn at Bell Labs,
  It was originally developed based on the Bourne shell source code, but it also features `csh` and `sh`, the development of which is continuing as I write this. <a href="http://github.com/att/ast" target="_blank" rel="noopener">manicured</a>.
- Bourne again shell `bash`
  This project is open source <a href="http://gnu.org/software/bash/" target="_blank" rel="noopener">GNU project</a> It is compatible with `sh` which combines important features of `ksh` and `csh`, and is becoming one of the most commonly used shells (generally being the default login shell of Linux and Apple's macOS Mojave).
- This `zsh` shell has its own community platform called <a href="http://ohmyz.sh/"  target="_blank" rel="noopener">"Oh My Zsh"</a>, `zsh` plug-ins and themes can be found in this community, I am currently using `zsh`, this shell is also the default of the macOS Catalina operating system, which replaces bash.
- friendly interactive shell `fish`
  well in accordance with <a href="http://fishshell.com/" target="_blank" rel="noopener">Description</a> on the web, I think this shell is really fun, the features I like about this shell are autosuggestions, and easy configuration via web-based.

There is still a lot that has not been explained in this article if you are still interested, read more <a href="http://en.wikipedia.org/wiki/List_of_command-line_interpreters#Operating_system_shells" target="_blank" rel="noopener">many</a> and also <a href="http://en.wikipedia.org/wiki/Comparison_of_command_shells" target="_blank" rel="noopener">Comparison</a> each shell.

If you are interested in changing the default login shell on the operating system, you can install it by following the documentation / installation method in each shell here I do not discuss because the distro we use may vary.

To make the default login shell on the OS you can use this command.

```bash
# command
$ sudo chsh [options] [LOGIN]

# contoh penggunaan
$ sudo chsh -s /user/bin/zsh harpi
# mengubah default shell user harpi menjadi zsh shell.
$ reboot

# atau kamu juga bisa mengubah file /etc/passwd dan edit secara manual user shellnya.
# jika masih bingung manfaatkan perintah man untuk melihat manual page.
$ man chsh
```

Lastly for this article, shells have various kinds, choose the shell that suits you to support productivity and adjust to your needs, too many plugins and confusion about choosing a theme is bad 😁.

Thank you for reading, _the author welcomes criticism and suggestions._

##### Notes

<small id="user-ref"><sup>[[1]](#user)</sup> Humans who operate and control the computer system.</small>

##### Resources

- [Evolution shells in Linux](http://developer.ibm.com/tutorials/l-linux-shells/)
- [Kernel Defintion](http://www.linfo.org/kernel.html)
- [The Shell](http://www.cis.rit.edu/class/simg211/unixintro/Shell.html)
