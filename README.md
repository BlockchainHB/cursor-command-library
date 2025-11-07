# Cursor Command Library
### Stop Prompting. Start Building with SOPs.

<div align="center">

[![YouTube Tutorial](https://img.shields.io/badge/YouTube-Tutorial-red?style=for-the-badge&logo=youtube)](https://youtu.be/hkhrfvGaFgE)
[![MIT License](https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=for-the-badge)](CONTRIBUTING.md)

*Production-grade custom commands for Cursor IDE. Built by the founding dev at LaunchFast.*

[🎯 Why Commands?](#why-cursor-commands) • [⚡ Quick Start](#quick-start) • [📚 Command Library](#command-library) • [🎥 Video Tutorial](#video-tutorial)

</div>

---

## Why Cursor Commands?

You're building with Cursor, but you're repeating the same prompts every single day. Every commit is the same explanation. Every code review is more typing, more context, more waiting.

**The problem isn't Cursor—it's that you're treating it like a chatbot instead of a team member who needs SOPs.**

Cursor custom commands transform your best prompts into reusable workflows. Build them once, and three things happen:

1. **Consistent Results** → Same input, same output, every time
2. **Team Alignment** → Commit commands to git. No more "how did you get Cursor to do that?"
3. **AI Agent SOPs** → Your AI teammate gets standardized operating procedures

Because commands are just markdown files, you can measure them, iterate them, and improve them. Your commands get better, and so does your codebase.

> **From the Builder:** These commands power LaunchFast, which hit $22k MRR in 90 days. They've been battle-tested on a production SaaS codebase serving 365+ customers.

---

## Quick Start

### Installation
```bash
# Clone the library
git clone https://github.com/BlockchainHB/cursor-command-library.git

# Copy commands to your project
cp -r cursor-command-library/.cursor/commands/ .cursor/

# Or cherry-pick specific commands
cp cursor-command-library/.cursor/commands/commit-feature.md .cursor/commands/
```

### Usage

1. Open Cursor Settings → **Rules, Memories, Commands**
2. Commands are auto-loaded from `.cursor/commands/`
3. Invoke with `/` in chat or composer:
   - `/prime-ui` → Load UI context
   - `/commit-feature` → Full commit workflow
   - `/gen-image` → Batch image generation

**Pro Tip:** Store shared commands at project level, personal commands at user level.

---

## Command Library

### 🎯 Level 1: Prime Commands
*Prep your agent with the right context before feature work.*

#### `/prime-ui`
Loads your entire UI layer—layout conventions, navigation patterns, component library—so the agent doesn't hallucinate your design system.

**Use when:** Starting any frontend feature work
```markdown
Task: Load UI context for layout and component work
Workflow: 
  1. Read src/components/layout/*
  2. Review navigation patterns
  3. Analyze dashboard composition
Output: Structured markdown summary
```

---

### ⚙️ Level 2: Workflow Commands
*Control the agent's execution path with variables and validation.*

#### `/commit-feature`
End-to-end commit workflow: changelog → branch check → commit → push → issue update.

**Handles:**
- ✅ Date verification (agents often get this wrong)
- ✅ Changelog management with proper formatting
- ✅ Branch protection (won't push to main)
- ✅ `git diff` scoping (only commits relevant files)
- ✅ Linear/Jira/GitHub issue updates
- ✅ Conventional commit format

**What used to take 5+ prompts now takes one command.**
```bash
# Before: Manual prompting
"Check the date"
"Write a changelog"
"Make sure we're not on main"
"Commit with proper format"
"Update the Linear issue"

# After: One command
/commit-feature
```

#### `/create-pr`
Structured PR creation with templates, label assignment, and reviewer tagging.

---

### 🤖 Level 3: Autonomous Commands
*Let the agent run loops with variables.*

#### `/gen-image`
Batch generate images from a markdown prompt file using Replicate MCP.

**Perfect for:**
- Marketing agencies mass-producing ad variants
- Product teams iterating on hero images
- Design systems exploring visual directions

**The loop:**
1. Reads your prompt file (`image-prompts.md`)
2. Generates images via Replicate
3. Saves with corresponding prompts
4. Creates summary report
5. Opens output folder

**Walk away and let it run.**
```markdown
# image-prompts.md
1. A futuristic dashboard with gradient cards
2. Minimalist mobile app hero section
3. SaaS landing page with 3D elements
```

---

### 📊 Analysis Commands

#### `/weekly-summary`
Synthesizes 7-10 days of commits into a structured report:
- Features shipped
- Bug fixes
- Tech debt addressed
- Actionable insights

**Great for:** Standup prep, investor updates, non-technical co-founder briefings

---

## The 3-Level Framework

| Level | What | When | Example |
|-------|------|------|---------|
| **Level 1** | Prime Commands | Prep agent context | `/prime-ui` |
| **Level 2** | Workflow Commands | Multi-step processes with validation | `/commit-feature` |
| **Level 3** | Autonomous Commands | Loops with variables | `/gen-image` |

**Start with Level 1.** Replace the prompts you type daily. Once you're comfortable, add controls (Level 2), then loops (Level 3).

---

## Video Tutorial

<div align="center">

[![Cursor Commands Tutorial](https://img.youtube.com/vi/hkhrfvGaFgE/maxresdefault.jpg)](https://youtu.be/hkhrfvGaFgE)

**Watch the full breakdown:** How I use Cursor commands to build LaunchFast

</div>

In this video, you'll learn:
- ✅ How to set up your first command in 3 minutes
- ✅ The 3 levels of commands (with real production examples)
- ✅ When to turn a workflow into a command (5-step audit)
- ✅ How commands transformed LaunchFast from vibe coding to agentic engineering

---

## Command Structure

All commands follow this template for consistency:
```markdown
# Task
Brief summary of what this command does

# Workflow
1. Step one with specific file paths
2. Step two with validation checks
3. Step three with variables: ${VARIABLE_NAME}

# Output
- Structured markdown response
- File updates (changelogs, reports)
- Third-party updates (Linear, Notion)
```

**Why this structure?**
- Agents understand tasks → workflows → outputs
- Easy to version control and diff
- Teams can iterate on command quality over time

---

## Contributing

Have a command that saves you hours? Share it.

1. Fork this repo
2. Add your command to `.cursor/commands/`
3. Follow the structure above
4. Submit a PR with:
   - Command use case
   - Before/after workflow comparison
   - Any MCP or tool dependencies

**Quality bar:**
- ✅ Generic and reusable (no hardcoded paths)
- ✅ Clear task/workflow/output sections
- ✅ Tested on a real codebase
- ✅ Includes inline comments for customization

---

## Best Practices

### 🎯 Command Scope
- **Project commands** → Specific to that codebase (store in `.cursor/commands/`)
- **User commands** → Used across all projects (store in global Cursor settings)
- **Team commands** → Commit to git, share via team dashboard

### 🔧 Variables
Use `${VARIABLE}` for dynamic inputs:
```markdown
Changelog location: ${CHANGELOG_PATH:./docs/changelog.md}
```

### 🛡️ Validation
Always validate before destructive operations:
```markdown
1. Verify current branch is not 'main'
2. If main → STOP and warn user
3. If feature branch → continue
```

### 📊 Measuring Success
Commands are SOPs. Track:
- Time saved per command invocation
- Consistency of output across team
- Reduction in back-and-forth prompting

---

## FAQ

**Q: Do commands use extra context tokens?**  
A: Yes, but strategically. Use project-level commands only when relevant to that workspace. Global commands consume tokens across all chats.

**Q: Can commands call other commands?**  
A: Not directly, but you can structure workflows to suggest next commands: "Now run `/commit-feature` to finalize."

**Q: What about MCP dependencies?**  
A: Commands like `/gen-image` require MCPs (Replicate, Linear). Install MCPs first, then commands will detect them.

**Q: How do I share commands with my team?**  
A: Commit `.cursor/commands/` to your repo. Everyone on your team gets the same SOPs.

---

**Connect:**
- 🐦 Twitter: [@BlockchainHB](https://twitter.com/BlockchainHB)
- 📺 YouTube: [Cursor Commands Tutorial](https://youtu.be/hkhrfvGaFgE)
- 🚀 LaunchFast: [launchfast](https://launchfastlegacyx.com)

---

## License

MIT © [BlockchainHB](https://github.com/BlockchainHB)

Built with ❤️ for the Cursor community.

**Prompts are the new functions. Build them once. Use them forever.**
