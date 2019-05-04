# Big Heading
`# Big Heading`

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
* Work
* As well
```
* Asterisks
* Work
* As well
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

Here is how you add a [link](google.com)<br/>
`Here is how you add a [link](google.com)`

You can also add [relative links](docs/contributing.md)<br/>
`You can also add [relative links](docs/contributing.md)`

And [link to anchors](#big-heading)<br/>
`And [link to anchors](#big-heading)`

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

![GitHub Logo](/images/logo.png)
Format: ![Alt Text](url)
