# vnow

Documentation Extractor for AI Context

<!-- Test sync: 2025-06-15 -->

## Installation

```bash
npm install -g vnow@next
```

> **Note**: `vnow` is currently in pre-release. Use `vnow@next` to get the latest version.

## Commands

### Basic Usage
```bash
# Extract repository documentation
vnow <user/repo>
vnow <github-url>

# Quick workflow commands  
vnow add <user/repo>                  # Download + enable in one command
vnow remove <user/repo>               # Disable + delete completely

# VS Code workspace integration
vnow enable                           # Add docs to VS Code context
vnow disable                          # Remove docs from VS Code context

# Utilities
vnow convert <file>                   # Convert markdown to clean text
vnow format <file>                    # Format text file for AI context
vnow upgrade [--check]                # Upgrade to latest version
vnow --version, -v                    # Show version information
```

## Output Options

- `--min` - Clean text optimized for AI (.min.md)
- `--code` - Code blocks only (.code.md)  
- `--all` - All formats (.md, .min.md, .code.md)

## Popular Frameworks

```bash
vnow sveltejs/svelte                  # Svelte documentation
vnow facebook/react                   # React documentation
vnow vuejs/core                       # Vue.js documentation
vnow solidjs/solid                    # SolidJS documentation
vnow tailwindlabs/tailwindcss         # Tailwind CSS documentation
vnow nextjs/next.js                   # Next.js documentation
vnow remix-run/remix                  # Remix documentation
vnow microsoft/TypeScript             # TypeScript documentation
```

## Testing

```bash
vnow add versionnow/docs              # Try vnow with our test repository
vnow remove versionnow/docs           # Clean up when done testing
```

## Output

- **Files saved to:** ./.vnow/ directory as <user>-<repo>.<format>
- **VS Code settings:** .vscode/settings.json files.exclude  
- **Perfect for:** GitHub Copilot and AI context

For more information: https://github.com/versionnow/docs