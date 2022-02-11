# **WEEK 6 LAB REPORT**
**Jordan Peranginangin (PID: A16798626)**

## **STREAMLINING SSH CONFIGURATION**
![image](configfile.png)
This is a screenshot of my .ssh/config file. I first navigated to the root directory using cd. I then used cd a second time to navigate into the .ssh directory. From there, I opened up the existing config file in VScode and edited the lines to match the example shown in the week 5 lab. 
```
$ java MarkdownParse image.md
[google.com, fake.png]
```
The symptom was that the getLinks() function was returning both the link and image when the desired result was just the link. The bug that caused this symptom was that the getLinks() could not differentiate a markdown link from an image. The failure-inducing input was the image.md file that included both a link and an image.
