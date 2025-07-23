# py_sandboxer

A lightweight sandboxing utility for evaluating and executing Python expressions under a simple ruleset.

## Usage

```python
from py_sandboxer import sandbox_eval

# use built-in presets
result = sandbox_eval("math.sqrt(16)", config="math_only")
print(result)  # 4
```
