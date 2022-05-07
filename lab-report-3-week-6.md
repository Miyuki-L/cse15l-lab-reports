# Lab Report 3: More Things with SSH

## Streamline SSH Configuration
### Create Your Alias
1. Open the file or create a file located at `~/.ssh` called config.
2. Add the lines
   ```
   Host ieng6
    HostName ieng6.ucsd.edu
    User cs15lsp22zzz (use your username)
   ```
   ![config file contents](lab3-Images\ssh-config-editing.png)
   * If this doesn't work try adding a line explicityly refering to your id_rsa file
      ```
      Host ieng6
         HostName ieng6.ucsd.edu
         User cs15lsp22zzz (use your username)
         IdentityFile ~/.ssh/id_rsa
      ```
3. The entry tells SSH what username to use (value in User) when logging into specific servers (HostName) and gives the server nicknames (Host)
4. To log on type `ssh [nickname you chose]`
   * In this case `ssh ieng6`
   ![ssh log in using alias](lab3-Images\ssh-with-alias.png)

* Now you can use `ieng6` in commands now instead.
   * For example copying a file to the server
      * Template: `scp [file to copy] [nickname]:[location to copy to]`
      * `scp .\testScpWithAlias.txt ieng6:~/testScpWithAlias.txt`

   ![scp using nickname](lab3-Images\scp-with-alias.png)

## Set Up Github Access from ieng6

## Copy Whole Directories with `scp -r`
When you are scp-ing a small group of files(your scenario) you need to make sure that the target directory exists in remote. If you are scp-ing the entire folder then the folder is automatically created if it does not exist already.