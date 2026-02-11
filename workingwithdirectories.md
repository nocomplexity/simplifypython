# Working with directories


Most Python code that deals with files and folders should nowadays use the **`pathlib`** module instead of the older `os` and `os.path` functions.

`pathlib` offers:

- Cleaner, more readable code
- Platform-independent path handling (`/` works on Windows too)
- Object-oriented interface
- Chainable operations
- Better exception messages


:::{tip} 
Use `pathlib` for all new code. Only use os when you specifically need low-level operations (os.scandir, os.walk, os.chmod, process handling, etc.) or when supporting very old Python versions (< 3.4).
:::


Why use pathlib?
- Object-Oriented: Paths are objects, not just strings, so you can call methods directly on them.

- Readable: The / operator for joining paths is much cleaner than nested os.path.join calls.

- Cross-platform: It handles the difference between Windows (\) and Unix (/) separators automatically.


## Importing pathlib

```python
from pathlib import Path
```


You usually only need this one import for most file-system tasks.

## Creating Path objects

```
# Common useful paths

home       = Path.home()                     
cwd        = Path.cwd()                      # current working directory
desktop    = Path.home() / "Desktop"
document   = Path.home() / "Documents"
config     = Path.home() / ".config" / "myapp" / "settings.toml"
project    = Path("/home/maikel/projects/my-awesome-app")
readme     = project / "README.md"
```

## Listing files in a directory

```python
folder = Path.home() / "projects"

# All entries (files + folders)
for item in folder.iterdir():
    print(item.name)

# Only file names as list
files = [p.name for p in folder.iterdir()]
print(files)

# Only Python files
py_files = [p.name for p in folder.glob("*.py")]
print(py_files)

# Recursively find all .md files
markdowns = list(folder.rglob("*.md"))
```

## Changing the current working directory

`pathlib` does not have a method to change the current directory — you still use `os` for that:

```python
import os

os.chdir(Path.home() / "projects")
# or
os.chdir(str(Path.home() / "projects"))   # sometimes needed for older code
```
But you can easily get & show the current directory as a Path:
```python
print(Path.cwd())
```

## Checking existence, file vs directory

```python
p = Path("notes.txt")

print(p.exists())       # True / False
print(p.is_file())      # True if regular file
print(p.is_dir())       # True if directory
print(p.is_symlink())   # True if symbolic link
```

## File size and modification time

```python
from datetime import datetime

photo = Path("vacation-2025.jpg")

# File size in bytes
size = photo.stat().st_size
print(f"Size: {size:,} bytes")

# Last modification time
mtime = datetime.fromtimestamp(photo.stat().st_mtime)
print(mtime.strftime("%Y-%m-%d %H:%M:%S"))
```

## Creating, deleting, renaming

```python
# Create directories (like mkdir -p)
report_folder = Path.home() / "Reports" / "2026" / "Q1"
report_folder.mkdir(parents=True, exist_ok=True)

# Create an empty file
(Path("temp.txt")).touch()

# Delete file
(Path("old.log")).unlink(missing_ok=True)

# Delete directory (must be empty)
(Path("empty_folder")).rmdir()

# Rename / move
source = Path("draft.md")
source.rename(source.with_name("final.md"))
# or move to different folder
source.rename(Path.home() / "Archive" / source.name)
```

## Building paths cleanly

```python
# Very readable and platform-safe
logfile = (
    Path.home()
    / ".local"
    / "share"
    / "myapp"
    / "logs"
    / f"app-{datetime.now():%Y%m%d}.log"
)

# Alternative style
config = Path("config") / "prod" / "database.ini"
```

## Quick reference table – old vs new

| Task                        | Old (`os` / `os.path`)                                | Modern (`pathlib`)                                              | Notes                              |
|-----------------------------|-------------------------------------------------------|-----------------------------------------------------------------|------------------------------------|
| Current working directory   | `os.getcwd()`                                         | `Path.cwd()`                                                    | —                                  |
| User home directory         | `os.path.expanduser("~")`                             | `Path.home()`                                                   | Platform-independent               |
| Join path components        | `os.path.join(a, b, c)`                               | `Path(a) / b / c`  or  `Path(a, b, c)`                          | `/` operator is very readable      |
| Base filename               | `os.path.basename(p)`                                 | `Path(p).name`                                                  | Includes extension                 |
| Directory part              | `os.path.dirname(p)`                                  | `Path(p).parent`                                                | Returns a Path object              |
| Exists (file or dir)        | `os.path.exists(p)`                                   | `Path(p).exists()`                                              | —                                  |
| Is regular file?            | `os.path.isfile(p)`                                   | `Path(p).is_file()`                                             | Does not follow symlinks           |
| Is directory?               | `os.path.isdir(p)`                                    | `Path(p).is_dir()`                                              | Does not follow symlinks           |
| File size (bytes)           | `os.path.getsize(p)`                                  | `Path(p).stat().st_size`                                        | Requires `.stat()`                 |
| Last modification time      | `os.path.getmtime(p)`                                 | `Path(p).stat().st_mtime`                                       | Unix timestamp (float)             |
| List directory contents     | `os.listdir(path)`                                    | `[p.name for p in Path(path).iterdir()]`                        | `iterdir()` → Path objects         |
| Pattern matching (glob)     | `glob.glob("*.py")`                                   | `Path().glob("*.py")`                                           | Returns iterator of Path objects   |
| Recursive glob              | —                                                     | `Path().rglob("*.py")`                                          | Like `**/*.py` in shell            |
| Delete / remove file        | `os.remove(p)`                                        | `Path(p).unlink(missing_ok=True)`                               | `missing_ok` prevents exceptions   |
| Create directory tree       | `os.makedirs(path, exist_ok=True)`                    | `Path(path).mkdir(parents=True, exist_ok=True)`                 | `parents=True` ≈ `mkdir -p`        |



## Examples

```python
# Find largest file in folder
biggest = max(folder.iterdir(), key=lambda p: p.stat().st_size if p.is_file() else 0)
print(f"Largest file: {biggest.name} – {biggest.stat().st_size:,} bytes")

# Backup all .py files
for py in folder.rglob("*.py"):
    backup = py.with_suffix(".py.bak")
    py.replace(backup)           # atomic move/rename

# Create dated report folder if needed
today = datetime.now().strftime("%Y-%m-%d")
(Path("reports") / today).mkdir(exist_ok=True)
```
