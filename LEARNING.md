## Installation
`npm install -g @anthropic-ai/claude-code`
This will install claude code on your system

### to start using claude code
`cd your-project
claude`
This will enable claude code in your project and you can use it to do various tasks

#### 1. Debug and fix your issues
#### 2. Automate tasks that take time are and not worth wasting time on.
#### 3. Build features from descriptions 
#### 4. Navigate code base with the MCP

It works in the terminal helping developers not switch tabs XD


There are multiple Slash commands that come with claude-code
To setup in the terminal we would first use
`/terminal-setup`

## Init
`/init` - Initialize a new CLAUDE.md with codebase documentation.

CLAUDE.md with have the codebase documentation when we run /init with the latest remarks, but if there is a change in the packages, project sturcture or anything that bothers the claude, it should be updated for better output.

## Hash
while interacting with the claude via terminal, if we want to provide some rules or remark that needs to be stored in the CLAUDE.md either locally or repo level, we might enter it using a `#`
Example
`# when making new page components, always add a link to that page in the header`
Using # it will know that it has to store it in the markdown, but will ask whether in Project memory(CLAUDE.md) or local memory of project (CLAUDE.local.md) or user memory (.claude/CLAUDE.md)

## Memory
`/memory`
Used to edit memory files present in the project
#### Project memory(CLAUDE.md)
#### local memory of project (CLAUDE.local.md)
#### user memory (.claude/CLAUDE.md)


## Context
Giving context to claude helps getting better results as the section of code it has to work in gets clearer.
We can provide the context by tagging the files/folders available in the project. We can tag them using `@`.
Example
`@src\components\buttons\` this will set the folder buttons in `src\components\` as context.
likewise
 `@src\components\buttons\buttons.js` this will set the file buttons.js in `@src\components\buttons\` as context.


 ### How to keep context clean
 #### 1. Provide only necessary files and avoid unnecessary context.
 #### 2. `/exit` - exits the chat session completely.
 #### 3. `/clear` - clears the entire session context completely and chat history.
 #### 4. `/compact` - compacts the chat & context into a small summary.
 #### 5. Press ESC twice - Rewind to a previous point in the session.


 ### Context Window
 #### Claude code can handle 200K tokens worth of context, where 1 token is 3-4 characters in a word.
 #### Efficiency of claude code drops as the context window fills, so to clean the context, use the methods given above.


 ## Tools
 ### Claude can do multiple types of tasks with the following tools:
 #### Bash
 #### Edit
 #### Glob
 #### grep
 #### LS
 #### MultiEdit
 #### NotebookEdit
 #### NotebookRead
 #### Read
 #### Task
 #### TodoWrite
 #### WebFetch
 #### WebSearch
 #### Write


 ## Planning
Planning is when claude puts together its plan of action on how intense to implement some features and asks you to approve it.

we can switch to plan mode using 'alt + m'
This will help interacting with discussions with claude and then it will give its solution, which then can be corrected like an response and we can give the permission for the relevant change scope.

It is ideally preferred where the scope is bigger, logic is smaller and we need to apply changes at scale.

 ## Thinking
 When we ask claude code to think about solutions before writing any code.

This would also work in the plan mode like the Planning section
but here the prompt should have keywords like Think hard, implement, etc.
Where it should be self explanatory but well communicated that this problem statement needs thinking

It is ideally preferred where the logic is tough, thinking is required, scope doesnt matter, the code can be small, the changes might not be applied to every file but the logic impacts the overall performance of the site.

### Key
'Think hard' would trigger more thinking than 'Think', it would trigger smaller amount of thinking and reasoning

we can use 'Think harder' to get more thinking and reasoning and 
'ultrathink' to get the most thinking

But this will proportionally use the tokens.