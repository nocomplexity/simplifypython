# Limitations of AI and LLMs in Python SAST


ML/AI solutions are not applicable to every problem. Validating Python code on security weakness is a area where using ML/AI technology should only be applied with care. 

Many SAST scanners for Python code claim perfect results with the use of AI technology. Often marketing, but recent years there is an explosion of:
- SAST scanners created with AI vibe-coding tools and
- SAST scanners that use AI agents for scanning your code. 


:::{caution} 
AI enabled Python SAST tools are still far from good enough. In the best case scenario, you’ll only be disappointed. But the risk of a false sense of security is enormous.
:::

Disadvantages of AI powered SAST scanners:

- **No single tool can judge the context** where a program is used, how it is used and by whom. There is a large difference between using a SAST scanner on code from a developer perspective, or to use a SAST scanner as a potential user of some Python software. Based on findings you will and must judge risks differently. Judging risks is always context dependent and can still not be automated. 


+++

- **Limited transparency and trust Issues**:  Using non FOSS solutions for cybersecurity is a large risk. Too many closed commercial cyber security solutions have proven to create security disasters instead of mitigating security risks.


+++

- **Security and Privacy Concerns**: Using AI tools, especially those that rely on cloud-based Large Language Models (LLMs), can introduce new security and privacy risks. Most AI powered SAST scanners require you to use some insecure AI agent on your code with a connection to a ‘black-box’. Using untrusted AI agents that have a connection to a remote service is a receipt for security and privacy disasters.


+++

- **AI/ML solutions do not fit every problem.** Or to put it even more clearly: In most cases applying AI is overkill, too expensive, does not work, and other traditional software solutions make far more sense. If it’s possible to structure a set of rules of “if-then scenarios” to handle a problem, then there is usually no need to use AI. And finding static security validation is in essence validation against clear rules. You do not want to worry about enough training data, validity of the result and the fear of looking at results that are created by a hallucinating AI application.

+++

- Unlike traditional software governed by explicit, deterministic logic, **AI/ML models are probabilistic**. This means that even with identical input code, outcomes can vary due to stochastic (random) processes during training, parallel processing on hardware, and the use of 'temperature' or 'seeds' in generative outputs.


:::{danger} 
So DO NOT rely on SAST scanners that are powered by AI-agents / LLM systems to solve your cyber security problems! AI agents are still struggling to write secure code.

**If you do use AI cyber solutions, you can be more vulnerable for security breaches instead of less.**
:::


AI solutions that are built upon LLMs for cyber security problems are still far from mature. HIDS systems (Host Intrusion Detection Systems) have a long history of applying ML technologies as well as spam-filters. Creating security products that ‘learns’ from patterns is not new for security. AI/ML technologies have been applied for many years for HIDS systems and spam-filters. Applying AI for cyber security has been done for many years with variable success. 


AI/ML technologies can and do help with cyber security, especially with DAST (Dynamic Application Security Testing) and creating better fuzzers. Cyber security professionals should be conservative with adopting new IT hypes for security testing tools. IT hypes like AI-agents and LLMs are not the holy grail for solving our cyber security problems. This is because in the end you always pay more for cyber security solutions, but the risks still remain. Cyber security is not a product, but a process. 

[Python Code Audit](https://codeaudit.nocomplexity.com), a modern Python-specific SAST scanner, uses AI/ML in an ethical and secure way. See the Python Code Audit [documentation](https://nocomplexity.com/documents/codeaudit/architecture.html#use-of-ai) for a deep dive into how AI/ML is used within this tool.

A great deal of research has been conducted, and continues to be undertaken, into the application of LLMs for security. Further information is provided below::

- Do LLMs consider security? an empirical study on responses to programming questions, https://link.springer.com/article/10.1007/s10664-025-10658-6  
