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
