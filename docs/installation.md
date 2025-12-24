# Installation & Usage

## Prerequisites

- Visual Studio Code 1.106+ (for custom agents)
- GitHub Copilot extension
- **GitHub Copilot Pro, Pro+, Business, or Enterprise** (required for Claude Sonnet 4.5 and advanced models)
  - Free tier does NOT include Claude Sonnet 4.5
  - See [GitHub Copilot Plans](https://docs.github.com/en/copilot/about-github-copilot/plans-for-github-copilot) for model availability

---

## Setup

### 1. Coding Standards

Copy coding standards to your project's `.github/` directory:

```bash
# Clone this repository
git clone https://github.com/jlacube/gh-copilot-tools.git

# Copy to your project
cp gh-copilot-tools/.github/copilot-instructions.md your-project/.github/
```

GitHub Copilot automatically reads `.github/copilot-instructions.md` as context.

---

### 2. Agent Configurations

Agent files are VS Code custom agent configurations (`.agent.md` format). To use:

1. Copy desired agent file(s) to your project's `.github/agents/` directory:
   ```bash
   # Copy specific agent
   cp gh-copilot-tools/.github/agents/coding-buddy-1.3.agent.md your-project/.github/agents/
   
   # Or copy all agents
   cp gh-copilot-tools/.github/agents/*.agent.md your-project/.github/agents/
   
   # Optionally create buddy directory for agent logs
   mkdir -p your-project/.github/buddy
   ```

2. VS Code automatically detects `.agent.md` files in `.github/agents/`

3. **Switch to agent via agent picker dropdown**:
   - Open Chat view (Ctrl+Alt+I / Cmd+Option+I)
   - Click the agent picker dropdown (shows current agent name)
   - Select your custom agent from the list

4. Submit prompts as normal - the selected agent's instructions and tools apply automatically

**Note:** Custom agents require VS Code 1.106+ and GitHub Copilot extension.

---

## Configuration

### Coding Standards Customization

Edit `.github/copilot-instructions.md` to add:
- Language-specific guidelines for your tech stack
- Project-specific conventions and patterns
- Team coding standards and preferences

### Agent Customization

Modify agent `.md` files to adjust:
- Communication style (if you prefer less blunt feedback)
- Required fetch count (default: 5+)
- TODO tracking requirements
- Logging verbosity

---

## Features & Benefits

### For Individual Developers
- **Consistent Code Quality**: Copilot generates code following established patterns
- **Deep Reasoning**: Extended thinking for complex problem-solving
- **Research Integration**: Automatic fetching of current best practices
- **Execution Validation**: Confidence that generated code actually works

### For Teams
- **Standardized Output**: All team members using Copilot get consistent style
- **Specification-Driven**: Clear requirements before implementation (Spec agents)
- **Quality Gates**: Enforced review and validation processes (Spec-Kitty)
- **Documentation**: Automatic logging of decisions and research

### For Legacy Projects
- **Reverse Engineering**: Extract specs from undocumented codebases
- **Modernization Planning**: Understand existing systems before refactoring
- **Knowledge Transfer**: Document tribal knowledge in specifications

---

## Technical Details

### Supported Languages (Coding Standards)
- Python 3.x (PEP 8, type hints, modern idioms)
- JavaScript ES6+ (Airbnb style, modern patterns)
- TypeScript 4.x+ (strict mode, advanced types)

### Agent Requirements
- **Tools**: vscode, execute, read, edit, search, web, sequentialthinking, agent, todo
- **Python Integration**: Python environment management for coding agents
- **MCP Support**: Model Context Protocol for advanced tool usage

### Timestamp Format
All agents use ISO 8601 UTC format: `YYYY-MM-DDTHH:MM:SSZ`

Generated via:
- **PowerShell**: `[System.DateTime]::UtcNow.ToString("yyyy-MM-ddTHH:mm:ssZ")`
- **Bash/sh**: `date -u "+%Y-%m-%dT%H:%M:%SZ"`

---

## Limitations

- **Agent Access**: Requires Claude 4.5/Sonnet model access through GitHub Copilot (Pro, Pro+, Business, or Enterprise plans)
- **Extended Thinking**: Thinking token budgets depend on model configuration
- **Web Tool**: Web search capabilities depend on environment setup
- **Coding Standards**: Currently covers Python and JavaScript/TypeScript (extensible)
- **Agent Count**: Repository includes 9 agents; choose relevant ones for your workflow
