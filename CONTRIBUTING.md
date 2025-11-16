# Contributing to No Pixie Icon Theme

Thank you for your interest in contributing to No Pixie Icon Theme! This document provides guidelines and instructions for contributing to this project.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Development Workflow](#development-workflow)
- [Commit Message Guidelines](#commit-message-guidelines)
- [Testing Your Changes](#testing-your-changes)
- [Publishing](#publishing)
- [Pull Request Process](#pull-request-process)

## Code of Conduct

By participating in this project, you are expected to uphold a respectful and collaborative environment. Please be considerate and constructive in your interactions with other contributors.

## Getting Started

### Prerequisites

- Node.js (v14 or higher recommended)
- npm or yarn
- Visual Studio Code
- Git

### Setting Up Your Development Environment

1. Fork the repository on GitHub
2. Clone your fork locally:
   ```bash
   git clone https://github.com/YOUR_USERNAME/nopixie-icon-theme.git
   cd nopixie-icon-theme
   ```

3. Install dependencies:
   ```bash
   npm install
   ```

   This will also set up Husky git hooks automatically via the `prepare` script.

4. Create a new branch for your feature or fix:
   ```bash
   git checkout -b feat/your-feature-name
   ```
   or
   ```bash
   git checkout -b fix/your-bug-fix
   ```

## Development Workflow

### Repository Structure

```
nopixie-icon-theme/
   themes/              # Icon theme JSON files
      no-pixie-purple-icon-theme.json
      no-pixie-blue-icon-theme.json
      no-pixie-yellow-icon-theme.json
   icons/               # SVG icon files
   images/              # Extension icon and screenshots
   scripts/             # Build and generation scripts
   .husky/              # Git hooks
   .commitlintrc.json   # Commit message rules
   package.json         # Project metadata and scripts
   README.md
```

### Making Changes

1. **Editing Icon Themes**:
   - **DO NOT** edit icon theme JSON files (`no-pixie-*-icon-theme.json`) directly - they are auto-generated
   - Modify [scripts/generate-icons.js](scripts/generate-icons.js) to change icon designs or add new file types
   - Update the `colorPalettes` object in the script to change icon colors
   - Run `npm run generate-icons` to regenerate all icon files and definitions
   - The script generates:
     - 192 SVG icon files (64 per variant: purple, blue, yellow)
     - 3 icon theme JSON definitions
     - Support for 40+ file types and special folders

2. **Adding New File Type Support**:
   - Edit [scripts/generate-icons.js](scripts/generate-icons.js)
   - Add entries to the `fileExtensions` or `fileNames` objects
   - Run `npm run generate-icons` to regenerate icon files

3. **Testing Your Changes**: See [Testing Your Changes](#testing-your-changes) section below

4. **Documentation**: Update [README.md](README.md) if your changes affect usage or features

## Commit Message Guidelines

This project uses [Conventional Commits](https://www.conventionalcommits.org/) enforced by Commitlint. All commit messages must follow this format:

```
<type>: <description>

[optional body]

[optional footer]
```

### Commit Types

- **feat**: A new feature
- **fix**: A bug fix
- **docs**: Documentation only changes
- **style**: Changes that do not affect the meaning of the code (white-space, formatting, etc)
- **refactor**: A code change that neither fixes a bug nor adds a feature
- **perf**: A code change that improves performance
- **test**: Adding missing tests or correcting existing tests
- **build**: Changes that affect the build system or external dependencies
- **ci**: Changes to CI configuration files and scripts
- **chore**: Other changes that don't modify src or test files
- **revert**: Reverts a previous commit

### Commit Message Rules

- Subject line must not start with uppercase (enforced by commitlint)
- Subject line must not be empty
- Type must not be empty
- Keep the subject line under 72 characters
- Use the imperative mood ("add feature" not "added feature")

### Examples

Good commit messages:
```
feat: add icon support for .astro files
fix: correct folder icon color for yellow theme
docs: update installation instructions
style: adjust icon spacing for better alignment
```

Bad commit messages:
```
Added new icons          # Missing type
fix: Fixed the bug       # Subject starts with uppercase
feat:                    # Empty subject
Updated stuff            # Missing type, vague description
```

### Automatic Validation

When you commit, Husky will automatically run Commitlint to validate your commit message. If your message doesn't meet the requirements, the commit will be rejected with an error message explaining what needs to be fixed.

## Testing Your Changes

### Manual Testing

1. Open VS Code
2. Press `F5` or go to `Run > Start Debugging`
3. This will open a new VS Code window with your icon theme loaded
4. In the Extension Development Host window:
   - Press `Ctrl+Shift+P` (or `Cmd+Shift+P` on macOS)
   - Type "File Icon Theme"
   - Select one of the No Pixie icon themes
5. Test with different file types to ensure icons display correctly:
   - Create test files with various extensions
   - Check folder icons for common directories
   - Verify special file icons (package.json, Dockerfile, etc.)

### What to Check

**Icon Themes:**
- Icons are clearly visible and recognizable
- Colors are consistent within each theme variant
- File type icons display correctly for various file extensions
- Folder icons change appropriately when expanded/collapsed
- Special folder icons (src, node_modules, .git, etc.) use distinct colors
- Icons work well with both light and dark VS Code themes

## Publishing

Publishing is handled via npm scripts and should only be done by maintainers:

```bash
# Package the extension
npm run package

# Publish to VS Code Marketplace
npm run publish:vsce

# Publish to Open VSX Registry (for Cursor compatibility)
npm run publish:ovsx

# Generate changelog
npm run changelog
```

## Pull Request Process

1. **Ensure your code follows the guidelines** in this document

2. **Update documentation** if needed:
   - Update [README.md](README.md) for user-facing changes
   - Update this file for contribution process changes

3. **Create a pull request**:
   - Use a clear, descriptive title following the conventional commit format
   - Describe what changes you made and why
   - Include screenshots for visual changes (before/after comparisons)
   - Reference any related issues

4. **Pull request requirements**:
   - All commits must pass Commitlint validation
   - Changes should be focused and atomic
   - Include screenshots demonstrating icon changes
   - Base your PR against the `main` branch
   - If AI tools were used to assist with the contribution, please disclose this in your PR description

5. **Review process**:
   - A maintainer will review your PR
   - Address any requested changes
   - Once approved, a maintainer will merge your PR

### Pull Request Template

When creating a PR, consider including:

```markdown
## Description
Brief description of changes

## Type of Change
- [ ] Bug fix (non-breaking change that fixes an issue)
- [ ] New feature (non-breaking change that adds functionality)
- [ ] Breaking change (fix or feature that would cause existing functionality to not work as expected)
- [ ] Documentation update

## Screenshots
Before/After screenshots if applicable

## Testing
Describe how you tested your changes

## Checklist
- [ ] My commits follow the conventional commit format
- [ ] I have updated documentation as needed
- [ ] I have tested my changes in VS Code
- [ ] I have tested all three icon theme variants (if applicable)
- [ ] I have disclosed any AI tools used in this contribution
```

## Questions or Problems?

- Check existing [issues](https://github.com/nopixie/nopixie-icon-theme/issues) to see if your question has been answered
- Open a new issue if you encounter bugs or have feature requests
- Be specific and include relevant details (VS Code version, OS, icon theme variant, etc.)

## Thank You!

Your contributions help make No Pixie Icon Theme better for everyone. We appreciate your time and effort!
