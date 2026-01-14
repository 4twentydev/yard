# CLAUDE.md - AI Assistant Guide for Yard

This document provides comprehensive guidance for AI assistants working on the Yard codebase.

## Project Overview

**Yard** is a new software project in its initial development phase. This repository is currently minimal, containing foundational files and awaiting its core implementation.

- **Repository**: 4twentydev/Yard
- **Current State**: Initial development phase
- **Primary Branch**: Main/master branch for stable releases

## Repository Structure

### Current Structure

```
Yard/
├── README.md           # Project overview and documentation
├── CLAUDE.md          # This file - AI assistant guidelines
└── .git/              # Git repository metadata
```

### Expected Structure (as project grows)

```
Yard/
├── src/               # Source code
├── tests/             # Test files
├── docs/              # Additional documentation
├── scripts/           # Build and utility scripts
├── config/            # Configuration files
├── .github/           # GitHub workflows and templates
├── README.md          # Project overview
├── CLAUDE.md          # AI assistant guidelines
├── LICENSE            # Project license
└── .gitignore         # Git ignore rules
```

## Development Workflow

### Git Practices

#### Branch Naming Convention

- **Feature branches**: `claude/feature-name-{session-id}`
- **Bug fixes**: `claude/fix-issue-description-{session-id}`
- **Documentation**: `claude/docs-description-{session-id}`

**CRITICAL**: All branch names MUST start with `claude/` and end with a matching session ID when working with Claude AI. Failure to follow this convention will result in 403 errors on push.

#### Commit Guidelines

1. **Commit Message Format**:
   ```
   <type>: <short summary>

   <detailed description if needed>
   ```

2. **Types**:
   - `feat`: New feature
   - `fix`: Bug fix
   - `docs`: Documentation changes
   - `refactor`: Code refactoring
   - `test`: Adding or updating tests
   - `chore`: Maintenance tasks
   - `style`: Code style/formatting changes

3. **Best Practices**:
   - Write clear, concise commit messages
   - Focus on "why" rather than "what"
   - Use present tense ("add feature" not "added feature")
   - Keep subject line under 50 characters
   - Use body for detailed explanations (if needed)

#### Push Protocol

- Always use: `git push -u origin <branch-name>`
- Retry on network errors (up to 4 times with exponential backoff: 2s, 4s, 8s, 16s)
- Never force push to main/master branches
- Only force push to feature branches with explicit approval

#### Pull Request Process

1. **Before Creating PR**:
   - Ensure all tests pass
   - Review your own changes
   - Update documentation if needed
   - Check for merge conflicts

2. **PR Description Format**:
   ```markdown
   ## Summary
   - Bullet point 1
   - Bullet point 2

   ## Changes Made
   - List of specific changes

   ## Test Plan
   - [ ] Testing step 1
   - [ ] Testing step 2

   ## Related Issues
   Fixes #<issue-number>
   ```

3. **PR Best Practices**:
   - Keep PRs focused and reasonably sized
   - Link related issues
   - Request reviews from appropriate team members
   - Address review comments promptly

### Code Review Guidelines

- Review for logic, security, performance, and maintainability
- Check for proper error handling
- Ensure code follows project conventions
- Verify tests cover new functionality
- Look for potential edge cases

## Code Conventions

### General Principles

1. **Simplicity First**:
   - Write clear, straightforward code
   - Avoid over-engineering
   - Don't add features beyond requirements
   - Keep solutions focused on the task at hand

2. **Code Quality**:
   - Write self-documenting code
   - Use meaningful variable and function names
   - Keep functions small and focused
   - Follow DRY (Don't Repeat Yourself) when appropriate
   - Avoid premature optimization

3. **Security**:
   - Never commit secrets, API keys, or credentials
   - Validate all external input
   - Be aware of common vulnerabilities (OWASP Top 10)
   - Use parameterized queries for database operations
   - Implement proper authentication and authorization

4. **Error Handling**:
   - Handle errors gracefully
   - Provide meaningful error messages
   - Log errors appropriately
   - Only catch exceptions you can handle
   - Validate at system boundaries

### Coding Style

*Note: Specific style guides will be added as the project language/framework is established*

- Follow language-specific best practices
- Use consistent indentation (tabs vs spaces will be standardized)
- Keep line length reasonable (typically 80-120 characters)
- Use whitespace for readability
- Group related code together

### Documentation

1. **Code Comments**:
   - Only add comments where logic isn't self-evident
   - Explain "why", not "what"
   - Keep comments up-to-date with code changes
   - Remove commented-out code (use git history instead)

2. **Documentation Files**:
   - Update README.md for user-facing changes
   - Update CLAUDE.md for process changes
   - Create additional docs as needed in `/docs`
   - Keep documentation current with implementation

## AI Assistant Guidelines

### Before Making Changes

1. **Always Read First**:
   - Never propose changes to code you haven't read
   - Read entire files before suggesting modifications
   - Understand existing patterns and conventions
   - Check for related code elsewhere in the codebase

2. **Use Task Planning**:
   - Use TodoWrite tool for complex tasks (3+ steps)
   - Break down large tasks into manageable steps
   - Mark tasks as in_progress before starting
   - Complete tasks immediately after finishing
   - Keep only one task in_progress at a time

3. **Research Before Acting**:
   - Search for existing implementations
   - Check for similar patterns in the codebase
   - Look for configuration files and settings
   - Understand the project's architecture

### During Development

1. **Make Focused Changes**:
   - Only change what's necessary for the task
   - Don't refactor unrelated code
   - Don't add "nice to have" features
   - Keep changes minimal and focused

2. **Avoid Over-Engineering**:
   - Don't add error handling for impossible scenarios
   - Don't create abstractions for one-time operations
   - Don't add features for hypothetical future requirements
   - Three similar lines > premature abstraction

3. **Security Awareness**:
   - Watch for injection vulnerabilities
   - Validate external input
   - Don't expose sensitive information
   - Use secure defaults

4. **Tool Usage**:
   - Use specialized tools (Read, Edit, Write) over bash
   - Run independent operations in parallel
   - Use Task tool for complex exploratory work
   - Never use bash echo for user communication

### Testing

1. **Write Tests For**:
   - New features
   - Bug fixes
   - Critical business logic
   - Edge cases and error conditions

2. **Test Coverage**:
   - Aim for comprehensive coverage
   - Test both success and failure paths
   - Include integration tests for workflows
   - Test edge cases and boundaries

3. **Running Tests**:
   - Run tests before committing
   - Ensure all tests pass before PR
   - Fix broken tests immediately
   - Don't skip or disable tests without good reason

### Code Review Checklist

Before submitting code for review, verify:

- [ ] All tests pass
- [ ] Code follows project conventions
- [ ] Documentation is updated
- [ ] No security vulnerabilities introduced
- [ ] Error handling is appropriate
- [ ] Code is readable and maintainable
- [ ] No debugging code or console.logs left behind
- [ ] Git history is clean and logical
- [ ] Commit messages are clear and descriptive

## Common Workflows

### Adding a New Feature

1. Create feature branch: `claude/feature-name-{session-id}`
2. Plan the work using TodoWrite (for complex features)
3. Read relevant existing code
4. Implement the feature
5. Write/update tests
6. Update documentation
7. Run tests and verify
8. Commit with clear message
9. Push to remote
10. Create pull request

### Fixing a Bug

1. Create fix branch: `claude/fix-description-{session-id}`
2. Reproduce the bug
3. Identify root cause
4. Implement fix
5. Add test to prevent regression
6. Verify fix works
7. Commit with clear message
8. Push to remote
9. Create pull request

### Updating Documentation

1. Create docs branch: `claude/docs-description-{session-id}`
2. Make documentation changes
3. Review for accuracy and clarity
4. Commit with clear message
5. Push to remote
6. Create pull request

## Project-Specific Notes

### Current Development Phase

The Yard project is in its **initial development phase**. As development progresses:

- Core architecture will be established
- Technology stack will be defined
- Coding standards will be formalized
- Build/test processes will be implemented
- CI/CD pipelines will be configured

This document should be updated as these decisions are made.

### Future Sections to Add

As the project grows, consider adding:

- **Architecture Overview**: System design and component interactions
- **API Documentation**: Endpoint specifications and contracts
- **Database Schema**: Data models and relationships
- **Deployment Guide**: How to deploy and configure
- **Troubleshooting**: Common issues and solutions
- **Performance Guidelines**: Optimization strategies
- **Dependency Management**: How to add/update dependencies

## Maintenance

### Keeping This Document Updated

This CLAUDE.md file should be updated when:

- Project structure changes significantly
- New conventions or patterns are established
- Development workflow changes
- New tools or processes are adopted
- Common issues or patterns emerge

AI assistants should proactively suggest updates to this document when they notice:
- Information that's out of date
- New patterns that should be documented
- Missing important guidelines
- Unclear or ambiguous instructions

## Questions and Support

When uncertain about:
- **Code patterns**: Search the codebase for similar examples
- **Project decisions**: Check git history and PR discussions
- **Best practices**: Refer to this document and language-specific guides
- **Unclear requirements**: Ask the user for clarification

## Version History

- **2026-01-14**: Initial version created for new repository

---

**Note**: This document is a living guide that should evolve with the project. Keep it updated and comprehensive to ensure all contributors (human and AI) have clear guidance.
