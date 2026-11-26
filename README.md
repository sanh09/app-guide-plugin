# app-guide-plugin: a tutor plugin for using the Claude app

**English** | [한국어](README.ko.md)

> **Reply language**: the tutor replies in the language the learner writes in (English, Korean, Japanese, and so on).

A tutor plugin that teaches how to use the Claude **web (claude.ai) and desktop apps** one step at a time, from your first chat to the more advanced features. No coding knowledge is needed.

## Course outline (3 levels, 12 lessons)

- **Basics**: your first chat and a tour of the screen, writing good questions, uploading files and images, web search, Research, and thinking settings
- **Everyday use**: Projects; instructions, memory, past-chat search, and incognito chats; artifacts and file creation; voice mode and mobile
- **Advanced**: connecting apps with connectors, skills, combining features, and using Claude safely and reliably

Each lesson has an explanation, a hands-on exercise in a new chat, and a quiz. Menu paths and feature details are checked against the official help center (https://support.claude.com) as of 2026-11.

## Install

### Option 1. Add it as a plugin (paid plans: Pro, Max, Ultra, Team, Enterprise)

1. In the Claude web or desktop app, open **Customize** in the left menu, then the **Plugins** tab.
2. Choose **Add** → **Add marketplace** → **Add from a repository**, and enter `sanh09/app-guide-plugin`.
3. Find `appguide-tutor` (skill `ai-chat-guide`) in the new marketplace and select **Add**.

Plugins added on the web or desktop are saved to your account and also carry over to Claude Code signed in with the same account. If your organization restricts marketplaces, ask your admin.

### Option 2. Add it as a skill (Free plan included)

1. Download [`dist/ai-chat-guide-skill.zip`](dist/ai-chat-guide-skill.zip) (open the file, then "Download raw file"). Don't unzip it.
2. Go to **Customize** → **Skills** → **"+"** → **"+ Create skill"** → **"Upload a skill"** and upload the file.
3. Check that the skill is turned on in the list.

Skills need code execution (file creation) turned on in settings. Add **either** the plugin or the skill, not both. With both, the same tutor shows up twice.

### Uploading the plugin file directly

For setups that need a direct upload, the plugin archive [`dist/ai-chat-guide-plugin.zip`](dist/ai-chat-guide-plugin.zip) is also provided.

## Usage

Start a new chat and say something like:

- "I'm new to Claude. Show me how to use it"
- "What are Projects?"
- "How do I turn off memory?"
- "How do I connect my apps to Claude?"
- "Give me a quiz on using Claude"

If you added it as a plugin, you can also call it directly with `/appguide-tutor:ai-chat-guide`.

## What the plugin does

- It only adds one skill (instructions and reference files). There are no hooks, MCP servers, or scripts, and it doesn't send data anywhere.
- It doesn't save your progress. In a new chat, the tutor asks where you want to start.

## Structure

```
.claude-plugin/marketplace.json            marketplace definition (sanh09-app-guide)
plugins/ai-chat-guide/
  .claude-plugin/plugin.json               plugin definition
  README.md, README.ko.md
  LICENSE, LICENSE-CC-BY-4.0, NOTICE      licenses (code MIT, content CC BY 4.0)
  skills/ai-chat-guide/
    SKILL.md                               tutor rules
    references/curriculum.md               lessons 1–12, exercises, quiz bank
    references/quiz-answers.md             quiz answer key (read only when grading)
    references/facts.md                    menu paths and features checked against the help center
dist/
  ai-chat-guide-skill.zip               for skill upload
  ai-chat-guide-plugin.zip              for plugin upload
```

After editing, raise `version` in `plugin.json` and rebuild the archives in `dist/`.

## Related repositories

- Claude Code courses in the Claude app: https://github.com/sanh09/guide-protocol
- Claude Code courses inside Claude Code: https://github.com/sanh09/code-guide-protocol

## Release notes

### 2026-11-26: Dual license (code MIT, content CC BY 4.0)
- Code stays under MIT; the tutor content is now under CC BY 4.0. See [License](#license) and [`NOTICE`](NOTICE).
- The plugin folder and both `.zip` files in `dist/` now include `LICENSE`, `LICENSE-CC-BY-4.0` and `NOTICE` (0.4.2). Nothing changes in how the tutor teaches.

### 2026-11-25: `-ko` dropped from the name (0.4.0, action needed)
- The plugin and skill are renamed from `ai-chat-guide-ko` to `ai-chat-guide`. The tutor still replies in the learner's language.
- The plugin is named `appguide-tutor` and holds the skill `ai-chat-guide` (0.4.1). The short name was too close to existing directory listings.

**If you added the old name, add it again** (refreshing can't move you to a new name):
- Added as a plugin: in Customize > Plugins, remove `ai-chat-guide-ko`, refresh the `sanh09-app-guide` marketplace, and add `appguide-tutor`.
- Added as a skill: in Customize > Skills, delete `ai-chat-guide-ko` and upload [`dist/ai-chat-guide-skill.zip`](dist/ai-chat-guide-skill.zip).

### 2026-11-25: English README and license
- The README is now in English by default, with the Korean version in [README.ko.md](README.ko.md). The plugin folder has its own README and LICENSE.

### 2026-11-25: Projects facts corrected (0.3.1)
- The tutor now says Projects are available to every user, Free included, and that the Free plan can create up to 5 projects. Before, it described project instructions as a paid feature.
- This repository is now the only home of `ai-chat-guide-ko`. It was removed from guide-protocol.

### 2026-11-25: Replies in the learner's language (0.3.0)
- The tutor replies in the language the learner writes in. Translated quizzes keep the meaning of each option, and grading compares meanings.

### 2026-11-25: Quiz answers no longer leak (0.2.0)
- Fixed quiz answers showing up in the question, examples, or hints. Answers now live in `references/quiz-answers.md` and are read only when grading.
- Options are shuffled every time, and answer-format examples use placeholders only, such as `1-?, 2-?`.
- Quiz cards put the answer only in the answer field and open in quiz mode. Quizzes are never asked with multiple-choice question buttons.

**How to update**
- Added as a plugin: in Customize > Plugins, refresh the `sanh09-app-guide` marketplace, or remove the plugin and add it again.
- Added as a skill: in Customize > Skills, delete the old skill and upload `dist/ai-chat-guide-ko-skill.zip` again.

Full change log: https://github.com/sanh09/code-guide-protocol/blob/main/maintenance/CHANGELOG.md

## Contributing

Changes go through pull requests, not direct pushes to `main`. Make a branch, edit, and merge the PR once checks such as `claude plugin validate .` pass. The automatic updates follow the same flow. Details: https://github.com/sanh09/code-guide-protocol/blob/main/maintenance/MAINTENANCE.md

## Maintenance

Rebuild the `dist/` files with `bash scripts/build-dist.sh`. The update procedure and records are in https://github.com/sanh09/code-guide-protocol/tree/main/maintenance

## License

This project uses two licenses:
- **Code** — shell scripts (`*.sh`) and JSON/YAML configuration files — is under the [MIT License](LICENSE). Code examples inside the lessons may also be used under MIT.
- **Content** — `SKILL.md`, the reference files (lessons, facts, quizzes, answer keys), evals, READMEs, maintenance documents and images — is under [Creative Commons Attribution 4.0 (CC BY 4.0)](LICENSE-CC-BY-4.0).

When you reuse the content, credit it like this: `app-guide-plugin by sanh09 (https://github.com/sanh09/app-guide-plugin), CC BY 4.0`. [`NOTICE`](NOTICE) has the details and the note on Anthropic trademarks. The plugin folder and every `.zip` in `dist/` include all three files.
