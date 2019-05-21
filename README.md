[See](https://daringfireball.net/projects/markdown/syntax)

# Big Heading
`# Big Heading`  
or
```
Big Heading
===========
```

headings automatically create anchors you can link to

[link to heading anchor](#big-heading)<br/>
`[link to heading anchor](#big-heading)`

## Second Heading
`## Second Heading`

### Third Heading
`### Third Heading`

#### Fourth Heading
`#### Fourth Heading`

##### Fifth Heading
`##### Fifth Heading`

###### Sixth Heading
`###### Sixth Heading`

## Text Formatting

**bold text**<br/>
`**bold text**` 
or 
`__bold text__`

_italic text_<br/>
`_italic text_` 
or 
`*italic text*`

**_bold italic text_ next to bold text**<br/>
`**_bold italic text_ next to bold text**`

_**bold italic text** next to italic text_<br/>
`_**bold italic text** next to italic text_`

~~strikethrough text~~<br/>
`~~strikethrough text~~`

Quoted text:
>is quoted <br/>
```
Quoted text:
>is quoted
```
> You can make<br/>
> the quoted block
>
> as big as you want
```
> You can make<br/>
> the quoted block
>
> as big as you want
```

does <br/> work?<br/>
`does <br/> work?`
yes 

## Lists

- Lists
- Are easy
- To do
```
- Lists
- Are easy
- To do
```
* Asterisks
+ And plus signs
* Work as well
```
* Asterisks
+ And plus signs
* Work as well
```
1. Numbered lists
2. Are straightforward
3. To create
```
1. Numbered lists
2. Are straightforward
3. To create
```
1. Nested lists
   - Can get
   - A little complicated
2. Just make sure
   1. You put the
   2. nested item under
   3. the first character
      - of the preceding item
```
1. Nested lists
   - Can get
   - A little complicated
2. Just make sure
   1. You put the
   2. nested item under
   3. the first character
      - of the preceding item  
```
- [ ] You can make
- [ ] Little check lists
- [x] As well!
```
- [ ] You can make
- [ ] Little check lists
- [x] As well!
```

testing definition list:
<dl>
   <dt>thing</dt>
   <dd>ok</dd>
   <dt>thing2</dt>
   <dd>ok2</dd> 
</dl>

## Code Snippets

This is how you `quote code`
```
This is how you `quote code`
```

```
you can quote
multi-line code
as well
with three back-ticks (```)
before and after
```
\`\`\`<br/>
you can quote<br/>
multi-line code<br/>
as well<br/>
with three back-ticks<br/>
before and after<br/>
\`\`\`

You can also tell it to format syntax highlighting

ruby:
```ruby
5.times do |i|
  puts i * i
end
```
` ```ruby ...``` `

sql:
```sql
CREATE TABLE puppies (
  id INTEGER PRIMARY KEY,
  name TEXT,
  breed TEXT
  )
```
` ```sql ...``` `
  
## Links

Plain links are automatically converted to clickable links
www.github.com

Here is how you add a [link](google.com)<br/>
`Here is how you add a [link](google.com)`

You can also add [relative links](docs/contributing.md)<br/>
`You can also add [relative links](docs/contributing.md)`

And [link to anchors](#big-heading)<br/>
`And [link to anchors](#big-heading)`

## Tables
First Header | Second Header
------------ | -------------
Content from cell 1 | Content from cell 2
Content in the first column | Content in the second column
Third one down | Oh yeah third one down
```
First Header | Second Header
------------ | -------------
Content from cell 1 | Content from cell 2
Content in the first column | Content in the second column
Third one down | Oh yeah third one down
```
a minimum of three hyphens is required under the cell titles

editing cell alignment:

| Left-aligned | Center-aligned | Right-aligned |
| :---         |     :---:      |          ---: |
| git status   | git status     | git status    |
| git diff     | git diff       | git diff      |

```
| Left-aligned | Center-aligned | Right-aligned |
| :---         |     :---:      |          ---: |
| git status   | git status     | git status    |
| git diff     | git diff       | git diff      |
```

## Even more stuff

you can mention a `@person` or a `@team` on the project like so

you can reference `#suggested_issues` or `#pull_requests` on the project

you can add emojis with `:EMOJICODE:` <br/>
find a list of all the options [here](https://www.webfx.com/tools/emoji-cheat-sheet/) <br/>
:smile: :dragon: :baby_symbol: :shipit: :pizza: :octocat:<br/>
`:smile: :dragon: :baby_symbol: :shipit: :pizza: :octocat:`

Tell Github to ignore markdown formatting with a backslash<br/>
\*\*this is not bold\*\* <br/>
`\*\*this is not bold\*\*`

You can backslash-escape the following characters:
```
\   backslash
`   backtick
*   asterisk
_   underscore
{}  curly braces
[]  square brackets
()  parentheses
#   hash mark
+   plus sign
-   minus sign (hyphen)
.   dot
!   exclamation mark
```
## Images
`![alt text](image url "optional title")`<br/>
I believe this has to be hosted in one of your repos

![baby bird](baby-bird_eric-schmuttenmaer-660x441-300x200.jpg)<br/>
`![baby bird](baby-bird_eric-schmuttenmaer-660x441-300x200.jpg)`
