# Qwen Code Development Context

## Project Overview

Qwen Code is an AI-powered command-line workflow tool for developers, adapted from Google's Gemini CLI and specifically optimized for Qwen3-Coder models. It provides advanced code understanding, automated task execution, and intelligent assistance directly from the terminal.

### Key Features
- **Code Understanding & Editing**: Query and edit large codebases beyond traditional context window limits
- **Workflow Automation**: Automate operational tasks like handling pull requests and complex rebases  
- **Enhanced Parser**: Adapted parser specifically optimized for Qwen-Coder models
- **Vision Model Support**: Automatically detect images in input and seamlessly switch to vision-capable models for multimodal analysis
- **Multi-Provider Support**: Works with Qwen OAuth, OpenAI-compatible APIs, ModelScope, and OpenRouter

### Architecture
- **Monorepo Structure**: Uses npm workspaces with multiple packages
- **Core Packages**:
  - `@qwen-code/qwen-code-core`: Core backend logic and AI integration
  - `@qwen-code/qwen-code`: CLI interface with React/Ink UI
  - `@qwen-code/qwen-code-test-utils`: Shared testing utilities
  - `@qwen-code/qwen-code-vscode-ide-companion`: VS Code integration companion
- **Technology Stack**: TypeScript, React (for CLI UI via Ink), Node.js >=20

## Building and Running

### Prerequisites
- Node.js version ~20.19.0 (for development) or >=20.0.0 (for production)
- Git

### Development Setup
```bash
# Clone and install
git clone https://github.com/QwenLM/qwen-code.git
cd qwen-code
npm install

# Build the project
npm run build          # Build main project
npm run build:all      # Build main project + sandbox container
npm run bundle         # Generate final bundle for distribution

# Run the CLI
npm start              # Start Qwen Code from source
npm run debug          # Start in debug mode with inspector
```

### Testing
```bash
# Run all checks (formatting, linting, tests)
npm run preflight

# Individual commands
npm run test           # Unit tests
npm run test:ci        # CI tests with coverage
npm run test:e2e       # End-to-end integration tests
npm run lint           # ESLint checks
npm run format         # Prettier formatting
npm run typecheck      # TypeScript type checking
```

### Makefile Shortcuts
```bash
make install           # npm install
make build             # npm run build
make build-all         # npm run build:all
make test              # npm run test
make lint              # npm run lint
make format            # npm run format
make preflight         # npm run preflight
make clean             # npm run clean
make start             # npm run start
make debug             # npm run debug
```

### Sandboxing
Sandboxing is highly recommended for security:

**macOS Seatbelt** (default):
- Uses permissive-open profile by default
- Can switch to restrictive profiles via `SEATBELT_PROFILE` environment variable

**Container-based** (all platforms):
```bash
# Enable container sandboxing
export GEMINI_SANDBOX=true  # or docker/podman

# Build with sandbox support
npm run build:all

# Run (automatically uses sandbox if enabled)
npm start
```

## Development Conventions

### Coding Standards
- **Strict TypeScript**: Full strict mode with comprehensive type safety
- **ESLint Rules**: Enforced via comprehensive ESLint configuration
  - No `any` types allowed
  - Prefer `const` over `let`/`var`
  - ES6 imports only (no `require()`)
  - No relative imports between packages (`import/no-relative-packages`)
  - Prefer arrow functions and object shorthand
- **Prettier**: Automatic code formatting with consistent style
- **React Conventions**: Using React 19 with JSX runtime, functional components

### Project Structure
```
qwen-code/
├── packages/
│   ├── cli/              # Command-line interface (React/Ink UI)
│   ├── core/             # Core AI logic and utilities
│   ├── test-utils/       # Shared testing utilities
│   └── vscode-ide-companion/ # VS Code integration
├── scripts/              # Build and utility scripts
├── integration-tests/    # End-to-end integration tests
├── docs/                 # Documentation
└── eslint-rules/         # Custom ESLint rules
```

### Git and Commit Guidelines
- **Conventional Commits**: Follow conventional commit message format
  - `feat(cli): Add --json flag to config command`
  - `fix(core): Handle null responses from API`
- **Small, Focused PRs**: Address single issues/features per PR
- **Link to Issues**: All PRs must reference existing GitHub issues
- **Preflight Checks**: Run `npm run preflight` before committing
- **Draft PRs**: Use for work-in-progress feedback

### Testing Practices
- **Unit Tests**: Located alongside source files with `.test.ts`/`.test.tsx` extensions
- **Integration Tests**: Comprehensive end-to-end tests in `integration-tests/` directory
- **Vitest**: Primary test runner with coverage support
- **Test Utilities**: Shared utilities in `test-utils` package

### Debugging
**VS Code Debugging**:
```bash
# Start in debug mode
npm run debug

# Attach VS Code debugger using .vscode/launch.json
```

**React DevTools**:
```bash
# Start CLI with React DevTools support
DEV=true npm start

# In separate terminal
npx react-devtools@4.28.5
```

### Documentation
- **Inline Documentation**: JSDoc comments for public APIs
- **External Docs**: Comprehensive documentation in `/docs` directory
- **README Updates**: Update README.md for user-facing changes
- **API Documentation**: Generated documentation for public interfaces

## Contribution Guidelines

### Before Contributing
1. **Sign CLA**: [Google Contributor License Agreement](https://cla.developers.google.com/)
2. **Review Guidelines**: Follow [Google's Open Source Community Guidelines](https://opensource.google/conduct/)
3. **Create Issue**: Open GitHub issue before coding for discussion/approval

### PR Requirements
- Link to existing issue
- Pass all preflight checks (`npm run preflight`)
- Include documentation updates for user-facing changes
- Small, atomic changes focused on single purpose
- Clear commit messages following conventional commits

### Code Quality
- Adhere to existing coding patterns and conventions
- Pay special attention to import paths and package boundaries
- Ensure proper error handling and type safety
- Write comprehensive tests for new functionality

## Environment Configuration

### Authentication
Configure via environment variables, `.env` files, or Qwen OAuth:

**Qwen OAuth** (recommended):
```bash
qwen  # Automatic browser authentication
```

**OpenAI-Compatible API**:
```bash
export OPENAI_API_KEY="your_key"
export OPENAI_BASE_URL="your_endpoint"  
export OPENAI_MODEL="your_model"
```

### Session Management
Create `~/.qwen/settings.json` for persistent configuration:
```json
{
  "sessionTokenLimit": 32000,
  "experimental": {
    "vlmSwitchMode": "once",
    "visionModelPreview": true
  }
}
```

### Development Environment
- Use Node.js ~20.19.0 for development (nvm recommended)
- Enable pre-commit hooks for automatic preflight checks
- Use sandboxing for secure development and testing