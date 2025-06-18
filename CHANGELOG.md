# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0-next.18] - 2025-06-18 - 2025-06-18

### Patch Changes (x.x.1)
- **CRITICAL BUG FIX: maxDepth Content Consistency**: Fixed maxDepth logic to ensure identical total content (pages, characters, tokens) regardless of maxDepth value
- **No Content Duplication**: Completely refactored file collection to process each markdown file exactly once, eliminating duplicate content across output files
- **Proper File Grouping**: maxDepth now correctly groups the same total content into different output files based on directory structure, never omitting or duplicating files
- **Enhanced maxDepth Documentation**: Updated help text and README to clarify that maxDepth controls organization, not content filtering
- **Verification Tested**: Confirmed that sum of all output files at any maxDepth matches the single file output at maxDepth=0

## [1.0.0-next.18] - 2025-06-18

### Minor Changes (x.1.x)
- **Componentized Stats Display System**: Created reusable `displayCustomStatsTable()` function with flexible emoji/title support
- **Unified Command Output**: All commands now show consistent, clean stats tables with appropriate emoji indicators
- **Enhanced User Experience**: Streamlined output with minimal verbose messaging - only essential stats tables displayed
- **Professional CLI Polish**: Commands now show `⬇️ DOWNLOADED`, `✅ ADDED/ENABLED`, `❌ DISABLED`, `🗑️ REMOVED` with beautiful formatted tables

### Patch Changes (x.x.1)
- Removed verbose deletion progress messages from remove command
- Cleaned up fallback success messages across all commands  
- Fixed unused imports and improved code maintainability
- Preserved single "Processing..." message for install operations
- Enhanced disable/remove command distinction (disable = settings only, remove = complete cleanup)
- Improved error handling with silent fallbacks instead of verbose messaging

## [1.0.0-next.17] - 2025-06-17 - 2025-06-16

### Patch Changes (x.x.1)
- Fixed version command showing "unknown" when installed via npm
- Fixed upgrade command "Deno.Command is not a constructor" error
- Added Node.js environment detection for npm package compatibility
- Replaced Deno.Command with Node.js child_process.spawn for npm environments

## [1.0.0-next.16] - 2025-06-17 - 2025-06-15 - 2025-06-15 - 2025-06-15

### 🚀 Major Enhancements

**Metadata-Driven Architecture Overhaul**
- **Revolutionary File Management**: Complete migration from legacy `${org}-${repo}` filename logic to metadata-driven, versioned filename system
- **Semantic Versioning Integration**: All files now use format `user-repo@1.0.0.md` with automatic GitHub API version detection
- **Robust Metadata System**: Centralized `.vnow/metadata.json` as the single source of truth for all repository tracking and file management

**Enhanced VS Code Copilot Integration**  
- **Smart Context Management**: `enable` and `disable` commands now use metadata for perfect file resolution
- **Append-Only Logic**: `enable` command appends to existing Copilot context instead of replacing it
- **File Existence Verification**: Only existing files are added to VS Code settings, preventing broken references
- **Automatic Deduplication**: Prevents duplicate entries in `.vscode/settings.json`

**Streamlined Command Workflows**
- **Unified `add` Command**: Now properly passes all flags (`--all`, `--min`, `--code`) to install and automatically enables files
- **Robust `remove` Command**: Uses metadata for complete cleanup - deletes all versioned files and removes from settings  
- **Intelligent `disable` Command**: Removes all files for a repository from Copilot context using metadata lookup
- **Enhanced `enable` Command**: Uses metadata to find and enable all generated file types for a repository

### 🛠️ Technical Improvements

**GitHub API Integration**
- **Real Version Detection**: Fetches actual semantic versions from GitHub releases API instead of using placeholders
- **Fallback Logic**: Graceful handling when API is unavailable or no releases exist
- **Rate Limit Awareness**: Efficient API usage with proper error handling

**File System Robustness** 
- **Atomic Operations**: Install process now has proper error handling with cleanup on failure
- **Backward Compatibility**: Legacy filename cleanup maintained for smooth migration
- **Directory Management**: Improved handling of empty directories and folder cleanup

**Error Handling & User Experience**
- **Comprehensive Validation**: All commands validate file existence before operations
- **Clear Error Messages**: Improved feedback when repositories or files are not found
- **Graceful Fallbacks**: Commands continue working even when metadata is partially corrupted

### ✅ Validation & Testing

**Comprehensive Command Testing**
- All core workflows validated: `add`, `enable`, `disable`, `remove`
- VS Code Copilot integration tested with real repositories
- Metadata consistency verified across multiple install/remove cycles
- File versioning confirmed with semantic version detection

**Quality Assurance**
- Zero legacy filename logic in active code paths (only in cleanup/fallback)
- All commands properly handle edge cases and missing files
- Settings.json integrity maintained across all operations
- Metadata.json serves as reliable source of truth for all file operations

### 🐛 Bug Fixes

- **Fixed**: `enable` command now correctly uses metadata instead of legacy filename guessing
- **Fixed**: `add` command properly passes flags to install and enables the correct generated files  
- **Fixed**: `disable` and `remove` commands use metadata for accurate file identification
- **Fixed**: VS Code settings corruption when enabling/disabling repositories multiple times
- **Fixed**: File deletion edge cases where metadata and actual files were out of sync

### 🧹 Code Quality

**Codebase Cleanup**
- **Legacy Code Removal**: Eliminated most `${org}-${repo}` filename logic throughout the codebase
- **Consistent Architecture**: All commands now use the same metadata-driven approach
- **Test Suite Cleanup**: Removed outdated test files that relied on legacy filename patterns
- **Documentation Sync**: Updated all help text and documentation to match new functionality

**Performance Optimizations**  
- **Reduced File I/O**: Metadata-driven lookups eliminate unnecessary file system scanning
- **Efficient Settings Updates**: Smart VS Code settings management with minimal file writes
- **Faster Command Execution**: Streamlined command logic with reduced redundant operations

### 📚 Documentation

- **Enhanced README**: Comprehensive feature overview with usage examples and advanced scenarios
- **Updated Help System**: All command help text reflects new metadata-driven functionality  
- **Better Examples**: Real-world usage patterns with popular framework repositories
- **Feature Highlights**: Clear documentation of versioned filenames and VS Code integration benefits

## [1.0.0-next.13] - 2025-06-15

### Added
- **Version detection improvements**: Enhanced version commands to work in both Deno and Node.js environments
- **Build system enhancements**: Streamlined build process without postinstall complexity

### Fixed
- Version commands (`vnow --version`, `vnow upgrade --check`) now correctly detect version in npm-installed packages
- Resolved development vs npm version conflicts by improving version detection logic

### Changed
- **Simplified installation**: Removed postinstall and first-run setup for faster, cleaner installation
- **Streamlined build**: Focuses on core functionality without setup automation
- Version detection now checks both `deno.json` (development) and `package.json` (npm) for maximum compatibility

## [1.0.0-next.9] - 2025-06-15

## [1.0.0-next.8] - 2025-06-15

### Minor Changes
- Refactored file generation to replace `.txt` output with `.min.md` format using clean text logic
- Enhanced `vnow enable` and `vnow disable` commands with flag-based behaviors:
  - `vnow enable` (no flags) now enables only `.md` files
  - `vnow disable` (no flags) now disables all file types (.md, .min.md, .code.md)
  - Added `--min`, `--code`, and `--all` flags for granular file type control
- Automated documentation sync to versionnow/docs repository during publish process
- Added version command (`vnow --version`, `vnow -v`) for current version display
- Added upgrade command (`vnow upgrade`) with automatic latest version installation
- Implemented daily automatic version checking with smart notifications

### Patch Changes  
- Updated all help text, documentation, and command descriptions to reflect new file handling logic
- Improved VS Code integration examples in README.md and help output
- Fixed file filtering logic to properly distinguish between `.md`, `.min.md`, and `.code.md` files
- Enhanced error handling and user feedback for enable/disable operations
- Added automatic CHANGELOG version updating during publish process
- Updated help system to include version and upgrade commands
- Implemented user config directory (`~/.vnow/config.json`) for version check persistence

## [1.0.0-next.3] - 2025-06-15

### Minor Changes
- VS Code workspace integration commands (`enable`, `disable`)
- File conversion utilities (`convert`, `format`)
- Comprehensive help system with real examples
- Automated build and publish pipeline for npm
- Documentation sync between README.md and help output

### Patch Changes
- Updated deno.json task names to use `dev:` prefix
- Improved CLI argument parsing and command structure
- Enhanced documentation with VS Code integration examples
- Node.js directory handle warnings (improved resource cleanup)
- Version increment regex for `next` pre-release workflow
- Build script maintainability and DRYness

## [1.0.0-next.2] - 2025-06-14

### Minor Changes
- Initial npm publishing with `@next` dist-tag
- Core documentation extraction functionality
- Support for multiple output formats (md, min.md, txt, code.md)
- GitHub URL and name/repo format parsing

### Patch Changes
- Moved from CLI prototype to production-ready tool
- Implemented modular command architecture

## [1.0.0-next.1] - 2025-06-13

### Minor Changes
- Initial Deno-based CLI implementation
- Basic GitHub repository documentation extraction
- Markdown to text conversion capabilities
- Core file processing utilities

---

## Release Types

### Major Changes (1.x.x)
- Breaking changes to CLI interface
- Major feature additions that change core functionality
- Significant architectural changes

### Minor Changes (x.1.x) 
- New features and commands
- Enhanced functionality that doesn't break existing usage
- Performance improvements

### Patch Changes (x.x.1)
- Bug fixes and improvements
- Documentation updates
- Dependency updates
- Security patches

### Pre-release (x.x.x-next.x)
- Alpha/beta features
- Experimental functionality
- Testing new capabilities before stable release