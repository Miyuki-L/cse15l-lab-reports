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
* failure-inducing input: file containing an image

**Relationship**: The failure-inducing input containing an image was passsed to make sure that the parser does not identify images as links since the markdown for links (`[text](link)`) and images (`![alt text](source)`) differs only by an `!`. This input executed the bug that the program had (not check for the preceding`!` for images) which caused it to identify an image's source as a link and returning it as a found link which is the wrong answer, resulting in the symptom.

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
* Bug: the program breaking out of the loop too earily.
* Symptom: wrong answer (not identifying the link after the image as link).
* failure-inducing input: file containing an image followed by any amount of links.

**Relationship**: Having a image followed by a link as the input caused the bug of breaking out of the loop when it sees a image to execute thereby ending the parser and stops checking anything that appears after it. Since the bug caused the program to not check the markdown that appears after the image, it misses the link after the image, resulting in a symptom of a wrong answer as it does not identify the link present in the markdown. 

---
## Code Change 3: Incomplete Link Causing Infinite Loop Bug 
### Screenshot of the Code Change diff from Github
### Link to test file containing failure-inducing input
### Symptom shown of Failure-inducing input
### Relationship between the bug, the symptom, and failure-inducing input