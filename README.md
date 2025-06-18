# vnow

🚀 **AI-Powered Documentation Extractor & VS Code Integration**

Transform GitHub repositories into AI-ready documentation with automatic version tracking, VS Code Copilot integration, and intelligent file management.

<!-- Sync date: 2025-06-18 -->

## ✨ Key Features

- **🤖 VS Code Copilot Integration**: Seamlessly add docs to your AI context
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
vnow add sveltejs/svelte --all

# Remove completely (disable + delete)  
vnow remove sveltejs/svelte

# Manual workflow
vnow sveltejs/svelte --all           # Install with all formats
vnow enable sveltejs/svelte          # Add to VS Code Copilot
vnow disable sveltejs/svelte         # Remove from Copilot
```

## 📋 Commands

### **Repository Management**
```bash
vnow <name/repo>                    # Extract documentation 
vnow <github-url>                   # Works with full GitHub URLs
vnow add <name/repo>                # Install + enable in one command
vnow remove <name/repo>             # Disable + delete completely
```

### **VS Code Integration**  
```bash
vnow enable <name/repo>             # Add standard .md files to Copilot
vnow disable <name/repo>            # Remove all files from Copilot
vnow enable <name/repo> --all       # Enable all file types (.md, .min.md, .code.md)
vnow enable <name/repo> --min       # Enable only minified .min.md files
vnow enable <name/repo> --code      # Enable only code .code.md files
vnow disable <name/repo> --min      # Remove only .min.md files from Copilot
vnow disable <name/repo> --code     # Remove only .code.md files from Copilot
```

> **Note**: `enable` adds files to VS Code Copilot context. `disable` only removes from VS Code settings (files remain). Use `remove` to delete files completely.

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
vnow sveltejs/kit                   # SvelteKit documentation
vnow vuejs/docs                     # Vue.js documentation
vnow reactjs/react.dev              # React documentation

# Full-Stack & Meta-Frameworks  
vnow nextjs/next.js                 # Next.js documentation
vnow nuxt/nuxt                      # Nuxt.js documentation

# Styling & Development Tools
vnow tailwindlabs/tailwindcss.com   # Tailwind CSS documentation
vnow microsoft/TypeScript-wiki      # TypeScript documentation
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
├── sveltejs-svelte@4.2.8.md           # Standard documentation
├── sveltejs-svelte@4.2.8.min.md       # Minified version  
├── sveltejs-svelte@4.2.8.code.md      # Code examples only
└── metadata.json                       # Repository tracking
```

### **VS Code Integration**
Enabled files are automatically added to `.vscode/settings.json`:
```json
{
  "github.copilot.chat.codeGeneration.instructions": [
    { "file": ".vnow/sveltejs-svelte@4.2.8.md" },
    { "file": ".vnow/sveltejs-svelte@4.2.8.min.md" }
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

### **Directory Depth Control (maxDepth)**
Control how deep vnow processes subdirectories in repositories:

```bash
# Default: Process 2 levels deep
vnow reactjs/react.dev               # Processes /docs/ and /docs/subdirs/

# Custom depth: Process 3 levels deep  
vnow reactjs/react.dev 3             # Processes /docs/subdirs/subsubdirs/

# Unlimited depth: Process all directories
vnow reactjs/react.dev 0             # Processes entire repository structure

# With custom name and depth
vnow reactjs/react.dev 2 my-react-docs  # 2 levels deep, custom directory name
```

**maxDepth Examples:**
- `maxDepth: 1` → Only top-level files (README.md, docs/file.md)
- `maxDepth: 2` → Two levels deep (docs/guide/setup.md) **[DEFAULT]**
- `maxDepth: 3` → Three levels deep (docs/guide/advanced/tips.md)
- `maxDepth: 0` → No limit (processes entire repository)

### **VS Code File Management**
Understand how enable/disable affects your Copilot context:

```bash
# Repository lifecycle
vnow add reactjs/react.dev --all     # Install + auto-enable .md files
vnow enable reactjs/react.dev --min  # Add .min.md files to context  
vnow enable reactjs/react.dev --code # Add .code.md files to context
vnow disable reactjs/react.dev --min # Remove only .min.md from context
vnow disable reactjs/react.dev       # Remove all files from context
vnow remove reactjs/react.dev        # Delete files + remove from context
```

**File States:**
- **Installed**: Files exist in `.vnow/` directory
- **Enabled**: Files are active in VS Code Copilot context  
- **Disabled**: Files exist but not in Copilot context
- **Removed**: Files deleted completely

### **Custom Organization**
```bash
vnow reactjs/react.dev 2 custom-name # Custom directory structure
vnow reactjs/react.dev 0             # No subdirectory depth limit
```

### **Batch Operations**  
```bash
# Install multiple repositories with different formats
vnow add sveltejs/svelte --all       # All formats + enable standard .md
vnow add reactjs/react.dev --min     # Minified only + enable .min.md  
vnow add vuejs/docs --code           # Code only + enable .code.md

# Fine-tune Copilot Context
vnow enable sveltejs/svelte --all    # Enable all Svelte file types
vnow enable reactjs/react.dev        # Enable standard React docs
vnow disable vuejs/docs --code       # Remove Vue code examples from context
```

## 🤝 Contributing & Support

- **Documentation**: https://github.com/versionnow/docs
- **Issues & Feature Requests**: https://github.com/versionnow/vnow/issues  
- **Discussions**: https://github.com/versionnow/vnow/discussions

## 📄 License

MIT License - see [LICENSE](LICENSE) for details.

---

**Perfect for GitHub Copilot, Claude, ChatGPT, and any AI coding assistant!** 🤖✨