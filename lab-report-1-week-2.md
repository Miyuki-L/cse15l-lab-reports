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
2. Type in ther terminal the following command `ssh cs15lsp22[Insert Your specific letters]@ieng6.ucsd.edu`
   * so the format of the command is ssh [your specific account]@ieng6.ucsd.edu
3. Then it will prompt you for a password. Type in your password
   * Don't worry if you do not see the usual **** when you type your password. It will look like you are not typing anything but you are. 
4. Once you get in you should see something like this
   ![accessing SSH](lab1-Images\accessingSSH.png)

## Trying Some Commands

## Moving Files with `scp`

## Setting an SSH Key

## Optimizing Remote Running