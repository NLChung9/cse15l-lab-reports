# Lab Report 

[My markdown repository](https://github.com/NLChung9/markdown-parser)

[Markdown repository I reviewed in week 7](https://github.com/MichaelYe48/markdown-parser)

> Consider the following tests:

> 1. </br>![Snippet 1](lab-report-4/lab-report-4-snippet1.png)

> 2. </br>![Snippet 2](lab-report-4/lab-report-4-snippet2.png)

> 3. </br>![Snippet 3](lab-report-4/lab-report-4-snippet3.png)

Expected outputs:
1. [`google.com, google.com, ucsd.edu]
2. [a.com, a.com(()), example.com]
3. [https://sites.google.com/eng.ucsd.edu/cse-15l-spring-2022/schedule]

How I turned the snippets above into tests: </br>![My Tests](lab-report-4/lab-report-4-tests1.png)

How the student I reviewed turned the snippets above into tests: </br>![His Tests](lab-report-4/lab-report-4-tests2.png)

### Implementation

My implementation: All three tests failed. (T_T) </br>![My failed tests](lab-report-4/lab-report-4-implementations1.png)

His implementation: All three tests failed. </br>![His failed tests](lab-report-4/lab-report-4-implementations2.1.png)
</br>![His failed tests](lab-report-4/lab-report-4-implementations2.2.png)
</br>![His failed tests](lab-report-4/lab-report-4-implementations2.3.png)

**Snippet 1**: This may be a small change in terms of lines of code.
To make the tests with inline ticks work, I would need to scan for any inline ticks that...
- start before the openBracket and end after the openBracket
- start after the openBracket and end after the closedBracket
- start after the closedBracket but before the openParenthesis(no matter where it ends, it breaks the link)

Additionally, if an inline tick starts BETWEEN the open and closed parenthesis and ends AFTER the closedParenthesis,
then the link doesn't break, but I can't treat the tick inside the parentheses as an open tick.

**Snippet 2**: This seems like it might be a larger change in lines of code.
To make tests with nested links, parentheses, and brackets, I would need to make sure that...
- If there are multiple links nested inside each other, only the innermost link will be treated as a link.
- If there are nested parentheses or brackets, that whichever "[]" pair that resides DIRECTLY before a "()" pair becomes part of the link. If the nest is between the brackets, it will show up as part of the link. If the nest is between the parentheses, it will become part of the URL.

There are many ways to write nested parentheses or brackets that break the code, so adding fixes for all of those cases might be more than 10 lines.

**Snippet 3**: This may be a small change in terms of lines of code.
- If there are any line breaks within the brackets or the parentheses, then the link is broken.



