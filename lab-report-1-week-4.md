# Lab Report 2 Week 4: Debugging and Testing

## Code Change 1: Identificatoin of Images Bug
[Link to commit](https://github.com/Miyuki-L/markdown-parser/commit/54e14a9bd72f58eb66159342c38a14db985d04d4?diff=split) containing the changes.
### Screenshot of the Code Change diff from Github
![Image identified as link code diff](lab2-Images\imageIdnetificationFixCodeDiff.png)
### Link to test file containing failure-inducing input
Here is the link to the failure-inducing input
[file link](https://github.com/Miyuki-L/markdown-parser/blob/main/test2.md).
### Symptom shown of Failure-inducing input
![image identification symptom](lab2-Images\imageIdentificationSymptom.png)
* This file was run with the original version provided by [source github](https://github.com/nidhidhamnani/markdown-parser/blob/main/MarkdownParse.java).
### Relationship between the bug, the symptom, and failure-inducing input
* Bug: the program does not differentiating between images and links by checking if there is a preceding `!`
* Symptom: wrong answer (counting image source as a link)
* Failure-inducing input: file containing an image

**Relationship**: The failure-inducing input containing an image was passsed to make sure that the parser does not identify images as links since the markdown for links (`[text](link)`) and images (`![alt text](source)`) differs only by an `!`. This input executed the bug that the program had (not check for the preceding`!` for images). Hence the program identifed an image's source as a link, which is the wrong answer, resulting in the symptom.

---
## Code Change 2: Not Identifying Links After Images Bug
[Link to commit](https://github.com/Miyuki-L/markdown-parser/commit/cb997e0b086965a79d75ff3983d058c63cd4b3e8?diff=split) containing the changes.
### Screenshot of the Code Change diff from Github
![not identifying links when there are images code diff](lab2-Images\imageAndNoLinkCodeDiff.png)
### Link to test file containing failure-inducing input
Here is the failure-inducing [input file](https://github.com/Miyuki-L/markdown-parser/blob/main/testImageAndLink.md).
### Symptom shown of Failure-inducing input
![Not identifying links after image symptom](lab2-Images\imageAndNoLinkSymptom.png)
* [This](https://github.com/Miyuki-L/markdown-parser/blob/54e14a9bd72f58eb66159342c38a14db985d04d4/MarkdownParse.java) was the version of MarkdownParse that the file was failing on.
### Relationship between the bug, the symptom, and failure-inducing input
* Bug: the program breaking out of the loop too early.
* Symptom: wrong answer (not identifying the link after the image as a link).
* Failure-inducing input: file containing an image followed by any amount of links.

**Relationship**: Having a image followed by a link as the input caused the bug of breaking out of the loop when it sees a image to execute, thereby ending the parser and stops checking anything that appears after it. Since the bug caused the parser to not check the markdown that appears after the image, it misses the link after the image, resulting in a symptom of a wrong answer as it does not identify the link present in the markdown. 

---
## Code Change 3: Incomplete Link Causing Infinite Loop Bug 
[Link to commit](https://github.com/Miyuki-L/markdown-parser/commit/fb2e6e7e0d03a9e705fd1ccd6abca039c8bd28c7) containing the changes.
### Screenshot of the Code Change diff from Github
![Incomplete link bug fix code diff](lab2-Images\incompleteLinkCodeDiff.png)
### Link to test file containing failure-inducing input
Here is the failure-inducing [input file](https://github.com/Miyuki-L/markdown-parser/blob/main/testNoLink.md).
### Symptom shown of Failure-inducing input
![Infinite loop symptom cause by incomplete link](lab2-Images\incompleteLinkSymptom.png)
* [This version](https://github.com/Miyuki-L/markdown-parser/blob/cb997e0b086965a79d75ff3983d058c63cd4b3e8/MarkdownParse.java) was the version of MarkdownParse that the file was run on and failed.
### Relationship between the bug, the symptom, and failure-inducing input
* Bug: not catching or checking if any of the opening and closing brackets and parenthesis were missing, essentially assuming that all elements were present.
* Symptom: infinite loop causing heap to run out of memory
* Failure-inducing input: file containing incomplete link (missing closing bracket and also parenthesis appearing before brackets)

**Relationship**: The failure-inducing input of incomplete and incorrectly formated link caused the bug to execute as elements of the link format were missing and the program was written with the assumption that all elements were present. The input just happened to execute the bug in a way that the currentIndex used as part of the while loop condition ends up being zero every single time the condition is checked. Thus the parser always starts again at the begining of the file everytime thereby never ending and exiting the while loop causing a infinite loop, resulting in the symptom.