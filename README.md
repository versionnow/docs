# vnow

Convert any GitHub repository to a single markdown file for AI Context

## ✨ Features

- **🤖 VS Code Copilot Integration** - Auto-add to AI context
- **🤖 Gemini CLI Integration** - Auto-add to AI context
- **📦 Smart Docs Management** - Versioned, organized output  
- **⚡ One-Command Workflows** - Install + enable context in one step
- **🎯 Multiple Formats** - Standard, minified, code-only

## 📦 Installation

```bash
npm i -g vnow                       # Install Globally
npx vnow                            # Run Instantly
```

### ➜ COMMANDS
```bash
vnow init                           # Initialize vnow config file
vnow install, i                     # Install from config 
vnow update                         # Update repos
vnow list                           # Lists enabled/disabled docs

vnow <org/repo>                     # Download repo docs
vnow add <org/repo>                 # Download + enable
vnow remove <org/repo>              # Remove + disable

vnow enable <org/repo>              # Enable docs in settings
vnow disable <org/repo>             # Disable docs from settings

vnow use vscode gemini              # Enables settings globally

vnow help                           # Show help menu
vnow upgrade                        # Upgrade to latest version
vnow --version, -v                  # Show version info
```

### ➜ DEMOS
```bash
vnow versionnow/docs                # Version Now docs

vnow sveltejs/svelte                # Svelte docs
vnow sveltejs/kit                   # SvelteKit docs
vnow vuejs/docs                     # Vue.js docs
vnow nuxt/nuxt                      # Nuxt docs
vnow reactjs/react.dev              # React docs
vnow nextjs/next.js                 # Next.js docs
vnow microsoft/TypeScript-wiki      # TypeScript docs
vnow tailwindlabs/tailwindcss.com   # Tailwind docs
```

### ➜ OPTIONS
```bash
vnow <org/repo> 1                   # One level deep
vnow <org/repo> 2                   # Two levels deep
vnow <org/repo> 100                 # Many levels deep!

vnow <org/repo>                     # Standard markdown (.md)
vnow <org/repo> --min               # Clean text optimized for AI (.min.md)
vnow <org/repo> --code              # Code blocks only (.code.md)
vnow <org/repo> --all               # All formats 

vnow <command> --vscode             # VS Code Settings override
vnow <command> --gemini             # Gemini Settings override
```

### ➜ OUTPUT
```bash
Config file:                        # vnow.json
Converted docs:                     # .vnow/
Metadata:                           # .vnow/metadata.json
VScode settings:                    # .vscode/settings.json
Gemini settings:                    # .gemini/settings.json
```

## 🔗 Links

- **Website**: https://version.now/ *(coming soon)*
- **Documentation**: https://github.com/versionnow/docs
- **Cheatsheet**: [BIG List of Docs](https://docs.google.com/spreadsheets/d/1Yxogakp1UIUSuwyNWboYtmDXifxGtlaoPI6P2NWkFa4/edit?gid=0#gid=0)

---

*Built for developers who work with AI coding assistants* 🤖