# Man Page

> *What is a man page? Why is it useful? For what purpose does it serve?*

This document is to provide a short (but not really short 눈_눈) tutorial/reference as to what a man page is and how to use it. Consider the man page as a mini-Google of the terminal. You can find information on commands, functions, and other programming related topics within your terminal without the use of the internet ( ᐛ )و. This way, if you were at a wifi-less location coding with **VIM** (like you're supposed to), you can use the man page to reference your needs. 

Since this is meant to be a tutorial/reference of the man page, I tried to make it ~~long~~ short as possible. However, never fear for the **TOC** is here:

### Table of Contents
1. [Introduction](#introduction)
2. [Sections](#sections)
3. [Layout](#layout)
4. [Executing](#executing)
	* [Pages](#id-pages)
	* [Flags](#id-flags)
5. [Navigating](#navigating)

### Introduction

> So what is the man page (•᷄ὤ•᷅)? Well...

Short for **manual page**, the **man page** is a software documentation normally found on a Unix or Unix-based operating system. Topics covered by the man page is split into eight sections, organized accordingly based on the operating system. By default, the man page uses a *terminal pager* program such as `more` or `less` to display its output. 

In case you're in dire need of definitions:

<dl>
	<dt>more:</dt> 
	<dd>A program to view (not edit) the contents of a text file one screen at a time.</dd>

	<dt>more:</dt> 
	<dd>A program to view (not edit) the contents of a text file one screen at a time.</dd>

	<dt>less:</dt> 
	<dd>A program with the capabilities of allowing both forward and backward navigation through the file.</dd>
</dl>

### Sections

The man page generally consists of eight sections (listed below). There are four other available sections and unfortunately, these additional four are only avaible on some systems so you may or may not be able to access them.

> The section order provided is accurate for **Research Unix**, **BSD**, **OS X**, and **Linux**.

Section | Topics
--------| -------
1 | General commands
2 | System calls
3 | Library functions (mainly the *C standard library*)
4 | Special files and drivers
5 | File format and conventions
6 | Games and screensavers
7 | Miscellanea
8 | System administration commands and daemons

##### Descriptions/notes about each topic:

> ...for those that want a little more reading in their life  ʅ(‾◡◝)ʃ 

1. **Command** is a directive to a computer program acting as an interpreter in order to perform a specific task.
	* Ex: `ls`, `cd`, `echo` are known commands
2. **System call** is the programmatic way in which a computer program requests a service from the kernel of the operating system it is executed on.
	* Ex: `open`, `kill`, `exit` are known system calls
3. **Library** is a collection of non-volatile resources used by programs to develop software.
	* Ex: `iostream` and `string` are library functions of the C standard library
4. **Special file** is an interface for a device driver that appears in a file system as if it were an ordinary file. **Driver** is a program that operates or control a type of device attached to a computer. 
5. **File format** is a standard way that information is encoded for storage in a computer file. 
	* Ex: `.cpp`, `.h`, `.txt` are common file formats in C++ programming
6. This section describes all the **games** that are available on the system and provide command line tools for controlling the **screensaver**. 
7. As implied. 
8. **Daemon** is a computer program that runs as a background process rather than being under the direct control of an inactive user. 
	* Ex: `sshd` is a daemond that services incoming SSH connections

**Note:** 

- There is a **Unix System V**, originally developed by AT&T 1983, that is similar to this but is listed in a different order. 
- The additional four section number/name are:

Section | Topics
--------| ---------------
0 | C library header files
9 | Kernel routines
n | Tcl/Tk keywords
x | The X Window System

### Layout:

> It's important to know how the page is organized before you execute the man command. This way, not only will you know what to expect but it can be easier for you to navigate through the page when you know what you're looking for. On the bright side, you are almost done with the tutorial ✧*｡٩(ˊᗜˋ*)و✧*｡. 

Each section, or page, of the man page follow a set layout, optimized for presentation on an ASCII text display without any form of highlighting or font control (bold and underline is common however). The standard layout of a page would look similar to this:

<dl>
	<dt>NAME</dt>
	<dd>The name of the command or function, followed by a one-line description of what it does.</dd>

	<dt>SYPNOPSIS</dt>
	<dd>For commands, a formal description of how to run it and what command line option (like flags) it takes.</dd>
	<dd>For functions, a list of parameters the function takes and which header file contains its definition</dd>

	<dt>DESCRIPTION</dt>
	<dd>A description of the functioning of the command or function.</dd>

	<dt>EXAMPLES</dt>
	<dd>Examples of how the command or function is commonly used.</dd>

	<dt>SEE ALSO</dt>
	<dd>List related commands or functions pertaining to the command or function.</dd>
</dl>

> Note: Other sections including OPTIONS, EXIT STATUS, RETURN VALUES, ENVIRONMENT, BUGS, FILES, AUTHOR, REPORTING BUGS, HISTORY, and COPYRIGHT may be present in the page as well depending on the command/function description. There is also the case where some of these sections may replace the standard sections. A good example is *syscall* where it has RETURN VALUE in place of EXAMPLE.

### Executing:

> Executing and exiting the man page is fairly simple. Like any command, its flags can be difficult to remember since there's always so many. Luckily only the basic few will be covered today so you can slowly *stache* some questions away (´┏･┓｀).

A few things to note before starting:

1. Keep in mind the set layout of the page when you use the man command.
	* You can compare the similarities each page has with each other. 
2. The man is a manual so it is very unlikely for it to contain source codes for examples.  
3. Similar to the **VIM**, you can *exit the man page by typing q*. 
	* There are a few VIM commands that will work on the man page. However, that's in a later section.

The basic format to read a manual page for a Unix command is:
	
	$ man <command_name>

The longer format to read a manual page is:
	
	$ man <section_#> <command name>

The latter is unecessary since both will produce the same result. For example, type this on the terminal:

	$ man ls

Type q to exit then try this:

	$ man 1 ls

Type q to exit and notice how both method produced the same result. Now type this into the terminal:
	
	$ man 2 ls

You should have gotten something similar to this as an error message:
	
	No entry for ls in section 2 of the manual

This is because even though `ls` is a legal command, it belongs in section 1 of the man page ([Sections] (#sections)). When you specify the section number, `man` will only look at that section of the manual, ignoring every other section.  

<div id="id-pages"/>
**Pages:**

> This is a fun fact ಠ_ಠ. If you're ever feeling lazy and/or curious, there is a way to check the section number of the command. 

Traditionally, pages in the man page are referred to using the notation **name(section)**. For example, 

	echo(1) is the same as "man echo" which is the same as "man 1 echo" 

If you have seen that format before but didn't know what it meant, you now know what it means. Additionally, you can also find it in the upper left corner in every page in `man`.

<div id="id-flags"/>
**Flags:**

Like any program, flags can be useful for providing more/new information to the user. The man page has its own set of flags, most of it you will probably never use and some of it you will find useful for knowing. We will only cover five here. 

<dl>
	<dt>-a</dt>
	<dd>Forces <b>man</b> to display all the manual pages that matches the command and not just the first.</dd>
</dl>
-------

Type this into the terminal then type q:

	$ man exit

Notice how this automatically exits the man page. In truth, there are three pages relating to **exit** in the man page. However, you wouldn't know that it had existed since, by default, `man` will exit after finding and displaying the first page of the command. Now retype it but with the **-a** flag and exit: 

	$ man -a exit

Notice how you're still in `man` but at a different page. You should have gone from BUILTIN(1) to EXIT(3) to exit(n) before you've fully exited `man`.

--------

<dl>
	<dt>-h</dt>
	<dd>Print a help message and exit</dd>
</dl>
-------

Type this into the terminal:

	$ man -h

You should obtain something like this:

![alt text](https://github.com/genjen123/Tutorial/blob/master/Images/-h%20flag.png "-h flag")

Conveniently, the man page provides you its list of flags and its respective description as well as the version number of your `man` (｡•̀ᴗ-)✧. So, if you ever forget a flag or want to test out new ones, you can always use **-h**.

--------

<dl>
	<dt>-f</dt>
	<dd>Seach the man page for the given word and provide a brief description of it.</dd>
</dl>
-------

Try something basic like `fork`:

	$ man -f fork

You should get this short description:

![alt text](https://github.com/genjen123/Tutorial/blob/master/Images/-f%20fork.png "-f flag") 

Now do the same thing but with `echo`. Your result should have produced something like this:

![alt text](https://github.com/genjen123/Tutorial/blob/master/Images/-f%20echo.png "-f flag")

> [Excuse the dark overlay on the right. That's just my soul caught in the picture |‿ʘ)]

Notice how the pages of where `echo` is found is listed before its functionality description. 

-------

<dl>
	<dt>-k</dt>
	<dd>Seach for the specified string in the man pages and displays the result on the standard output.</dd>
</dl>
-------

Reusing `fork` as an example:

	$ man -k fork

If you've noticed, the list has increased by 1 (ﾉ^ヮ^)ﾉ:・ﾟ✧. If you do the same with `echo`, you'll notice that the list has increased by 3. In cause you're wondering why **-f** and **-k** is different even though its output is similar, here it is:

	-f : displays a man page description to give you a general idea of what a command does

	-k : searches the man page to help you learn which functions to use to perform a job

Simply put, **-f** is like the definition while **-k** is like the dictionary. 

-------

<dl>
	<dt>-K</dt>
	<dd>Seach for the specified string in <i>all</i> man pages.</dd>
</dl>
-------

Consider this as an upgrade of the **-k** flag. Since **-K** goes through all pages for the specified string, it's best to use it with a section number or the program can run very slow. 

Again, let's use `fork` again as an example. 
	
	$ man -K fork

Firstly, notice how long the first line took to appear. When it does, you should see something like this at the end of the line: **[ynq]**. 

	y - yes
	n - no
	q - quit

> The program is simply asking if you want to read that page or not. Typing **y** then ENTER will open the page, **n** then ENTER will find and load the next page, and **q** and ENTER will exit the search.

Here is a visual example:

![alt text](https://github.com/genjen123/Tutorial/blob/master/Images/-K%20fork.png "-K flag")

As mentioned before, this flag is best used with a section number. Since we know that `fork` is in section 2, type in the command and checkout the difference in result:

	$ man 2 -K fork

The program runs a lot faster when the section number is included doesn't it? That's because by setting the section number, you are telling `man` to check the string only in the pages of that section.

### Navigating:

> Knowing how to navigate through a page in the man page is especially important for saving time. Anyone who has seen a long man page will agree that this is crucial to stopping future headaches ʘ‿ʘ.

Depending on what you are searching for, the man page can range from being short to bearable to ridiculously long. You can test the difference in length yourself to see how long a page can extend. 

Type this into your terminal for a short length man page:
	
	$ man pwd

Now, checkout the bearable-level length:
	
	$ man man

Finally, the ridiculously long page length: 

	$ man bash

How long did it take you to scroll down to the bottom of the page in that last command? Surely it was very bash-specific ≖‿≖. As you can see, these man pages can become very long and can be tiring to read through. However, if you know exactly what you want to find, it's a lot faster to directly navigate there rather than scrolling through the whole page. 

In case you forgot, many scrolls ago, in the [Introduction] (#introduction) section, there was the `less` program (ʘᗩʘ’). Now this `less` program is used by the man page to allow both forward and backward navigation. You may have noticed by now, the `less` commands are similar to the **VIM** editor. So if you've forgotten your VIM commands, this is a good chance to relearn some of it. 

Let's try a new page this time. Ready your terminal and type this in:

	$ man waitpid

Now `waitpid` is a fairly lenghty page so it'll be a good example for this section. Below is your friendly commands **cheat sheet**. You should try some of these out to get the feel of it. 

	To find a word/pattern:
		/ : search for a pattern starting from the next occurrence
		? : search for a pattern starting from the previous occurence
		n : finds next match (find next)
		N : finds the previous match (find previous)

	To switch pages:
		CTRL+F or SPACE : page down
		CTRL+B : page ups
		g : move to first line of page
		G : move to last line of page

	To navigate through each line:
		j : move one line down
		k : move one line up
		CTRL+G : show the current lines, byte, and percentage statistics

> Note: Just like **VIM**, numbers before a command will work as well. For example, **45G** will start the page at the 45th line. 

------

That's it. That's the end of the man page tutorial. You've learned the basics of what you needed to know about the `man page`. Congratulations! ヽ(＾▽＾)人(＾▽＾)人(＾▽＾)ﾉ










