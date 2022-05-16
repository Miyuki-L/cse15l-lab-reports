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

---
## Set Up Github Access from ieng6
This section will allow you to complete actions like git push from the command line. Demo would be done using the ieng6 server

### Instruction
1. First connect to the ieng6 remote server
2. Use `ssh-keygen` to create the keys.
   * Use the default setting of `ssh-keygen` (id_rsa, other version might have problems with the ieng6). Simply press enter when prompted for file to save the key (unless you want to save the key elsewhere) and for a passphrase.
3. Go to where the public key is saved
   * If you used the default then it'll be in the .ssh folder
4. Use `cat id_rsa.pub` or the relevant file name or other commands to get the contents of the public key. <br>
   ![private key on computer](lab3-Images/private-key-on-ieng6.png)
5. Go to [Github](github.com) and in the uppr right corner of any page, click the profile photo. Then click **Settings**.
6. On the left find and click **SSH and GPG keys** 
7. Using the **New SSH Key** button, create a name for the key and in the "Key" field paste the public key that was copied.
![Adding public Key to Github](lab3-Images/public-key-on-github.png)

### Demo
Now if you run the command `git push` it should work and here is the resulting [git commit](https://github.com/Miyuki-L/CSE15L-Skill-Demo-1/commit/b34aea40bd67e2a3cf78ffb2ee6c4a2ffd2ddd32).
![Working Git commit and push on ieng6](lab3-Images/git-commit-and-push-on-ieng6.png)

---

## Copy Whole Directories with `scp -r`
The `-r` is for recursive which allows us to copy the entire directory.
### Copy Whole Directory
* Template: `scp -r [path to directory to copy] [server]:[location to copy to]`
   * e.g. `scp -r . ieng6:~/markdown-parser`
      * This will copy the present directory over to a directory called markdown-parser on the server we nicknamed ieng6.
      * If the destination directory exists then it'll copy it into that directory but if not it'll create it.

   ![Recursive Copy Directory with scp -r](lab3-Images\scp-whole-dir-recursively.png)
   * Note: picture only shows the begining few lines as the output is too long to show.
* Now you can run the tests in the directory that you just copied on the ieng6 server
   ![running tests on ieng6 server](lab3-Images\compile-run-markdown-test-in-ieng6.png)
### Copy Select Files
* Template: `scp -r [path of files, types of files, or directory to copy] [server]:[location to copy to]`
   * e.g. `scp -r *.java *.md lib/ ieng6:~/markdown-parse`
      * This will copy all the java and md files in the present directory into the markdown-parse directory in remote server ieng6.
      * **Note: the directory must already be present on the remote server**

   ![scp parts of a directory](lab3-Images\scp-part-ssh-compile-run-test-in-ieng6.png)

### Copy and Run in Same Line
The following command would copy the entire directory over to the remote server then log on to the server, compile and run the tests.

* `scp -r . ieng6:~/markdown-parse;ssh ieng6 "cd markdown-parse/;/software/CSE/oracle-java-17/jdk-17.0.1/bin/javac -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar MarkdownParseTest.java;/software/CSE/oracle-java-17/jdk-17.0.1/bin/java -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar org.junit.runner.JUnitCore MarkdownParseTest"`

![scp and ssh in same line compile and run](lab3-Images\scp-ssh-whole-one-line-part-1.png)
![scp and ssh in same line compile and run](lab3-Images\scp-ssh-whole-one-line-part-2.png)

Things to note:
* When running javac and java commands with ssh as in the command above, the server uses an older version of java, which results in a error message like:
   ![java compile error](lab3-Images\same-line-runing-java-version-error-part1.png) 
   ![java compile error](lab3-Images\same-line-running-java-version-error.png)
* Solution: replace javac with `/software/CSE/oracle-java-17/jdk-17.0.1/bin/javac` and java with `/software/CSE/oracle-java-17/jdk-17.0.1/bin/java`. 

