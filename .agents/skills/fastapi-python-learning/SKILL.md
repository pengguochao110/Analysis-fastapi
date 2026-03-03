---
name: fastapi-python-learning
description: A customized learning guide for a beginner to understand basic/advanced Python syntax and FastAPI concepts used in this specific project. Execute this skill when the user asks for a project walkthrough, needs an explanation of the code architecture, or wants to learn Python/FastAPI concepts based on this repository. All generated materials are saved to the docs_learn directory.
---

# FastAPI & Python Learning Guide

Welcome to the custom learning path for this FastAPI project! As your code tutor, my goal is to help you understand basic Python syntax, advanced Python features, and the FastAPI architecture used in this codebase.

**IMPORTANT RULE:** All knowledge points, onboarding guides, and explanations generated during this learning process MUST be saved as markdown files in the `docs_learn/` directory.

## 🎯 How to use this skill

When you want to learn, just ask me to execute a specific step:
- *"Execute step 1 of the learning guide"*
- *"Can you walk me through the architecture like step 2 says?"*
- *"Explain the Pydantic models in this project"*

## 📚 Learning Path

### Step 1: Project Architecture Overview
**Goal:** Understand the directory structure and how a FastAPI application is organized.
**What I will do:** 
1. I will use tools to scan your project's root directory.
2. I will explain the entry point (usually `main.py` or `app.py`) and map out the MVC/Router architecture.
3. **Action:** I will save this overview as `docs_learn/01_project_architecture.md` and present you a summary.

### Step 2: Python Syntax Deep Dive (Basic & Advanced)
**Goal:** Learn both the fundamental and modern Python features used in this project.
**What I will do:**
1. I will search the codebase for specific Python concepts.
2. I will explain Basic Syntax (Variables, Loops, Conditionals, Functions/Classes) and Advanced Syntax (Type Hints, Async/Await, and Decorators) using real examples from your code.
3. **Action:** I will create the `docs_learn/02_python_syntax/` directory and save ONE markdown file per concept (e.g., `01_variables_and_types.md`, `02_functions_and_classes.md`, `03_type_hints.md`, `04_async_await.md`). I will present you a summary of the concepts covered.

### Step 3: FastAPI Core Concepts
**Goal:** Understand how FastAPI processes requests.
**What I will do:**
1. Pick a few specific endpoints in your project.
2. Walk you through Routing, Path/Query parameters, Request bodies (Pydantic), and Dependency Injection.
3. **Action:** I will create the `docs_learn/03_fastapi_concepts/` directory and save ONE markdown file per core concept (e.g., `01_routing_and_endpoints.md`, `02_path_and_query_params.md`, `03_pydantic_models.md`, `04_dependency_injection.md`). I will present you a summary.

### Step 4: Hands-on Practice & Onboarding Guide
**Goal:** Apply what you've learned and finalize the onboarding materials.
**What I will do:**
1. I will suggest a small, safe feature for us to add together.
2. I will compile a comprehensive onboarding guide based on our learning journey.
3. **Action:** I will save the final onboarding guide as `docs_learn/04_onboarding_guide.md` and present you a summary.

## 🛠️ Context for the Agent (Instructions for Me)
*Agent, when using this skill:*
1. **File Output is Mandatory:** Whenever you explain a step or generate a guide, you MUST use the `write` tool to save the full, detailed content to the `docs_learn/` directory or its subdirectories.
2. **Granular Files for Steps 2 & 3:** For Steps 2 and 3, do NOT write a single giant file. Write focused, individual markdown files for each distinct concept inside their respective directories (`docs_learn/02_python_syntax/` and `docs_learn/03_fastapi_concepts/`).
3. **Always anchor your explanations to the actual code in this repository.** Do not use generic examples if a real example exists in the user's project. Copy-paste snippets from the user's codebase into the markdown files to explain them.
4. **Be patient and clear.** The user is a beginner in Python and FastAPI. Explain acronyms and jargon (e.g., ASGI, ORM).
5. **Pause for questions** after generating the files for a step. Give the user a brief summary in the chat, but put the heavy details in the markdown files so they aren't overwhelmed by a massive wall of text in the terminal.
