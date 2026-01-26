# How To Harden Path Operations

## The Challenge

The `pathlib` module is the modern, "Pythonic" standard for filesystem interaction. However, its high-level abstraction is a double-edged sword. While it makes code more readable, it often masks the underlying complexity of filesystem security. The core challenge is that `Path` objects act as **filesystem access sinks**; when they interact with untrusted input without rigorous validation, they become direct conduits for system exploitation.

## The Threat

Using `Path` objects insecurely primarily exposes applications to **Path Traversal** (CWE-73). By injecting sequences like `../`, an attacker can "break out" of the intended directory to access sensitive system files.

Beyond traversal, secondary threats include:

* **Denial of Service (DoS):** Using `read_text()` or `read_bytes()` on attacker-controlled paths can force the application to load massive files (like `/dev/zero`) into memory, crashing the service.
* **Insecure File Modes:** Improper use of write/append modes can allow attackers to overwrite critical configurations.
* **Race Conditions (TOCTOU):** A gap between checking file permissions and performing the operation can be exploited to swap a safe file for a malicious one.

## Vulnerable Code Example

In the following examples, the application blindly trusts `user_input`, allowing it to control the resulting path or exhaust system resources.

```python
from pathlib import Path

# Vulnerable: Direct path traversal risk
user_input = "../../etc/passwd"
path = Path(user_input)
with path.open("r") as f:
    data = f.read()

# Vulnerable: Memory exhaustion via read_text
config_path = Path(user_input)
config = config_path.read_text()

# Vulnerable: Unvalidated binary read
binary_data = Path(user_input).read_bytes()

```

## Secure Mitigation

The gold standard for securing `Path` objects is **Path Anchoring**. This involves resolving the absolute path and verifying that it remains a child of a trusted base directory.

```python
from pathlib import Path

# 1. Define and resolve a trusted base directory
base_dir = Path("/app/data").resolve()
user_input = "../../etc/passwd" 

# 2. Join input with base and resolve to eliminate '../' and symlinks
target_path = (base_dir / user_input).resolve()

# 3. Security Check: Ensure the resolved path is inside the base directory
if base_dir in target_path.parents:
    # 4. Resource Check: Prevent DoS by limiting file size (e.g., 10MB)
    if target_path.exists() and target_path.stat().st_size < 10_000_000:
        data = target_path.read_text(encoding="utf-8", errors="strict")
else:
    raise PermissionError("Access Denied: Path escape detected.")

```

## Discussion

Securing `pathlib` is less about the module itself and more about the implementation logic. 

**The `.resolve()` method is the most critical line of defence**; it canonicalizes the path, meaning it resolves all symbolic links and removes `..` components before you perform your validation check.

Developers should also move away from "Check-then-Act" patterns where possible to avoid race conditions. When using `read_text()`, always explicitly define the `encoding` and `errors` parameters to prevent the application from making dangerous assumptions about the data. 

Finally, always operate under the **Principle of Least Privilege**: ensure the OS-level user running the Python script only has access to the specific directories required for the task.


More information:

* https://docs.python.org/3/library/pathlib.html 
* [CWE-73: External Control of File Name or Path](https://cwe.mitre.org/data/definitions/73.html)