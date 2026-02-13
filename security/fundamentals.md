# Python Security Fundamentals

This chapter provides a comprehensive exploration of the security mechanics inherent in Python development. 

To perform threat modelling for the use of Python software or when creating Python programs, insight into the Python architecture is required.

The core components when using a Python program are:

- **Execution environment**: This is the target environment where Python programs are executed.

- **Python interpreter software**: This is the software needed to execute Python software.

- **Dependencies**: The dependencies needed within the execution environment vary depending on the type of Python software.

The core components for when creating or running a Python program are:

- **Execution environment**: This is the target environment where Python programs are executed.

- **Python interpreter software**: This is the software needed to execute Python software.

- **Development tools**: This refers to all the software used to create Python software. Every organisation or developer may use different development tools. From a threat-modelling perspective—especially from a supply chain viewpoint—the development software and the processes used matter. Some tools include editors, notebooks, test software, test data, version control, issue management systems, and release tools.

The focus then shifts outward to the Python Attack Landscape, examining the external risks posed by the modern software supply chain and third-party dependencies. By understanding this environment, we categorise specific Python Security Threats. 


The following section provides key insights regarding the Python execution model. The Python execution model is relevant for when **creating Python** software or when only **using** Python software. The section outlines how the underlying runtime influences the safety of your code. Building on this technical foundation, we define a formal Python Threat Model to identify trust boundaries and protect vital assets. This section ends with the [Python Attack landscape](security/attacklandscape), a deep dive on all common security threats that are relevant for Python software.


```{tableofcontents}