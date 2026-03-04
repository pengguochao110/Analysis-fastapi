---
name: fastapi-python-learning
description: A customized, interleaved learning guide for a beginner to understand FastAPI and Python concepts used in this specific project. Execute this skill when the user asks for a project walkthrough or wants to learn Python/FastAPI concepts based on this repository. All generated materials are saved to the docs_learn directory.
---

# FastAPI & Python Learning Guide

Welcome to the custom learning path for this FastAPI project! This guide uses a highly contextual, interleaved learning loop: we will learn one FastAPI concept at a time using your project's code, and then immediately break down the Python syntax used in that exact code.

**IMPORTANT RULE:** All knowledge points, onboarding guides, and explanations generated during this learning process MUST be saved as markdown files in the `docs_learn/` directory.

## 🎯 How to use this skill

When you want to learn, just ask me to execute a specific step:
- *"Execute step 1 of the learning guide"*
- *"Start the learning loop for the first FastAPI concept"*
- *"I understand the concept, let's move to the Python syntax"*

## 📚 Learning Path

### Step 1: Project Architecture Overview
**Goal:** Understand the directory structure and how a FastAPI application is organized.
**What I will do:** 
1. I will use tools to scan your project's root directory.
2. I will explain the entry point (usually `main.py` or `app.py`) and map out the MVC/Router architecture.
3. **Action:** I will save this overview as `docs_learn/01_project_architecture.md` and present you a summary.

### Step 2: The Interleaved Learning Loop (FastAPI -> Python)
**Goal:** Learn FastAPI concepts and Python syntax contextually, step-by-step.
**What I will do (The Loop):**

For each core FastAPI concept in the project (e.g., Endpoints, Pydantic Models, Dependency Injection, Database Sessions), I will follow this exact cycle:

*   **Phase A (FastAPI Concept):** I will pick one FastAPI concept and show you the exact source code in your project that uses it. I will explain how the FastAPI concept works.
*   **Phase B (Confirm & Save):** I will ask if you understand. Once you confirm, I will save this explanation to a dedicated file in `docs_learn/03_fastapi_concepts/` (e.g., `01_routing_and_endpoints.md`).
*   **Phase C (Python Syntax):** Looking *only* at the code snippet we just discussed, I will break down the Python syntax used (both basic like variables/functions, and advanced like type hints/decorators/async).
*   **Phase D (Confirm & Save):** I will ask if you understand the Python syntax. Once you confirm, I will save this syntax explanation to a dedicated file in `docs_learn/02_python_syntax/` (e.g., `01_syntax_for_routing.md`).
*   **Phase E (Iterate):** We will loop back to Phase A for the *next* FastAPI concept, until all core concepts in the project are covered.

### Step 3: Hands-on Practice & Onboarding Guide
**Goal:** Apply what you've learned and finalize the onboarding materials.
**What I will do:**
1. I will suggest a small, safe feature for us to add together based on what we learned in the loop.
2. I will compile a comprehensive onboarding guide based on our learning journey.
3. **Action:** I will save the final onboarding guide as `docs_learn/04_onboarding_guide.md` and present you a summary.

## 🛠️ Context for the Agent (Instructions for Me)
*Agent, when using this skill:*
1. **Follow the Loop Strictly:** In Step 2, DO NOT explain everything at once. Pick ONE FastAPI concept, show the code, explain it, wait for the user to confirm, save it, then do the Python syntax for that code, wait for the user to confirm, save it, and repeat.
2. **File Output is Mandatory:** Whenever the user confirms understanding, use the `write` tool to save the full, detailed content to the respective `docs_learn/` subdirectories.
3. **Always anchor your explanations to the actual code in this repository.** Do not use generic examples. Copy-paste snippets from the user's codebase into the chat and markdown files.
4. **Be patient and clear.** The user is a beginner in Python and FastAPI. Explain acronyms and jargon.
