# ai-chat-guide-ko: Claude app guide tutor

**English** | [한국어](README.ko.md)

A step-by-step tutor for the Claude web and desktop apps, from your first chat to connectors and skills. Each lesson has a short explanation, an exercise you try in a new chat, and a quiz. It replies in the language you write in, and no coding knowledge is needed.

## Lessons

1. Your first chat and a tour of the screen
2. Writing good questions
3. Uploading files and images
4. Web search, Research, and thinking
5. Projects
6. Making it yours: instructions, memory, past-chat search, and incognito chats
7. Artifacts and creating files
8. Voice mode and mobile
9. Connecting apps with connectors
10. Skills
11. Combining features
12. Using Claude safely and reliably

## How to start

Start a conversation and say what you want to learn, for example:

- "I'm new to Claude. Show me how to use it"
- "What are Projects?"
- "How do I turn off memory?"

Menu paths, commands, and settings are checked against the official documentation and kept in `skills/ai-chat-guide-ko/references/facts.md`. Quiz answers are kept in a separate file and read only when grading, so they are not shown before you answer.

## Install

In the Claude web or desktop app: **Customize** → **Plugins** → **Add** → **Add marketplace** → **Add from a repository**, enter `sanh09/app-guide-plugin`, then add `ai-chat-guide-ko`.

## What it does

- It adds one skill: instructions and reference files. It has no hooks, MCP servers, or scripts, and it sends no data anywhere.
- It doesn't save your progress. In a new chat, the tutor asks where you want to start.

## Source and license

Source, release notes, and other courses: https://github.com/sanh09/app-guide-plugin

License: MIT. See [LICENSE](LICENSE).
