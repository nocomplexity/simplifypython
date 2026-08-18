# Overview

:::{tip} 
Performance matters — but wisely
:::

Python is often labelled “slow”. **That label is misleading.**  

:::{admonition} Speed of development matters
:class: note

The time from idea to working solution is often more important than raw execution speed.
:::


What matters most for the majority of problem-solving work is how quickly you can move from an idea to a correct, working solution. In this respect Python is extremely fast. Its dynamic nature removes the friction of compilation, rigid type declarations and lengthy build cycles, allowing rapid experimentation and iteration.

There is little to gain—and much to lose—by trying to turn Python into a statically typed language. The language’s power lies precisely in its dynamic core. Embracing that dynamism, rather than fighting it, is usually the more productive path.

Whether you work alone or with the assistance of modern AI tools, the combination of Python’s flexibility and its rich ecosystem makes the overall process of solving problems remarkably fast.


With the right approach and tools, Python can deliver excellent performance for large-scale numerical work while retaining the advantages that make it such a productive language.


Solving problems with computers should be fast. Python is an outstanding tool for this purpose: it lets you harness powerful hardware and sophisticated algorithms with remarkable ease. Yet Python is frequently described as slow. This reputation is largely undeserved.

Python itself is not inherently slow; used with the right libraries and techniques it can perform massive numerical calculations at high speed.

## How to start improving performance

1. **Ensure the code is correct.**  
   Before any optimisation, write tests and simple benchmark scripts. Without them you cannot tell whether a change is an improvement, a regression, or simply random noise.

2. **Refactor first.**  
   Prefer the simplest, most appropriate libraries for everyday tasks. Clean, clear code is easier to profile and easier to accelerate later.

Do **not** rewrite entire programs in C, C++, Go or Rust as a first resort. Performance-critical sections are usually a small fraction of a codebase. Abandoning Python wholesale is almost never necessary.

Python continues to offer decisive advantages:

- **Rapid iteration** – no compile step during development. Interactive notebooks are especially powerful for prototyping (see the NOCX book for practical guidance).
- **A rich ecosystem** – mature, highly optimised libraries such as NumPy, pandas, PyTorch and many others.
- **Readable code** that remains accessible to humans.
- **A large pool of skilled developers** – far more people can productively improve a Python codebase than can work effectively in languages that demand compilation.
- **Easy onboarding** for new team members.

The Pareto principle applies strongly here: roughly 80 % of runtime often comes from 20 % of the code. Identify the true bottlenecks first. In many cases, modest improvements to the Python code or a better algorithmic design yield larger gains than a complete rewrite.

Creating high-performance Python is still not taught as systematically as it could be. Always ask whether a redesign of the algorithm or a more careful use of existing libraries would be a better investment of effort than low-level reimplementation.