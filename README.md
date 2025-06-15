# vnow

🚀 **AI-Powered Documentation Extractor & VS Code Integration**

Transform GitHub repositories into AI-ready documentation with automatic version tracking, VS Code Copilot integration, and intelligent file management.

<!-- Sync date: 2025-06-15 -->

## ✨ Key Features

- **🤖 VS Code Copilot Integration**: Seamlessly add repository docs to your AI context
- **📦 Versioned File Management**: Automatic semantic versioning with metadata tracking  
- **🎯 Multiple Output Formats**: Standard, minified, and code-only documentation
- **⚡ Smart Workflows**: One-command install + enable, remove + cleanup
- **🔄 Auto-Updates**: Daily version checking with upgrade notifications
- **📊 Detailed Statistics**: File counts, sizes, tokens, and processing metrics

## 📦 Installation

```bash
npm install -g vnow@next
```

> **Note**: Currently in pre-release. Use `vnow@next` for latest features.

## 🚀 Quick Start

```bash
# Add repository to your AI context (install + enable)
vnow add facebook/react --all

# Remove completely (disable + delete)  
vnow remove facebook/react

# Manual workflow
vnow facebook/react --all           # Install with all formats
vnow enable facebook/react          # Add to VS Code Copilot
vnow disable facebook/react         # Remove from Copilot
```

## 📋 Commands

### **Repository Management**
```bash
vnow <user/repo>                    # Extract documentation 
vnow <github-url>                   # Works with full GitHub URLs
vnow add <user/repo>                # Install + enable in one command
vnow remove <user/repo>             # Disable + delete completely
```

### **VS Code Integration**  
```bash
vnow enable <user/repo>             # Add to Copilot context
vnow disable <user/repo>            # Remove from Copilot context
vnow enable <user/repo> --all       # Enable all file types
vnow disable <user/repo> --min      # Disable only .min.md files
```

### **File Processing**
```bash
vnow convert <file>                 # Convert markdown to clean text
vnow format <file>                  # Format text for AI context
```

### **Maintenance**
```bash
vnow upgrade [--check]              # Update to latest version  
vnow --version, -v                  # Show current version
vnow --help, -h                     # Show detailed help
```

## 🎛️ Output Formats

| Flag | Format | Description |
|------|--------|-------------|
| *default* | `.md` | Clean markdown documentation |
| `--min` | `.min.md` | Minified text optimized for AI |
| `--code` | `.code.md` | Code blocks and examples only |
| `--all` | *all* | Generate all three formats |

## 🌟 Popular Frameworks & Libraries

```bash
# Frontend Frameworks
vnow sveltejs/svelte                # Svelte documentation  
vnow facebook/react                 # React documentation
vnow vuejs/core                     # Vue.js documentation
vnow solidjs/solid                  # SolidJS documentation

# Full-Stack & Meta-Frameworks  
vnow nextjs/next.js                 # Next.js documentation
vnow remix-run/remix                # Remix documentation
vnow nuxt/nuxt                      # Nuxt.js documentation

# Styling & UI
vnow tailwindlabs/tailwindcss       # Tailwind CSS documentation
vnow chakra-ui/chakra-ui            # Chakra UI documentation

# Development Tools
vnow microsoft/TypeScript           # TypeScript documentation  
vnow denoland/deno                  # Deno runtime documentation
```

## 🧪 Try It Out

```bash
# Test with our documentation repository
vnow add versionnow/docs --all      # Install all formats + enable
vnow disable versionnow/docs        # Remove from Copilot  
vnow enable versionnow/docs --min   # Re-enable just minified version
vnow remove versionnow/docs         # Complete cleanup
```

## 📁 File Management

### **Versioned Filenames**
Files are automatically versioned using semantic versioning:
```
.vnow/
├── facebook-react@18.2.0.md           # Standard documentation
├── facebook-react@18.2.0.min.md       # Minified version  
├── facebook-react@18.2.0.code.md      # Code examples only
└── metadata.json                       # Repository tracking
```

### **VS Code Integration**
Enabled files are automatically added to `.vscode/settings.json`:
```json
{
  "github.copilot.chat.codeGeneration.instructions": [
    { "file": ".vnow/facebook-react@18.2.0.md" },
    { "file": ".vnow/facebook-react@18.2.0.min.md" }
  ]
}
```

## 📊 Statistics & Tracking

Every installation provides detailed metrics:
- **File Count**: Number of pages processed
- **Size Information**: File sizes in MB and character counts  
- **Token Estimates**: Approximate AI token usage
- **Processing Time**: Installation duration
- **Version History**: Track updates with automatic metadata

## 🔧 Advanced Usage

### **Custom Organization**
```bash
vnow facebook/react 2 custom-name    # Custom directory structure
vnow facebook/react 0                # No subdirectory depth limit
```

### **Batch Operations**  
```bash
# Install multiple repositories
vnow add sveltejs/svelte --all
vnow add facebook/react --min  
vnow add vuejs/core --code

# Enable all at once  
vnow enable sveltejs/svelte
vnow enable facebook/react
vnow enable vuejs/core
```

## 🤝 Contributing & Support

- **Documentation**: https://github.com/versionnow/docs
- **Issues & Feature Requests**: https://github.com/versionnow/vnow/issues  
- **Discussions**: https://github.com/versionnow/vnow/discussions

## 📄 License

MIT License - see [LICENSE](LICENSE) for details.

---

**Perfect for GitHub Copilot, Claude, ChatGPT, and any AI coding assistant!** 🤖✨