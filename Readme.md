# Hands-On AI Workshop: From Python Tools to MCP (and beyond)

This repository contains a hands-on workshop that demystifies how modern AI systems work, designed for both technical and non-technical audiences.

This workshop is designed to build intuition step by step:
![Workshop roadmap](https://raw.githubusercontent.com/mhornstein/AI_Foundations_Workshop/main/images/roadmap.png)

* The workshop is delivered through `workshop.ipynb`, which contains all the required material.  
* **Optional:** The file `bonus-manual-mcp-client-flow.md` is an optional deep dive for curious readers who want to understand how an MCP client works behind the scenes. It is not part of the workshop.

---

## Running Locally (Optional)

The notebook is designed to run on Google Colab / Drive, but it can also be executed locally:

1. Install Python (I used Python 3.10.8 on Windows).

2. Create a virtual environment:
    ```bash
    py -3.10 -m venv .venv
    ```
3.  Activate it:
   
    ```bash
    .\.venv\Scripts\Activate.ps1
    
    ```
    
4.  Install dependencies:
    
    ```bash
    pip install -r requirements.txt
    
    ```
