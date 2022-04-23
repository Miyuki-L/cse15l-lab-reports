# Lab Report 2 Week 4: Debugging and Testing

## Code Change 1: Identificatoin of Images
### Screenshot of the Code Change diff from Github
![Image identified as link symptom](lab2-Images\imageIdnetificationFixCodeDiff.png)
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

Relationship: passing in a file containing an image triggers the bug as the markdown for links (`[text](link)`) and images (`![alt text](source)`) differs only by an `!` and the program does not check for the `!` causing it to identify an image's source as a link and returning resulting in an wrong answer, the symptom.

---
## Code Change 2
### Screenshot of the Code Change diff from Github
### Link to test file containing failure-inducing input
### Symptom shown of Failure-inducing input
### Relationship between the bug, the symptom, and failure-inducing input
---
## Code Change 3
### Screenshot of the Code Change diff from Github
### Link to test file containing failure-inducing input
### Symptom shown of Failure-inducing input
### Relationship between the bug, the symptom, and failure-inducing input