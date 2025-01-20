# Naming Conventions

## PEP8

[PEP8](https://www.python.org/dev/peps/pep-0008/) is the "Style Guide for Python Code". Reading this is good. So check the document:


But applying PEP8 is even better. To simplify the use of PEP8 many tools have been created. So use one.

```{todo}
  
   Check Black linter and checker tool! Include link e.g.
```

pycodestyle is a tool to check your Python code against some of the style conventions in PEP 8.


A simple summary of PEP8:

| Type                  | Public          | Internal       |
|----------------------|-----------------|----------------|
| Packages             | `lower_with_under` |                |
| Modules              | `lower_with_under` | `_lower_with_under` |
| Classes              | `CapWords`       | `_CapWords`     |
| Exceptions           | `CapWords`       |                |
| Functions            | `lower_with_under()` | `_lower_with_under()` |
| Global/Class Constants | `CAPS_WITH_UNDER` | `_CAPS_WITH_UNDER` |
| Global/Class Variables | `lower_with_under` | `_lower_with_under` |
| Instance Variables    | `lower_with_under` | `_lower_with_under` (protected) |
| Method Names         | `lower_with_under()` | `_lower_with_under()` (protected) |
| Function/Method Parameters | `lower_with_under` |                |
| Local Variables       | `lower_with_under` |                |