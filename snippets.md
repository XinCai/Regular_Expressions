```

.       - Any Character Except New Line
\d      - Digit (0-9)
\D      - Not a Digit (0-9)
\w      - Word Character (a-z, A-Z, 0-9, _)
\W      - Not a Word Character
\s      - Whitespace (space, tab, newline)
\S      - Not Whitespace (space, tab, newline)

\b      - Word Boundary
\B      - Not a Word Boundary
^       - Beginning of a String
$       - End of a String

[]      - Matches Characters in brackets
[^ ]    - Matches Characters NOT in brackets
|       - Either Or
( )     - Group

Quantifiers:
*       - 0 or More
+       - 1 or More
?       - 0 or One
{3}     - Exact Number
{3,4}   - Range of Numbers (Minimum, Maximum)


#### Sample Regexs ####

[a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+\.[a-zA-Z0-9-.]+
```

Example : `path: /bsb(/|$)(.*)` 这个表达式 使用了 regex 来表示 一个url path， 使用了以下 regex 符号：  
  - group expression : `()`
  - any character: `.`
  - either or : `|` 
  - end of a string: `$` 
  - quantifiers: `*` 
说明：  /bsb(/|$) : 表示 match either `/` or end of a string `$`
      （.*）： 表示 0个 或 多个 任意 character       


  
