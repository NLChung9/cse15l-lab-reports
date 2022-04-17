# Lab Report 3

The programming prompt we will be working with for this essay is: 
_"Write a program that takes a markdown file as a command line argument and then prints 
out all of the URLs of the links (but not of images) in that file.”_

**Part 1: Getting Started**

> Watch [this video](https://www.youtube.com/watch?v=k67e-Icw4ug)

> Answer the following questions:
1. How many times did the programmer use the internet to look up how to do something?<br />
    **1**
2. Around what was the largest number of lines of code written in between runs of the program?<br />
    **11**
3. Around how many times did the programmer use autocomplete on a variable name? How many typos do you think this helped avoid?<br />
    **15**. I think this helped avoid 3-5 typos, but it also slightly quickened the coding process.
    Its usefulness would be more apparent in writing a larger program.
    
**Part 2: Getting and Running the Code**

> Make a **fork** of [this repository.](https://github.com/nidhidhamnani/markdown-parser)

> Answer the following questions: 
1. How many different values does currentIndex have when the program is run on the given example? What are they?<br />
    **3 values: 0, 39, and 65. The 0 is the value that currentIndex is initialized with. Then, currentIndex is 
    modified to become closeParen + 1 twice. This is because test-file.md has two closed parentheses located at
    indexes 38 and 64.**
2. What is the purpose of the second argument to indexOf? What would be different if it wasn’t provided?<br />
    **The second argument provides the index at which the program should start.
      So, for indexOf("]", openBracket), the method searches for a "]" located after the index where openBracket was found.**
      
**Part 3: Finding a Breaking Test**

> Create a new markdown file that tests a different use of links than in the original. Test the program on that file. Discuss among 
> your group what it means to test something different. Try running your new test. What happens? Did it succeed or not?
> 
> Repeat this process until you create a file that has incorrect behavior. Commit this new file and push it to GitHub.
> 
> Question: _Why bother making a commit at this point? What benefit might that have in the future? How might it help a staff member who is answering your question on Piazza?_
 
Answer: **Making this commit helps people view the bug much more easily. In future projects, it will facilitate the process of debugging between group members. This allows a staff member to view your code and work with it manually.**

**Part 4: Improving the Program**

> Discuss as a group – why is the program not behaving as expected on the test file you wrote? How could you fix it?
> 
> The program assumes that the text ends at a parentheses (using currentIndex to count them) so maybe we could add code that breaks out of the loop when it reaches the end of the text
> 
> Work on fixing the problem as a group so that:<br />
> -The original test (test-file.md) still has the same output (the one the programmer initially tried)<br />
> -The broken test you wrote has correct output<br />
> 
> **Remember – this means you need to keep testing on the original test and on the new one you wrote, until both work.**

The program breaks if the **last character of the file is not ")".**

This is because...
1. The while loop is only set to end when currentIndex >= markdown.length
2. currentIndex is only modified to be closeParen + 1, or the index after closeParen.

So, if closeParen is not the last character, currentIndex can never become equal to or greater than markdown.length, so the loop will run infinitely.

To fix this, I added the following code after int openBracket = markdown.indexOf("[", currentIndex);

if (openBracket == -1){
    break;
}

If openBracket == -1, that means there are no more "[" in the text. Because open brackets are required for making links in markdown,
(no open brackets) == (no more links), and the loop breaks as a result.

**Part 5: repeating the Process**

> Create two more breaking tests, then two fixes to the program.







