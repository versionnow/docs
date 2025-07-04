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
npm i -g vnow@next
```


### ➜ COMMANDS
```bash
vnow <org/repo>                     # Extract or more repo documentation 
vnow add <org/repo>                 # Download + enable in one command
vnow remove <org/repo>              # Disable + delete completely

vnow enable <org/repo>              # Add docs to AI context
vnow disable <org/repo>             # Remove docs from AI context

vnow install                        # Install from vnow.json config
vnow help                           # Show help menu
vnow --version, -v                  # Show version information
```

### ➜ EXAMPLES
```bash
vnow add versionnow/docs            # Try vnow with our docs
vnow add sveltejs/svelte            # Svelte framework docs
vnow add vuejs/docs                 # Vue.js documentation
vnow add reactjs/react.dev          # React documentation
vnow add nextjs/next.js             # Next.js documentation
```

### ➜ OUTPUT OPTIONS
```bash
vnow <org/repo>                     # Standard markdown (.md)
vnow <org/repo> --min               # Clean text optimized for AI (.min.md)
vnow <org/repo> --code              # Code blocks only (.code.md)
vnow <org/repo> --all               # All formats (.md, .min.md, .code.md)

vnow <org/repo> 1                   # 1 level deep
vnow <org/repo> 2                   # 2 levels deep
```

### ➜ CLI SETTINGS
```bash
--vscode                            # Use VS Code settings
--gemini                            # Use Gemini settings
```

### ➜ ALL COMMANDS
```bash
init                                # Initialize vnow.json config file
install [repos...]                  # Install from repositories or config
add [repos...]                      # Add repositories to documentation
remove [repos...]                   # Remove repositories from documentation
enable [repos...]                   # Enable documentation files
disable [repos...]                  # Disable documentation files
version [args...]                   # Show version information
help [command]                      # Show help or command-specific help
upgrade                             # Upgrade to latest version
```

### ➜ OUTPUT LOCATIONS
```bash
Config file:                        # vnow.json
Converted docs:                     # .vnow/
Metadata:                           # .vnow/metadata.json
VScode settings:                    # .vscode/settings.json
Gemini settings:                    # .gemini/settings.json
```

## 🔗 Links

- **Website**: [https://version.now](https://version.now) *(coming soon)*
- **Documentation**: [GitHub](https://github.com/versionnow/docs)
- **Issues**: [Report bugs](https://github.com/versionnow/vnow/issues)
- **Cheatsheet**: [Big List Of Repos](https://docs.google.com/spreadsheets/d/1Yxogakp1UIUSuwyNWboYtmDXifxGtlaoPI6P2NWkFa4/edit?gid=0#gid=0)

---

*Built for developers who work with AI coding assistants* 🤖