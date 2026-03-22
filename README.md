# OpenCode Configuration

My personal OpenCode global configuration with custom agents and commands for enhanced development workflow.

## Features

- **Review Agent**: Senior-level code review focusing on correctness, security, and maintainability
- **Custom Commands**: 
  - `/check-file` - Review specific files for issues
  - `/pr-summary` - Generate PR descriptions from branch diff
  - `/review-changes` - Analyze recent git changes

## Setup

1. Clone this repository to your OpenCode config directory:
   ```bash
   git clone https://github.com/ridakaddir/opencode.config.git ~/.config/opencode
   ```

2. Copy the example configuration:
   ```bash
   cp opencode.example.json opencode.json
   ```

3. Set your Context7 API key:
   ```bash
   export CONTEXT7_API_KEY="your-api-key-here"
   ```
   
   Or add it to your shell profile for persistence:
   ```bash
   echo 'export CONTEXT7_API_KEY="your-api-key-here"' >> ~/.zshrc
   ```

4. Install dependencies:
   ```bash
   npm install
   ```

## Configuration

### Environment Variables

- `CONTEXT7_API_KEY`: Your Context7 API key for enhanced documentation access

### Agents

#### Review Agent (`agents/review.md`)
- Read-only code review agent
- Focuses on logic errors, security issues, and architectural violations
- Temperature: 0.1 for consistency
- Permissions: Read-only with limited git commands allowed

### Commands

#### `/check-file <file-path>`
Review a specific file for issues and improvements.

**Example:**
```bash
/check-file src/components/UserAuth.tsx
```

#### `/pr-summary` 
Generate a comprehensive PR description from the current branch diff.

**Features:**
- Analyzes commits from main branch
- Creates structured PR description
- Includes testing notes and breaking changes

#### `/review-changes`
Analyze recent commits and flag potential issues before opening a PR.

**Features:**
- Reviews last 15 commits
- Provides diff summary
- Suggests verification steps

## Usage

Once configured, these agents and commands are available globally in OpenCode:

```bash
# Review a specific file
/check-file src/components/UserAuth.tsx

# Generate PR description
/pr-summary

# Review recent changes
/review-changes
```

## Project Structure

```
├── agents/
│   └── review.md           # Code review agent configuration
├── commands/
│   ├── check-file.md       # File review command
│   ├── pr-summary.md       # PR description generator
│   └── review-changes.md   # Change analysis command
├── opencode.example.json   # Configuration template
├── package.json           # Dependencies
└── README.md              # This file
```

## Requirements

- Node.js >= 16.0.0
- OpenCode AI
- Context7 API key (optional, for enhanced documentation)

## License

MIT