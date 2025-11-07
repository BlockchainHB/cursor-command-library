# Cursor Command Library

A collection of reusable custom commands for [Cursor IDE](https://cursor.sh/) that help streamline your development workflow. These commands are designed to be easily integrated into your Cursor workspace and can be customized to fit your specific needs.

## 📚 What are Cursor Commands?

Cursor Commands are custom instructions that you can invoke directly in Cursor IDE to automate common development tasks. They're stored as markdown files in the `.cursor/commands/` directory and can be called using Cursor's command palette.

## 🚀 Getting Started

1. **Clone this repository** or download the commands you need
2. **Copy commands** to your project's `.cursor/commands/` directory
3. **Customize** the commands to match your project structure and preferences
4. **Use** the commands via Cursor's command palette (Cmd/Ctrl + Shift + P)

## 📖 Available Commands

### `commit-feature.md`
A comprehensive workflow for committing features to GitHub with proper changelog management, commit message formatting, and optional issue tracking integration.

**Features:**
- Automatic date verification
- Changelog management
- Conventional commit format
- Branch protection checks
- Issue tracking integration (Linear, Jira, GitHub Issues)

### `create-pr.md`
Streamline your pull request creation process with structured templates and best practices.

**Features:**
- Branch preparation checklist
- PR description templates
- Label and reviewer assignment
- Issue linking

### `gen-image.md`
Generate product images using Replicate's AI image generation models from text prompts.

**Features:**
- Batch image generation from markdown prompts
- Multiple model support (nano-banana, flux, etc.)
- Organized output structure
- Generation reports

### `prime-ui.md`
Create beautiful, modern UI components with best UX practices.

### `weekly-review.md`
Generate a comprehensive summary of codebase changes over the past 7-10 days.

**Features:**
- Commit analysis
- Change categorization (features, bug fixes, tech debt)
- Synthesis of shipped work
- Actionable insights

## 🎥 Learn More

Watch our tutorial video on how to use Cursor Commands:

**https://youtu.be/hkhrfvGaFgE?si=SOP67E2hCKr6u7ml**

This video covers:
- How to set up custom commands in Cursor
- How to use and customize these commands
- Best practices for creating your own commands
- Tips and tricks for maximizing productivity

## 🤝 Contributing

We welcome contributions! If you have a useful Cursor command that others might benefit from, please:

1. **Fork** this repository
2. **Create** your command file in `.cursor/commands/`
3. **Follow** the existing command format and structure
4. **Submit** a pull request with a clear description

### Command Format Guidelines

- Use clear, descriptive titles
- Include an Overview section explaining what the command does
- Break down workflows into numbered steps
- Use markdown formatting for readability
- Include examples where helpful
- Make commands generic and reusable (avoid hardcoded paths or personal references)

## 📝 License

This project is open source and available under the MIT License.

## 🙏 Acknowledgments

Thanks to the Cursor IDE team for creating such a powerful development tool, and to all contributors who help make this library better.

---

**Made with ❤️ for the Cursor community**

