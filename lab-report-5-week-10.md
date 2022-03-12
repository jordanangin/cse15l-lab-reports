# **WEEK 10 LAB REPORT**
**Jordan Peranginangin (PID: A16798626)**

**How you found the tests with different results (Did you use diff on the results of running a bash for loop? Did you search through manually? Did you use some other programmatic idea?)**

In order to find the tests with different results, I first redirected the output of bash script.sh to result.txt in my implementation of markdown-parse. I then repeated the process for the professor's version of markdown-parse. Once I had two result.txt files, I used the diff command which showed the differences between the result.txt file in my markdown-parse and the result.txt file in the professor's version. 

---
## **TEST 1**
22.md:
```
[foo](/bar\* "ti\*tle")
```
My implementation's result: 
```
[]
```
Their implementation's result: 
```
[/bar\* "ti\*tle"]
```
Expected result: 
```
[]
```
Based on the test shown above, my implementation of markdown-parse is correct. Because backslashes are not valid characters in links and the text between the opening and closing parentheses contain backslashes, the link in 22.md is invalid. Consequently, the link in 22.md shouldn't be added to the resulting ArrayList. Therefore, my implementation is correct since the resulting ArrayList is empty and the provided implementation is incorrect since the link was added to the resulting ArrayList.

The problem with the provided implementation of markdown-parse is that the code does not check whether backslashes exists in potential links. In order to solve this, indexOf("\") can be used. After using substring to grab the text between the two parenthesis, call indexOf("\"). If indexOf("\") returns any number besides -1, the link contains a backslash and it shouldn't be added to the resulting ArrayList.

---
## **TEST 2**
495.md:
```
[link](foo(and(bar)))
```
My implementation's result: 
```
[foo(and(bar))]
```
Their implementation's result: 
```
[foo(and(bar]
```
Expected result: 
```
[foo(and(bar))]
```
Based on the test shown above, my implementation of markdown-parse is correct. Markdown-parse should grab all the text between the opening and closing parentheses. However, the provided implementation does not. Instead, the provided implementation grabs all the text between the first opening parenthesis and first closing parenthesis and adds that to the ArrayList. On the other hand, my implementation correctly grabs all the text between the first opening parenthesis and the last closing parenthesis.

The problem/bug with the provided implementation of markdown-parse is that the code does not check whether the closing parenthesis is the last closing parenthesis of that line. In order to fix this, the code needs to check whether there is another closing parenthesis before the next opening bracket. If another closing parenthesis before the next opening bracket exists, store the index of that closing parenthesis in closeParen. This change will fix the bug seen in the provided implementation.