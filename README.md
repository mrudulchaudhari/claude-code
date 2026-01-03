# claude-code

Starting 2026 with learning Claude code, how to integrate it with the system, how to maximise productivity and what happens behind the scene

---


# Claude Code Documentation

## Installation

`npm install -g @anthropic-ai/claude-code`

This will install claude code on your system

### To start using claude code

```bash
cd your-project
claude
```

This will enable claude code in your project and you can use it to do various tasks

1. Debug and fix your issues
2. Automate tasks that take time are and not worth wasting time on.
3. Build features from descriptions
4. Navigate code base with the MCP

It works in the terminal helping developers not switch tabs XD

---

## Slash Commands

There are multiple Slash commands that come with claude-code. To setup in the terminal we would first use `/terminal-setup`

### Init

`/init` - Initialize a new CLAUDE.md with codebase documentation.

CLAUDE.md with have the codebase documentation when we run /init with the latest remarks, but if there is a change in the packages, project sturcture or anything that bothers the claude, it should be updated for better output.

### Model

`/model` - Choose between various models in claude

### Permissions

`/permissions` - Choose the changes that you want to allow claude to do automatically and thereafter you it wont ask again for the same in the chat, where as you may remove or add permissions manually inside the settings.local.json for claude permissions in .claude/ directory inside the project.

---

## Memory

`/memory` - Used to edit memory files present in the project

**Memory Types:**
- Project memory (CLAUDE.md)
- Local memory of project (CLAUDE.local.md)
- User memory (.claude/CLAUDE.md)

### Hash

While interacting with the claude via terminal, if we want to provide some rules or remark that needs to be stored in the CLAUDE.md either locally or repo level, we might enter it using a `#`

**Example:**
```
# when making new page components, always add a link to that page in the header
```

Using # it will know that it has to store it in the markdown, but will ask whether in Project memory(CLAUDE.md) or local memory of project (CLAUDE.local.md) or user memory (.claude/CLAUDE.md)

---

## Context

Giving context to claude helps getting better results as the section of code it has to work in gets clearer. We can provide the context by tagging the files/folders available in the project. We can tag them using `@`.

**Example:**
- `@src\components\buttons\` this will set the folder buttons in `src\components\` as context.
- `@src\components\buttons\buttons.js` this will set the file buttons.js in `@src\components\buttons\` as context.

### How to keep context clean

1. Provide only necessary files and avoid unnecessary context.
2. `/exit` - exits the chat session completely.
3. `/clear` - clears the entire session context completely and chat history.
4. `/compact` - compacts the chat & context into a small summary.
5. Press ESC twice - Rewind to a previous point in the session.

### Context Window

Claude code can handle 200K tokens worth of context, where 1 token is 3-4 characters in a word. Efficiency of claude code drops as the context window fills, so to clean the context, use the methods given above.

---

## Tools

Claude can do multiple types of tasks with the following tools:

- Bash
- Edit
- Glob
- grep
- LS
- MultiEdit
- NotebookEdit
- NotebookRead
- Read
- Task
- TodoWrite
- WebFetch
- WebSearch

---

## Planning

Planning is when claude puts together its plan of action on how intense to implement some features and asks you to approve it.

We can switch to plan mode using **'alt + m'**

This will help interacting with discussions with claude and then it will give its solution, which then can be corrected like an response and we can give the permission for the relevant change scope.

**It is ideally preferred where the scope is bigger, logic is smaller and we need to apply changes at scale.**

---

## Thinking

When we ask claude code to think about solutions before writing any code.

This would also work in the plan mode like the Planning section but here the prompt should have keywords like Think hard, implement, etc. Where it should be self explanatory but well communicated that this problem statement needs thinking

**It is ideally preferred where the logic is tough, thinking is required, scope doesnt matter, the code can be small, the changes might not be applied to every file but the logic impacts the overall performance of the site.**

### Key

'Think hard' would trigger more thinking than 'Think', it would trigger smaller amount of thinking and reasoning

We can use 'Think harder' to get more thinking and reasoning and 'ultrathink' to get the most thinking

**But this will proportionally use the tokens.**

---

## Custom Commands

We create custom command to reduce the writing of similar tasks, like giving a context, approach, color grade, for example when we build some frontend component, we are working in same directory, with similar css, so we need not write the context and UI again and again, we may just store it in some custom command

### To create a custom command:

1. Create a commands folder inside .claude/
2. Create a markdown file (.md) named after the desired command name, example ('ui-component.md')
3. Inside the markdown file we made add the details desiredd for example task, variants, testing
4. Run it using /component-name and then one can specify what needs to be done ahead, otherwise it would let the AI decide what is ideal in the current scenario and will make changes accordingly

### Using Arguments

To make custom commands more functional we can pass arguments, example parse $Argument and then later the task which is all mentioned in the markdown, this can be then called with the command name and an argument can be passed. We can store the passed argument in the markdown or basically the custom command using `[var-name]` inside the markdown file

### Adding Metadata

Likewise we can also supply meta data on the top in the form of front data, which markdown allows us to add

**Example:**
```yaml
---
description: something something
argument hint: something | something1
---
```

When we make changes to the custom command file (markdown file), we need to restart the session to experience the changes using `/exit`

---

## MCP and MCP Server

### Model Context Protocol

It gives claude the ability to connect with external data sources, services and API.

```
 _____________       ____________       _________________
|             |     |            |     |                 |
| Claude Code | <-->| MCP Server | <-->| External Source |
|_____________|     |____________|     |_________________|
```

### MCP Servers

#### Supabase MCP

```
 _____________       ____________       _________________
|             |     |  Supabase  |     |                 |
| Claude Code | <-->| MCP Server | <-->|    Supabase     |
|_____________|     |____________|     |_________________|
```

#### Playwright MCP

A MCP server that provides browser automation capabilities using Playwright. This server enables LLM to interact with webpages through structured accessibility snapshots, bypassing the need for screenshots or visually-tuned models.

#### One can install these MCP servers on the local machine by checking out the exact commands of them in either the claude code documentation or of the MCP server documentation. As Anthropic (Parent company of Claude) developed MCP, one would find most MCP servers compatible with Claude Code.

When you install MCP on our project, you would find a .mcp.json file inside the project file.

---

## Subagents

Subagents allow us to create a whole team working on our project where each subagent can have its own expertise. Each subagent can be isolated and configured to work on particular tasks. Example we can create a subagent who expertises and onl works with Unittesting, likewise for security audits or a UX reviewer. All the subagents work independently from each other, they have their own system prompts and their own context windows. Claude code can delegate tasks to subagents.

### Creating a Subagent

We can create a new subagent using `/agent`

Then we can choose the scope of the subagent, Project or Personal. We can also ask claude to generate the configuration or manually do the same.

Once an agent is created one can see inside the .claude folder one can see the agents folder with the markdown file for the agent.

We can mention the Agent in the markdown of a slash command, example if we creating a UI-UX reviewer subagent, we can invoke it last in the markdown of the custom command we created for /ui-component, this will invoke the subagent automatically if we use /ui-component to do any ui changes and our work will get reviewed by the UI-UX reviewer agent, similarly we can use the subagent to build unittests, etc.

**To see the changes we need to /exit and restart the claude session and then we can use the created changes**

---

## Claude Code with Github

We can integrate Claude Code with the github to automate PR reviews. To do this we need Github CLI already installed on the system.

Once installed you need to login using:
```bash
gh auth login
```

Then in the claude chat `/install-github-app` - to set up github actions for repository. Then we can specify the repository. Then it will ask us to install Claude Code on github - there we can install and authorize and also select the repositiories (all or selective) for claude code to work with.

Once done we can see Claude and Claude review in github actions

We can use Claude code to review a PR or work on an issue

### Issue example

Example create an issue titled - Link on the logo mission and description - add link to logo in the navbar to redirect to the homepage

And then create the issue, and in the comment say something like @claude can you fix this and then the claude code will start working

### PR example

When we create a pull request, claude code will automatically check the content inside (the changed files) and to provide better context, we can tag the issue (example #41) for claude to understand better. Once assessed, claude will provide a detailed feedback

We can specify the and restructure what are the musts in the code for example readability, or having simple nested loops so that once a PR is raised, claude will assess and will give a general feedback but also specify if the code is readable, and if it is getting complexed with some nested loops and is there a way to handle it better.

---

## Learnings till now (Summarized)

### This is a personal experience which i got while playing with claude code in my terminal and also the github (during my internship)

### Check the code yourself

Blindly following claude wont help, it might get stuck in its own loop sometimes

**Example** - I got stuck between readability and parameter overuse section in my claude PR review where my code initiall was readable, and it asked me to do a certain changes in parameters (I removed a parameter that wasnt there) but then it asked me to add it back, and then once i added it back it asked me to remove, so this loop kept on going and I had to take a decision and give my code ahead.

### Context is key

Set a context window for better output

**Example** - in my initial practices with AI, I spent high amount of tokens for simple tasks, where I could have simply mentioned the file so that it restricted its scope. So initially I was burning more tokens and also not getting adequate output XD. Clear and crisp context window gives better output and saves you thousands of tokens, sometimes millions (if working on a bigger project).

### Over reliance on AI

It took the control away from me from my code base

The Project i was working on to test Cursor (Similar to Claude code), I created a project, and I took help to create the frontend, but then I lost control over the styling and scripting, because I kept cursor to make changes without reading what it was actually doing. Now I use Claude Code to help me by making me understand the structure, how an engineer thinks, and then do tasks that are redundant example creating unittests (which I know how to create and its just time consuming to create for all functions).

### Claude Code is too powerful

I learned it only while using it

Claude code can literally think like an engineer, it can easily do the tasks that most freshers do (like me), it can create projects, keep track of code, especially Opus 4.5 can do really complex tasks, to design a system and then also hard code it, but what i realised working with any of the Agentic AI is that it can create mistakes, but then the scale at which it does correct things is also helpful. And with coming models, like Gemini 3 pro which is really good in algorithms, according to me the role of an engineer would be to supervise, manage these agents and subagents and would really help good programmers by increasing their efficiency by 10 times or even more.