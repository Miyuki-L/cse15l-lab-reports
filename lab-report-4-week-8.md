# Lab Report 4: Code Review of Markdown Parse

## Markdown Parser Directories
* [My Markdown Parse Repository](https://github.com/Miyuki-L/markdown-parser)
* [Markdown Parse Reviewed Repository](https://github.com/mv5903/markdown-parser)

## Snippet 1

### The Code Snippet
```
`[a link`](url.com)

[another link](`google.com)`

[`cod[e`](google.com)

[`code]`](ucsd.edu)
```
### Expected Output
![Expected Output of Snippet 1](lab4-Images\snippet1Preview.png)
The expected output should be the list 
* ```["`google.com", "google.com", "ucsd.edu"]```

### JUnit test
#### My Repository's JUnit Test
![JUnit test code snippet 1 my repo](lab4-Images\myrepositorytestsnippet1.png)
#### Reviewed Repository's JUnit Test
![JUnit test code snippet 1 reviewed repo](lab4-Images\reviewedrepositorytestsnippet1.png)
#### JUnit Test Output on My Repository
![JUnit Output on my repository](lab4-Images\myrepositorysnippet1output.png)
#### JUnit Test Output on Reviewed Repository
![JUnit Output on reviewed repository](lab4-Images\reviewedrepositorysnippet1output.png)

### Code Change Review on My Repository
I don't think there is a small code change that would make it work as it will involve a couple if statements and while loop which would result in more than 10 lines. For every pair of backticks before the closeParen, check if the index of the openBracket or closeBracket is within the backticks. If the openBracket is within the backticks reset all deliminators of a link, and if closeBracket is within the backticks reset all but the openBracket.  

---

## Snippet 2
```
[a [nested link](a.com)](b.com)

[a nested parenthesized url](a.com(()))

[some escaped \[ brackets \]](example.com)
```
### Expected Output
![Expected Output of Snippet 2](lab4-Images\snippet2Preview.png)
The expected output should be the list 
* ```["a.com", "a.com(())", "example.com"]```

### JUnit test
#### My Repository's JUnit Test
![JUnit test code snippet 2 my repo](lab4-Images\myrepositorytestsnippet2.png)
#### Reviewed Repository's JUnit Test
![JUnit test code snippet 1 reviewed repo](lab4-Images\reviewedrepositorytestsnippet2.png)
#### JUnit Test Output on My Repository
![JUnit Output on my repository](lab4-Images\myrepositorysnippet2output.png)
#### JUnit Test Output on Reviewed Repository
![JUnit Output on reviewed repository](lab4-Images\reviewedrepositorysnippet2output.png)

### Code Change Review on My Repository
I think this would require a more invovled change. If statements would need to be added to make sure that none of the deliminates identified for the potential link are escaped. New functions that involved loops would be needed to identify the correct matching parentheses and brackets for nested parenthesis and brackets.   

---

## Snippet 3
```
[this title text is really long and takes up more than 
one line

and has some line breaks](
    https://www.twitter.com
)

[this title text is really long and takes up more than 
one line](
https://sites.google.com/eng.ucsd.edu/cse-15l-spring-2022/schedule
)


[this link doesn't have a closing parenthesis](github.com

And there's still some more text after that.

[this link doesn't have a closing parenthesis for a while](https://cse.ucsd.edu/



)

And then there's more text
```

