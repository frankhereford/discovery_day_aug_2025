# UV Python Tooling Discovery Day 🚀

A day-long exploration of `uv`, the blazing-fast Python package manager and virtual environment tool that's revolutionizing Python development in 2025.

## 🎯 Exploration Goals

- [ ] Understand what `uv` is and why it's gaining popularity
- [ ] Install and configure `uv` on the system
- [ ] Compare `uv` performance vs traditional tools (pip, poetry, etc.)
- [ ] Learn core `uv` workflows for project management
- [ ] Explore Python version management with `uv`
- [ ] Test dependency management and lockfiles
- [ ] Create sample projects using `uv`
- [ ] Document best practices and gotchas

## 📚 Background

`uv` is a high-performance Python package manager and virtual environment tool created by Astral (makers of Ruff). Written in Rust, it aims to replace multiple Python tools with a single, unified solution that's 10-100x faster than traditional alternatives.

### What `uv` Replaces

- `pip` - Package installation
- `virtualenv` / `venv` - Virtual environments
- `pyenv` - Python version management
- `poetry` - Dependency management and packaging
- `pip-tools` - Dependency pinning and compilation

## 🔧 Installation Methods

### Option 1: Using the official installer (Recommended)

```bash
# macOS/Linux
curl -LsSf https://astral.sh/uv/install.sh | sh

# Windows
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

### Option 2: Using Homebrew (macOS)

```bash
brew install uv
```

### Option 3: Using pip (if you must)

```bash
pip install uv
```

### Verify Installation

```bash
uv --version
```

## 🏃 Quick Start Exploration

### 1. Python Installation Management

```bash
# List available Python versions
uv python list

# Install a specific Python version
uv python install 3.12

# Install the latest Python
uv python install 3.13

# List installed Python versions
uv python list --only-installed
```

### 2. Project Creation and Management

```bash
# Create a new project
uv init my-project
cd my-project

# Create project with specific Python version
uv init --python 3.12 my-project-312

# Initialize in existing directory
uv init .
```

### 3. Virtual Environment Management

```bash
# Create and activate virtual environment
uv venv

# Create with specific Python version
uv venv --python 3.12

# Activate environment (traditional way)
source .venv/bin/activate  # macOS/Linux
.venv\Scripts\activate     # Windows

# Or use uv run (no activation needed)
uv run python --version
```

### 4. Package Management

```bash
# Add dependencies
uv add requests
uv add pandas numpy
uv add pytest --dev  # Development dependency

# Install from requirements
uv add -r requirements.txt

# Remove packages
uv remove requests

# Update packages
uv sync --upgrade

# Install all project dependencies
uv sync
```

## 🧪 Experiments and Benchmarks

### Performance Comparison

Create a simple benchmark to compare `uv` vs `pip`:

```bash
# Benchmark: Installing popular packages
time pip install requests pandas numpy matplotlib
# vs
time uv add requests pandas numpy matplotlib
```

### Project Structure Exploration

Document the project structure `uv` creates:

```
my-project/
├── .python-version      # Python version specification
├── .venv/              # Virtual environment (if created)
├── pyproject.toml      # Project configuration and dependencies
├── uv.lock            # Dependency lockfile
└── README.md
```

## 📝 Learning Experiments

### Experiment 1: Migration from pip/poetry

- [ ] Take an existing pip-based project
- [ ] Convert to use `uv`
- [ ] Document the process and benefits

### Experiment 2: Dependency Resolution

- [ ] Create conflicting dependencies
- [ ] See how `uv` handles resolution
- [ ] Compare with pip's behavior

### Experiment 3: Cross-platform Testing

- [ ] Test the same project on different OS
- [ ] Verify lockfile reproducibility

### Experiment 4: Script Running

```bash
# Run scripts without activating environment
uv run python script.py

# Run with specific dependencies
uv run --with requests python -c "import requests; print(requests.get('https://httpbin.org/json').json())"

# One-off tool execution
uv tool run black .
uv tool run pytest
```

## 🔍 Advanced Features to Explore

### Python Version Management

```bash
# Pin Python version for project
echo "3.12" > .python-version

# Use specific Python for command
uv run --python 3.11 python script.py
```

### Dependency Groups

```bash
# Add to specific dependency groups
uv add --group dev pytest black ruff
uv add --group docs sphinx

# Install specific groups
uv sync --group dev
uv sync --all-groups
```

### Lock Files and Reproducibility

```bash
# Generate lockfile
uv lock

# Install from lockfile
uv sync --frozen

# Update specific package
uv lock --update requests
```

## 📊 Findings and Observations

### Performance Results

| Operation              | pip  | uv   | Speedup |
| ---------------------- | ---- | ---- | ------- |
| Installing requests    | X.Xs | Y.Ys | Zx      |
| Installing pandas      | X.Xs | Y.Ys | Zx      |
| Cold environment setup | X.Xs | Y.Ys | Zx      |

### Pros Discovered

- [ ] Speed improvements (quantify)
- [ ] Unified tool experience
- [ ] Better error messages
- [ ] Automatic virtual environment management
- [ ] Built-in Python installation

### Cons/Limitations Found

- [ ] Learning curve for existing workflows
- [ ] Tool maturity concerns
- [ ] Ecosystem compatibility issues
- [ ] Missing features vs specialized tools

## 🛠 Common Commands Reference

### Project Management

```bash
uv init [project-name]          # Create new project
uv add <package>                # Add dependency
uv remove <package>             # Remove dependency
uv sync                         # Install dependencies
uv lock                         # Update lockfile
```

### Python Management

```bash
uv python install <version>    # Install Python version
uv python list                 # List available versions
uv python uninstall <version>  # Remove Python version
```

### Running Code

```bash
uv run <command>                # Run in project environment
uv run --with <pkg> <command>   # Run with extra dependencies
uv tool run <tool>              # Run external tool
```

### Environment Management

```bash
uv venv                         # Create virtual environment
uv venv --python <version>      # Create with specific Python
```

## 🔗 Useful Resources

- [Official UV Documentation](https://docs.astral.sh/uv/)
- [UV GitHub Repository](https://github.com/astral-sh/uv)
- [Python Developer Tooling Handbook - UV Section](https://pydevtools.com/handbook/reference/uv/)
- [UV vs Other Tools Comparison](https://docs.astral.sh/uv/concepts/tools/)

## 📋 Migration Cheatsheet

### From pip + venv

```bash
# Old way
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt

# New way
uv sync
```

### From Poetry

```bash
# Old way
poetry install
poetry add requests

# New way
uv sync
uv add requests
```

### From pyenv

```bash
# Old way
pyenv install 3.12.0
pyenv local 3.12.0

# New way
uv python install 3.12
echo "3.12" > .python-version
```

## 🎯 Next Steps and Follow-up

- [ ] Integrate `uv` into CI/CD pipelines
- [ ] Create team migration guide
- [ ] Explore advanced configuration options
- [ ] Test with complex multi-package projects
- [ ] Evaluate for production deployments

## 📈 Summary Metrics

**Time Saved**: _TBD after exploration_  
**Commands Learned**: _TBD_  
**Migration Effort**: _TBD_  
**Overall Experience**: _TBD_

---

**Exploration Date**: [Insert Date]  
**UV Version**: [Insert Version]  
**Python Versions Tested**: [Insert Versions]  
**Operating System**: [Insert OS]

> 💡 **Pro Tip**: Use `uv --help` and `uv <subcommand> --help` throughout the day to discover features not covered in this guide!
