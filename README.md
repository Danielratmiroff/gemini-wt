# 🔷 Gemini-Worktree

Run multiple Gemini Code instances in parallel without stepping on each other. This CLI creates isolated git worktrees for each Gemini session, so you can work on different features simultaneously while keeping your main branch clean.

_This is a fork of [claude-wt](https://github.com/jlowin/claude-wt) that works with Gemini instead of Claude. Inspired by [Jeremiah Lowin](https://github.com/jlowin/claude-wt)._

## 🚀 Quick Start

Jump right in without installing anything:

```bash
uvx gemini-wt new "implement user authentication"
```

**That's it.** You're now working in a clean branch where Gemini can't mess up your pristine codebase.

### Installation Options

If you prefer global installation:

```bash
uv tool install gemini-wt
```

## 🎯 Commands

### ✨ Start Fresh: `new`

Spin up a new isolated Gemini session:

```bash
uvx gemini-wt new "implement user authentication"
```

Behind the scenes: creates a timestamp branch, sets up a worktree in `.gemini/worktrees/`, and launches Gemini with your query.

Want a memorable branch name? Use `--name`:

```bash
uvx gemini-wt new "fix the parser" --name parser-fix
```

Need to branch from a specific source? Use `--branch`:

```bash
uvx gemini-wt new "hotfix for prod" --branch main --name hotfix-123
```

### 🔄 Pick Up Where You Left Off: `resume`

Gemini sessions are like good TV shows—you want to continue watching:

```bash
uvx gemini-wt resume 20241201-143022
```

The session ID is shown when you create it.

### 📋 See What's Running: `list`

See all your active worktrees:

```bash
uvx gemini-wt list
```

Shows each session with its health status.

### 🧹 Clean Up: `clean`

Remove a specific session when you're done:

```bash
uvx gemini-wt clean 20241201-143022
```

Or clean everything:

```bash
uvx gemini-wt clean --all  # The Marie Kondo approach
```

## 🔧 How It Works

Think of it like having multiple parallel universes for your code:

1. **Branch Creation** → Each session gets its own branch (`gemini-{timestamp}` or your custom name)
2. **Worktree Setup** → Creates a separate directory in `.gemini/worktrees/` so files don't conflict
3. **Gemini Launch** → Starts Gemini in the isolated environment with full repo access
4. **Session Management** → Resume, list, and clean up sessions effortlessly

## 🎁 Why You'll Love This

- **Fear-Free Experimentation** → Gemini can't break your main branch even if it tries
- **Mental Clarity** → No more "did I commit that test code?" anxiety
- **Context Switching** → Jump between different Gemini conversations effortlessly
- **Easy Cleanup** → One command to remove all experimental branches
- **Clean History** → Your main branch stays pristine for serious work

## 📋 What You Need

- **Python 3.12+**
- **Git with worktree support** (any recent version)
- **Gemini CLI** (installed and authenticated)

## 🛠️ Development

Uses uv for dependency management:

```bash
uv sync
uv run gemini-wt --help
```

Or test changes without installing:

```bash
uvx --from . gemini-wt --help
```
