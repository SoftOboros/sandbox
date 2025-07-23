📜 INSTRUCTIONS.md — Codex Setup Script

# Py Sandboxer Codex Instructions

## 🏗️ Project Scaffold

Create a Python package named `py_sandboxer` with the following structure:

py_sandboxer/
├── init.py
├── sandbox.py
├── rules.py
├── exceptions.py
tests/
└── test_sandbox.py
setup.py
README.md
pyproject.toml


## ✨ `py_sandboxer/__init__.py`

Export the public API:
```python
from .sandbox import sandbox_eval, sandbox_exec, load_ruleset
from .exceptions import SandboxViolation

__all__ = [
    "sandbox_eval",
    "sandbox_exec",
    "load_ruleset",
    "SandboxViolation",
]
🔒 py_sandboxer/sandbox.py

Implement:

sandbox_eval(expr: str, config: dict = None) -> Any
sandbox_exec(code: str, config: dict = None) -> dict
Internally load rules using load_ruleset() from rules.py
Both functions should accept optional config objects (dicts or paths).

📜 py_sandboxer/rules.py

Implement:

load_ruleset(config: Union[dict, str]) -> dict
filter_globals(globals_dict: dict, rules: dict) -> dict
Support .gitignore-like pattern matching for safe/deny lists.
❗ py_sandboxer/exceptions.py

class SandboxViolation(Exception):
    pass
🧪 tests/test_sandbox.py

Basic tests:

Allow and deny math.sqrt, os.system, etc.
Confirm blocked access raises SandboxViolation.
⚙️ setup.py

Create a standard setuptools setup with:

from setuptools import setup, find_packages

setup(
    name='py_sandboxer',
    version='0.1.0',
    packages=find_packages(),
    install_requires=[],
)
📦 pyproject.toml

Include minimal metadata for compatibility:

[build-system]
requires = ["setuptools"]
build-backend = "setuptools.build_meta"
📘 README.md

Explain usage with examples like:

from py_sandboxer import sandbox_eval

sandbox_eval("math.sqrt(16)", config={"allow": ["math.sqrt"]})
Let me know if you want Codex to support AST rewriting, tracing, or Jupyter-safe context controls in future expansions.