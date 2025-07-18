# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.29.0] - 2025-07-05 - 2025-07-05

### Minor Changes (x.1.x)
- **Update Command**: Added `vnow update` command to update all repositories to their latest versions with smart change detection
- **Source Array Permanent Record System**: Refactored vnow.json source array to be a permanent record of downloaded repositories, only modified during download (install/add/enable) or removal operations
- **Simplified Enable/Disable Logic**: Enable and disable commands now only affect AI context settings, never modify the source array, providing cleaner separation of concerns
- **Centralized Source Management**: Created `sourceManager.ts` utility with `addToConfigSource` and `removeFromConfigSource` functions using metadata `srcPath` as canonical values

### Patch Changes (x.x.1)
- **Install Stats Bug Fix**: Fixed install command showing duplicate file counts when multiple CLI tools are configured (vscode + gemini)
- **Install Scope Bug Fix**: Fixed install command showing all enabled files instead of only files from repositories in vnow.json source array
- **Clean Command Safety Rule**: Added mandatory git commit requirement before running clean commands to prevent data loss
- **Enhanced Test Coverage**: Added comprehensive source array behavior tests ensuring enable/disable preserve source while install/add/remove modify it appropriately
- **Silent Source Updates**: Source manager now supports silent mode to prevent verbose logging during batch operations

### 🛠️ Technical Improvements

**Source Array Management**
- **Permanent Record**: Source array represents actual downloaded repositories, not temporary enable/disable state
- **Metadata Integration**: Uses `srcPath` from metadata as canonical source of truth for array entries  
- **Centralized Logic**: Single utility handles all source array modifications with consistent error handling
- **No Auto-Cleanup**: Manual edits and mismatches between metadata and source are preserved without validation

**Command Behavior Changes**
- **Install/Add Commands**: Always add successful downloads to source array using centralized utility
- **Enable Command**: Downloads missing repos and adds to source, but existing repos only affect settings
- **Disable Command**: Never modifies source array, only removes from AI context settings
- **Remove Command**: Only command that removes entries from source array, uses centralized utility

## [1.0.0-next.27] - 2025-07-04 - 2025-07-04 - 2025-07-04 - 2025-07-04 - 2025-07-04 - 2025-07-04

### Minor Changes (x.1.x)
- **JSON Schema IntelliSense**: Added comprehensive JSON schema support for `vnow.json` configuration files with autocomplete, validation, and hover documentation
- **Auto-Generated Schema Integration**: Integrated schema generation into build process with TypeScript-based schema definitions that auto-generate JSON schemas
- **Enhanced CLI Settings Support**: Added robust support for both VS Code and Gemini CLI tools with flag-based configuration (`--vscode`, `--gemini`, `--all`)
- **Config-Based Installation**: Added `vnow install` command to automatically install all repositories listed in `vnow.json` source array
- **Initialization Command**: Added `vnow init` command to create clean configuration files with schema references and user-selected CLI tools

### Patch Changes (x.x.1)
- **DRY Config Management**: Unified all config file operations to use single `saveConfig()` function, ensuring consistent clean output with only essential fields
- **Settings File Comma Handling**: Fixed JSON comma syntax issues in VS Code and Gemini settings files when adding multiple repositories across organizations
- **Schema Build Integration**: Automated schema generation during `deno task build` process for consistent development workflow
- **Clean Config Output**: Config files now only include user-relevant fields (`$schema`, `settings`, `source`) without internal configuration clutter
- **Type Safety Improvements**: Resolved TypeScript errors in config handling with proper type definitions and centralized functions

### 🛠️ Technical Improvements

**IntelliSense & Developer Experience**
- **TypeScript Schema Definition**: Created `src/schema/schema.ts` with comprehensive schema definitions
- **Build-Time Generation**: Schema auto-generates during build process ensuring consistency
- **VS Code Integration**: Full autocomplete support for configuration properties with pattern validation
- **Error Prevention**: Real-time validation prevents invalid repository formats and settings

**Configuration Architecture**
- **Essential Fields Only**: Generated config files contain only `$schema`, `settings`, and `source` properties
- **Schema Reference**: All config files include `$schema` property for IDE support
- **CLI Tool Flexibility**: Support for multiple CLI tools with individual or combined configuration
- **Default Handling**: Smart defaults with VS Code as primary target, extensible to other tools

## [1.0.0-next.23] - 2025-06-26 - 2025-06-25 - 2025-06-25 - 2025-06-25 - 2025-06-24 - 2025-06-18 - 2025-06-18

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
- Automated documentation sync to versionnow/+docs repository during publish process
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