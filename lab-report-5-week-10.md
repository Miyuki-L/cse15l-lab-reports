# Lab Report 5 Week 10: Vim and VimDiff

## How To Find the Test With Different Results
Note: Instructions are under the assumption that the test files are alreardy present in in the diretctory and there is a bash script that runs the test files. 

1. In both your Markdown Parser direcotry and the provided Markdown Parser directory run the command `bash script.sh > results.txt`
   * This is assuming you have a bash script  file named script.sh
   * This will redirect the output of running the script in to a file named results.txt.
2. Go to your home directory (This is assuming that the home directory contains both the markdown parse directories).
3. Run the command `vimdiff my-markdown-parser/results.txt cse15lsp22-markdown-parser/results.txt`
   * Adjust and rename the paths if necessary. 
   * You want to run this command on the results.txt file you created in step 1. 
4. After running the command you will see something like this:
   ![picture of vimdiff running](lab5-Images\VimDiffView.png)
5. The lines highlighted in pink represents lines where the two files differ.
   * This is where you will find the tests with different results. 

## Link To Test Files with Different Results
* [Test 14](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/14.md)
* [Test 487](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/487.md)

## Test 14
### Expected Output 
![Test 14 Expected Output](lab5-Images\test14expectedoutput.png)
* The expected output for test 14 is that no links are identified. So the results in results.txt for this test should be [].
* Expected output determined using [the CommonMark demo site](https://spec.commonmark.org/dingus/).
### Implmentation Outputs
#### My Implementation
![Test 14 Output on My Markdown Parser](lab5-Images\test14myoutput.png)
* My implementation provides the correct output for this test file.
#### Provided Implementation
![Test 14 Output on Provided Markdown Parser](lab5-Images\test14providedparseroutput.png)

Changes:
* ![Test 14 Provided Parser Area Needing Change](lab5-Images\test14providedparserareaforchange.png)
* The problem is that although there is code in the test file that has the valid format for a link, because the opening bracket is escaped, it is not a link and the program does not check for escaped characters. To fix this bug, the program should check whether each of the deliminators of a link [,],(,) are escaped by adding a check after finding each of the deliminator or after finding all deliminators that check whether there is a escape key ("`\`") preceding each deliminator. (This change should be inside the getLinks function.)

## Test 487
### Expected Output
![Test 487 Expected Output](lab5-Images\test487expectedoutput.png)
* The expected output for test 487 is that no links are identified. So the results in results.txt for this test should be [].
* Expected output determined using [the CommonMark demo site](https://spec.commonmark.org/dingus/).

### Implmentation Outputs
#### My Implementation
![Test 487 Output on My Markdown Parser](lab5-Images\test487myoutput.png)

Changes:
* ![Test 487 Provided Parser Area Needing Change](lab5-Images\test487providedparserareaforchange.png)
* The problem is that because there is a space in the provided url, it is no longer a link however my markdown parser conducts no checks and assumes that whatever is in between the parentheses is a valid url. What should be done to fix the code is that before adding the identified potential link to the list of identified links certain checks should be made on the link. In this case, there should be a check whethehr the potential link contains a space or not and if it does then it's not a link. Changes should be made to the getLinks function. 

#### Provided Implementation
![Test 487 Output on Provided Markdown Parser](lab5-Images\test487providedparseroutput.png)
* The Provided Markdown Parser correctly identifies that there are no links in the test file. 
