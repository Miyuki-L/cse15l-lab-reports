# Setting Up your IDE and Accessing a Remote Server

## Installing VScode
1. First go to [Visual Studio Code's Website](https://code.visualstudio.com/)
2. Choose the appropriate version for you operating system.
   ![VScode Installer](lab1-Images\VSdownload.png)
3. Follow the installer instructions
4. Once VScode is installed. You should see something like this when you open it. 
   ![picture of running VScode](lab1-Images\runningVSCode.png)

### Useful or Fun things
* You can turn on Autosave by going to File > Autosave
   * This way you do not have to keep saving the file.

   ![turning autosave on](lab1-Images\autosave.png)
* You can change the theme of VScode by Settings > Color Theme
   ![changing VScode themes](lab1-Images\theme.png)

* You can turn on Word warp to make view long lines of code more convinent
   * View > Word Wrap

   ![turning on word wrap](lab1-Images\wordwrap.png)


## Remotely Connecting

### Before You Start (Window Users): Installing OpenSSH
1. Go to Settings > Apps > Optional features in your computer settings.
   * If you want more detailed instructions go [here](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse). 
2. In the search search for OpenSSH Client. If it is there, then you are good. You have OpenSSH intalled.
3. If not, up top there is "Add an optional feature" and click on the View features button. 
4. Search for and install OpenSSH Client.

### Finding Your Course-Specific account
1. Go to https://sdacs.ucsd.edu/~icc/index.php and find your account.
   * For CSE 15L, the account follows the formate cs15lsp22____ 
      * The underscored section is unique to each student.
2. Once you found your account name you may need to reset your password. 
   * Follow the instructions [here](https://piazza.com/redirect/s3?bucket=uploads&prefix=paste%2Fktv2gnof3sx5bf%2F181c3cb053df5cf1ccaf0457f56f12a2e5aa90b139aef8c2ea8fcc590f02fadf%2FHow-to-Reset-your-Password.pdf) for reset.
   * Caution: The password reset may  take a while.

### Actually Connecting
1. Open a terminal in VSCode using Ctrl + ` or Terminal > New Terminal
   ![Opening a Terminal in VScode](lab1-Images\openingTerminal.png)
2. Type in ther terminal the following command:
   * `ssh cs15lsp22[insert your specific letters]@ieng6.ucsd.edu`
   * so the format of the command is ssh [your specific account]@ieng6.ucsd.edu
3. Then it will prompt you for a password. Type in your password
   * Don't worry if you do not see the usual **** when you type your password. It will look like you are not typing anything but you are. 
4. Once you get in you should see something like this
   ![accessing SSH](lab1-Images\accessingSSH.png)


## Trying Some Commands

### Here are some commands that you can do
* `pwd`
* `mkdir <name>`
* `cd ~`
* `cd ..`
* `cd <directory>`
* `ls`
* `ls -lat`
* `ls -l` or `ls -a` or `ls -t`
* `ls <directory>`
* `cp <current path> <destination path>`
* `cat <path>`

![example commands](lab1-Images\examplecommands.png)

### Explanations
* `pwd`: present working directory. 
   * It will tell you the current path/location that you are at
* `mkdir <name>`: make directory
   * It will create a directory (can be understood as a folder) with the provided <name>.
* `cd`: change directory
   * This will change which directory you are in
   * `cd ~`: will take you to your home directory
   * `cd ..`: will take you back one directory
   * `cd <directory>`: takes you to a directory that is in your present directory
   * `cd <full path>`: will take you to the directory specified at that path.
* `ls`: list
   * it will list the contents in the current directory
   * you can add commands like `-l`, `-a`, `-t` and combine them.
      * `-l`: long
         * will give you more information about the contents in the present directory
      * `-a`: all
         * will list **all** the files even the hidden ones.
      * `-t`: time
         * will sort the contents by their time. 
* `cp <current path> <destination path>`: copy a file and directory from one location to another
   * will copy what ever is specified at the current path to the location designated by the destination path
* `cat <path>`: read the content
   * if <path> designates a file it will show you the contents of the tile
   * if <path> is an directory it will tell you that it is an directory


## Moving Files with `scp`
`scp` stands for secure copy\
`scp` is used to copy a file or directory from your local computer into the remote computer

### How to use `scp`
In the terminal of your local computer use the following command
   * `scp <thing to copy> <computer to copy to>: <destination location on the computer>`
   * ex: `scp WhereAmI.java cs15lsp22zz@ieng6.ucsd.edu: ~/`
      * this will copy the file WhereAmI.java to the computer user cs15lsp22zz can access and into its home directory.
   * It will prompt you for your password. Use the same password that you use to log into ssh

Here is an working example
![example of scp](lab1-Images\scpExample.png)


## Setting an SSH Key

## Optimizing Remote Running