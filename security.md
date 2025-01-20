# Security

Having a separate section on security is **WRONG**. 

Security is a process that must be embedded within your development flow. At every step. From design to production and in all maintenance and operations steps.

:::{important}
The bare minimum to do is:
[Security by design](https://nocomplexity.com/documents/securitybydesign/sdlc.html)
:::

:::{tip}
Professional Python programmers SHOULD be familiar with basic security threats and measurements to prevent security risks.
So: READ AND USE [The Open Security Reference Architecture](https://nocomplexity.com/documents/securityarchitecture/introduction.html)
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

