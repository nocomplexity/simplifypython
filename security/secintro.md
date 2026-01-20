# Introduction

Python is the most widely used programming language worldwide, valued for its readable syntax and extensive ecosystem. Its accessibility makes it suitable for a broad audience, including occasional programmers, academic researchers and professional developers.

Python plays a central role in modern computing. It powers some of the world’s largest websites and web applications, serving as a key driver of advances in artificial intelligence and machine learning. Its comprehensive libraries and adaptability have established it as a standard tool across scientific research and data-intensive disciplines.

In addition to its academic and research applications, Python is deeply integrated into the operations of millions of companies and supports a vast number of software systems and applications globally. This combination of versatility, scalability, and community support underpins Python’s position as a foundational technology in contemporary computing.

In today’s digital world, cybersecurity remains a critical concern. This applies equally to using or creating Python software: preventing vulnerabilities starts with a solid architecture, but even well-written code—including AI-generated code—is not secure by default.

Validating Python code for potential vulnerabilities is therefore essential, whether you are writing your own programs or relying on code developed by others.

:::{hint} 
Security is a process that must be embedded within your development flow at every stage, from design through to production, maintenance, and operations. For those using or developing Python programs, this means that security should, at a minimum, be integrated into the initial design or architecture.
:::

:::{admonition} TLDR - If you short on time
:class: important
The bare minimum to do as programmer is:
* Follow and use the [Python Secure Coding Guidelines](https://nocomplexity.com/documents/codeaudit/securecoding.html).

and:

* Practice [Security by design](https://nocomplexity.com/documents/securitybydesign/sdlc.html).
:::


:::{tip}
If you are a professional Python programmer, make sure you become familiar with basic security threats and the measures used to prevent security risks.

Read and use: [The Open Security Reference Architecture](https://nocomplexity.com/documents/securityarchitecture/introduction.html)

:::


## Python Security Model  

Developing secure programs in Python requires understanding its strengths and limitations in handling security. Below are some critical insights and best practices to help you build secure Python applications.  

### Key Recommendations  

- **Follow a Security Checklist**: Start with a comprehensive security checklist, such as this [simple security checklist](https://nocomplexity.com/documents/securityarchitecture/prevention/simple-checklists.html), to identify and mitigate potential vulnerabilities.  

- **Understand Privilege Separation**:  
  Python, by design, does not implement internal privilege separation, which increases the attack surface. If an attacker can execute arbitrary Python code, they effectively gain full access to the system.  

  **Solution**: Implement privilege separation outside Python by running it within a sandboxed environment. This reduces risks by isolating the Python process from critical system resources.  

### Bytecode Concerns  

- **Lack of Bytecode Safety**: CPython does not verify the safety of bytecode. If an attacker can execute arbitrary bytecode, they could import and run sensitive code. However, this should be considered a secondary concern since code execution implies significant compromise.  

- **Avoid Building Sandboxes in CPython**: Creating a secure sandbox inside CPython is impractical due to the extensive attack surface. Python's rich introspection capabilities (e.g., the `inspect` module) and features that execute code on demand make it challenging to enforce strict isolation.  

### Examples of Potential Exploits  

- A literal string like `'\N{Snowman}'` automatically imports the `unicodedata` module.  
- Code designed to log warnings can potentially be abused to execute malicious code.  

### Secure Development Approach  

For robust security, do not rely on Python itself for sandboxing. Instead, encapsulate CPython in a dedicated, externally managed sandbox. This design ensures that the Python environment remains isolated, significantly reducing the risk of exploitation.  

