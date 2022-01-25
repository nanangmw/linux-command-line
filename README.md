# Linux

### UNIX
Linux is considered a Unix-like operating system which basically means that Linux derives heavy inspiration from Unix without actually conforming to be a full Unix operating system. macOS and FreeBSD would be two more examples of a Unix-like operating system.

### Linux
Linux isn't directly Unix, just directly inspired by it, and incorporates many of its ideas and interfaces into it. It was created in 1991 by Linus Torvalds who is still an influential figure today and still runs the Linux project. He created Linux because at the time there was no single free, open-source reimplementation of the Unix operating system (the BSD kernel wasn't yet available yet) so he wrote his own kernel which became known as the Linux kernel.

# The CLI

### Anatomy of a CLI Command
CLI is often called a REPL, a Read Evaluate Print Loop. It's basically an interactive way of programming where you're writing one line of code at a time, feeding data in and out of little programs. Using commands here, you can navigate around you computer, read and write data, make network calls, and all sorts of other stuff. Basically most anything you can do with a desktop you can do with a command line.

The way a REPL works is that you send one command at a time and the shell runs the command and returns to you a result. During the course of running that one command, it may print some things out. And you can, using some rudimentary programming syntax, write a line that runs multiple times (or, another way of saying "runs multiple times" is looping.)

### Shells and Emulators
Shell is almost certainly called (it definitely is unless you changed something), the Bourne Again Shell (which is making fun of the Bourne shell which bash replaced.) It's by far the most common shell and is over 30 years old. the most common of which are zsh, ash, PowerShell, and cmd.exe.
Shell is running inside some sort of emulator. That emulator could be Terminal.app or iTerm2 on macOS, or Windows Terminal  on Windows 10. This the window that's containing the shell, and you can use that emulator to switch out what shell is running inside of it. For now we want to be on bash (or zsh is basically the same too.)

### File System
The way bash works is that you are always in a folder somewhere on your computer. Think of it like your computer's File Explorer or Finder: you can navigate into and out of folders while you look for files.

Our first command we're going to run in your computer is pwd. So type `pwd` and hit enter. This will send the command `pwd` to the shell which will evaluate that and print out the answer.

`pwd` is a little program that tells you the current path of where you are in the file system. `pwd` stands for present working directory. It's basically like asking the computer "where am I right now?" Mine says `/home/ubuntu`. I am inside of the `ubuntu` folder which itself is inside of the `home` directory. The terms folder and directory are interchangeable and I say both all the time.

### Arguments / Parameters
In the case of cd, we're passing data into cd to tell it how to run. If we run `cd ..`, the `..` is an argument or parameter (basically the same thing, for this purpose the two terms can be used interchangeably.) This is just how you pass information into the program so it can do what you want it to do. Not all programs need parameters or sometimes they're optional. Let's look at `pwd`: it never needs any arguments. Or `ls` which has optional arguments. If you say `ls`, it's the same as saying `ls .`. The `.` in this case means "this directory". So if I say `ls ..` it'll give me what's the content of the directory one up from where I am. Or if I say `ls /home` it'll give me the contents of the `home` directory. In these examples, I've given you arguments that happen to be paths but that isn't always true. Arguments are just bits of information you give to a program, frequently they're paths to files or folders but they can often be other things.

### Flags
`--help` which is a flag but this commands can take all sorts of flags to customize how they'll act. Like parameters, they're bits of information that change how the command works. 
Many programs allow you to be lazy and combine flags together. In this case, we can say `ls -la` and that's the same as `ls -a -l` (order doesn't matter either.) This is usually true but it depends on the individual command you're running.
You can pass parameters to flag too. Let's say in our home directory we wanted to not show the `snap` directory in our output. We can use flags to do that. If we type `ls --ignore snap` it will not output snap. This can also be written as `ls --ignore=snap` to make it clearer what that ignore is referring to. We can also say `ls -I snap` for the shorthand. We can't use the equal here. Lastly if we wanted to do an `ls` on the `/home` directory and not show the `ubuntu` folder, we could type `ls --ignore ubuntu /home`. In this particular case, the order is important. Immediately after ignore, the part you're trying to ignore is passed, then the last parameters to `ls` as a whole is passed. This is why some people like that equals. `ls --ignore=ubuntu /home` is very clear.

# Editors

### nano
nano is an old open source text editor that itself was an evolution from a previous text editor called pico. Pico was the text editor of the command-line email client Pine that people grew to love so much that they used it for everything. Because Pine was licensed in such a way that Debian wouldn't include it with its distro, Chris Allegretta re-implemented under the name  TIP (_Tip Isn't Pico_, computer scientists love  it eventually was renamed to nano.

### vim
The genesis of the ideas that went into vim started with an editor called ed (said ee-dee) which itself was inspired by a previous editor called qed. ed was developed by Ken Thompson at Bell Labs in 1969. It is a line-oriented editor and I have no clue how to use it. It's actually rather well known for being pretty user unfriendly. In spite of this, it's still available on most Unix-like systems including Ubuntu and macOS. If you do start it, just know it's CTRL+D a few times to quit it. It's important to note that ed was created in a time where memory was precious, screens were tiny and sometimes just one line at a time, and modems were measured in bits, not even kilobits. It arose at a time when it fit its constraints.
vim has multiple _modes_ you can put the editor into. By default we are in command mode. So if you start typing, nothing will appear and you may actually accidentally trigger some commands. If you want to kick the editor into insert mode, just hit `i`. You should see `-- INSERT --` at the bottom to let you know you can type now. I'm going to put and now I'm writing this from vim. at the bottom of the file. Once I'm done writing and want to head back to command mode, you can hit Esc. You'll see the `-- INSERT --` disappear.

# Files, Pipes, and Permissions

### Interacting with Files
A core concept of computing in general is files but in particular when it comes to navigating a command line. In this section we're going to go over some of the core programs you'll want to know so you can interact with files in Linux :
1. `less`. is a program for reading files.
2. `man`. it will show manual for a command.
3. `cat`.  is short for concatenate because it concatenates the file to the standard output.
4. `head` / `tail`. Head will read the first lines of a file and out put them and tail will read the last lines of a file and output them.
5. `mkdir`. mkdir makes a new directory/folder.
6. `touch`. touch create a new empty file.
7. `rm`. Remove a file.
8. `cp`. is short for copy.
9. `mv`.  moving a file from one place to another.
10. `tar`.  is short for tape archive and it initially used to prepare files to be backed up to a magnetic tape archive but it became useful to just group together files in single files as a tarball (like a zip file).


# Streams and Pipes

### Streams
Linux has an interesting concept where basically all input and output (which are text) are actually streams of data/text. Like plumbing pipes where you can connect and disconnect sections to redirect water to different places, so too can you connect and disconnect streams of data. There are three standard streams :
1. `stdout` (said standard output or standard out).
2. `stdin` (said standard input or standard in).
3. `stderr` (said standard error or standard err).

### Pipes
One of the most powerful shell operators is the pipe (|). The pipe takes output from one command and uses it as input for another. And, you're not limited to a single piped command—you can stack them as many times as you like, or until you run out of output or file descriptors.

# Users, Groups, and Permissions
* User: the owner of the file (person who created the file).
* Group: the group can contain multiple users. Therefore, all users in that group will have the same permissions. It makes things easier than assign permission for every user you want.

### Permissions
Every file and directory in your UNIX/Linux system has following 3 permissions defined for all the 3 owners discussed above.
* Read: This permission give you the authority to open and read a file. Read permission on a directory gives you the ability to lists its content.
* Write: The write permission gives you the authority to modify the contents of a file. The write permission on a directory gives you the authority to add, remove and rename files stored in the directory. Consider a scenario where you have to write permission on file but do not have write permission on the directory where the file is stored. You will be able to modify the file contents. But you will not be able to rename, move or remove the file from the directory.
* Execute: In Windows, an executable program usually has an extension “.exe” and which you can easily run. In Unix/Linux, you cannot run a program unless the execute permission is set. If the execute permission is not set, you might still be able to see/modify the program code(provided read & write permissions are set), but not run it.

