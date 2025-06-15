# vnow

Convert GitHub documentation to searchable markdown files for AI/Copilot context.

<!-- Test sync: 2025-06-15 -->

## Install

```bash
npm install -g vnow@next
```

> **Note**: `vnow` is currently in pre-release. Use `vnow@next` to get the latest version.

### Automatic VS Code Setup

When installed in a VS Code workspace, vnow automatically:
- Downloads vnow documentation (`versionnow/docs`) for context
- Enables it in your workspace settings for Copilot integration
- Provides instant access to vnow command documentation

If automatic setup doesn't work, you can manually run:
```bash
vnow versionnow/docs
vnow enable versionnow/docs
```

## Usage

### Basic Commands

```bash
# Download and convert repository documentation
vnow <user/repo> [options]
vnow <github-url> [options]

# VS Code workspace integration  
vnow enable [--min|--code|--all]   # Enable docs in VS Code context
vnow disable [--min|--code|--all]  # Remove docs from VS Code context

# Utilities
vnow convert <file>               # Convert markdown to clean text format
vnow format <file>                # Format text file for AI context
vnow upgrade [--check]            # Upgrade vnow to latest version
vnow --version, -v                # Show version information
vnow help                         # Show help information
```

### Repository Formats

vnow accepts either `user/repo` format or full GitHub URLs:

```bash
# Repository format
vnow denoland/deno

# GitHub URL format  
vnow https://github.com/sveltejs/svelte/tree/main/documentation/docs

# With output options
vnow sveltejs/kit --all
```

## Examples

### Documentation Extraction

```bash
# Popular documentation repositories
vnow denoland/docs
vnow sveltejs/svelte/documentation/docs  
vnow sveltejs/kit/documentation/docs
vnow tailwindlabs/tailwindcss.com

# Framework documentation
vnow microsoft/TypeScript/doc
vnow nodejs/node/doc
vnow reactjs/react.dev
```

### VS Code Integration

> **Auto-Setup**: When you install vnow globally in a VS Code workspace, it automatically downloads and enables `versionnow/docs` for instant Copilot context.

```bash
# Enable specific repo docs in VS Code
vnow enable versionnow/docs

# Enable only .md files
vnow enable

# Enable only .min.md files  
vnow enable --min

# Enable only .code.md files
vnow enable --code

# Enable all file types
vnow enable --all

# Disable specific repo docs
vnow disable versionnow/docs

# Disable all file types
vnow disable

# Disable only .min.md files
vnow disable --min

# Disable only .code.md files
vnow disable --code

# Disable all file types (same as no flags)
vnow disable --all
```

### Version Management

```bash
# Check current version
vnow --version
vnow -v

# Check for updates
vnow upgrade --check

# Upgrade to latest version
vnow upgrade
```

## Output Formats

- **Default (.md)**: Full markdown with all content
- **Minified (--min)**: Clean text optimized for AI context
- **Code only (--code)**: Just headings and code blocks
- **All formats (--all)**: Generate all output types

## Files and Organization

- **Downloads**: Documentation files are saved to `./.vnow/` directory
- **Naming**: Files use format `<user>-<repo>.<extension>` (e.g., `denoland-docs.md`)
- **VS Code**: Integration modifies `.vscode/settings.json` to include/exclude files

Perfect for feeding documentation context to GitHub Copilot, ChatGPT, or other AI tools.