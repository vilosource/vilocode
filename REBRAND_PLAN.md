# ViloCode Rebranding Plan

## Overview
This document outlines the comprehensive plan to rebrand the Qwen Code project from "Qwen" to "ViloCode". This is a major undertaking that requires careful handling of both branding and functionality aspects to ensure no functionality is broken.

## Files to Update for Branding Changes

### 1. File Names and Paths
- `SPEC.md` - Main specification document
- `README.md` - Main documentation
- `QWEN.md` - Development context document
- `CONTRIBUTING.md` - Contribution guidelines
- `CHANGELOG.md` - Release history
- `LICENSE` - License file

### 2. Package Configuration Files
- `package.json` - Root package info
- `packages/cli/package.json` - CLI package
- `packages/core/package.json` - Core package
- `packages/test-utils/package.json` - Test utils package
- `packages/vscode-ide-companion/package.json` - VS Code extension

### 3. VS Code Extension Files
- `packages/vscode-ide-companion/README.md` - Extension README
- `packages/vscode-ide-companion/package.json` - Extension manifest

### 4. Code Implementation Files
- `packages/cli/src/gemini.tsx` - Main CLI entry point
- `packages/core/src/config/config.ts` - Core configuration
- `packages/core/src/telemetry/loggers.ts` - Telemetry logging

### 5. Documentation and Examples
- `docs/` - Documentation directory
- Various example files and markdown docs

### 6. Script Files
- `scripts/` - Build and utility scripts
- `Makefile` - Build commands

## Phase 1: Preparation (1-2 hours)
1. Create backup copies of all modified files
2. Identify all hardcoded references to "Qwen" in code
3. Document current branding elements
4. Create a mapping of old brand names to new brand names

## Phase 2: Core Branding Changes (3-4 hours)
### Package Names and Binaries
Update all package.json files to change:
- `name` field from `@qwen-code/qwen-code` to `@vilocode/vilocode`
- `displayName` fields in VS Code extension
- `description` fields
- Binary names (`qwen` to `vilocode`)
- Repository URLs from QwenLM to Vilocode organization

### Documentation Updates
Update all text references from:
- "Qwen Code" → "ViloCode"
- "Qwen3-Coder" → "ViloCode-Coder"
- "Qwen OAuth" → "ViloCode OAuth"
- "Qwen CLI" → "ViloCode CLI"
- "Qwen Code Companion" → "ViloCode Companion"

### Code Implementation Updates
- Update window titles to show "ViloCode" instead of "Qwen"
- Update default git co-author in `config.ts` from "Qwen-Coder" to "ViloCode-Coder"
- Update repository URLs from QwenLM to Vilocode organization
- Update error messages and logs where Qwen is mentioned

## Phase 3: VS Code Extension Updates (1-2 hours)
1. Update VS Code extension manifest
2. Update readme and documentation
3. Update command names and titles

## Phase 4: Testing and Validation (2-3 hours)
1. Run `npm run preflight` to check formatting, linting, and tests
2. Run `npm test` to verify all tests still pass
3. Build the project to ensure compilation works
4. Test CLI functionality manually with `npm start`
5. Verify VS Code extension builds properly

## Phase 5: Final Review (1 hour)
1. Comprehensive review of all changed files
2. Verify all branding references are updated correctly
3. Ensure no functionality is impacted by changes

## Specific Branding Changes Required

### Package Names and Binaries
Replace all instances of:
- `@qwen-code/qwen-code` with `@vilocode/vilocode`
- `qwen` with `vilocode` 
- `gemini` with `vilocode` in file names and references

### Documentation Updates
Update all text references from:
- "Qwen Code" → "ViloCode"
- "Qwen3-Coder" → "ViloCode-Coder"
- "Qwen OAuth" → "ViloCode OAuth"
- "Qwen CLI" → "ViloCode CLI"
- "Qwen Code Companion" → "ViloCode Companion"

### Code Implementation Updates
- Change window titles to show "ViloCode" instead of "Qwen"
- Update default git co-author from "Qwen-Coder" to "ViloCode-Coder"
- Update repository URLs from QwenLM to Vilocode organization
- Update error messages and logs where Qwen is mentioned

## Potential Issues and Solutions

1. **Dependency References**: Some dependencies might hardcode Qwen references. Need to verify all external dependencies.
2. **URLs and API Endpoints**: Check for hard-coded URLs that may reference Qwen services
3. **Git Commit Authors**: Ensure the git co-author name is updated properly
4. **Binary Names**: Change all references to the executable name from `qwen` to `vilocode`
5. **VS Code Extension**: Update extension ID and display name
6. **Copyright Headers**: Update copyright notices to reflect new brand

## Testing Strategy

1. Run `npm run preflight` to check formatting, linting, and tests
2. Run `npm test` to verify all tests still pass
3. Test the CLI functionality manually with `npm start`
4. Verify VS Code extension builds properly
5. Check that all branding elements appear correctly

## Timeline Estimate
- Preparation: 1-2 hours
- Core Branding Changes: 3-4 hours
- VS Code Extension Updates: 1-2 hours
- Testing and Validation: 2-3 hours
- Final Review: 1 hour
- **Total: 8-12 hours**

This rebranding requires careful attention to detail to avoid breaking functionality while maintaining all features and capabilities of the original Qwen Code product.