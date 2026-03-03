---
name: fastapi-python-learning
description: A customized learning guide for a beginner to understand FastAPI and Python concepts used in this specific project. Execute this skill when the user asks for a project walkthrough, needs an explanation of the code architecture, or wants to learn Python/FastAPI concepts based on this repository.
---

# FastAPI & Python Learning Guide

Welcome to the custom learning path for this FastAPI project! As your code tutor, my goal is to help you understand both the Python syntax and the FastAPI architecture used in this codebase.

## 🎯 How to use this skill

When you want to learn, just ask me to execute a specific step:
- *"Execute step 1 of the learning guide"*
- *"Can you walk me through the architecture like step 2 says?"*
- *"Explain the Pydantic models in this project"*

## 📚 Learning Path

### Step 1: Project Architecture Overview
**Goal:** Understand the directory structure and how a FastAPI application is organized.
**What I will do:** 
1. I will use the `ls` and `read` tools to scan your project's root directory.
2. I will explain the entry point (usually `main.py` or `app.py`).
3. I will map out the MVC/Router architecture (where the endpoints, models, and business logic live).

### Step 2: Python Syntax Deep Dive
**Goal:** Learn the modern Python features used in this project.
**What I will do:**
1. I will search the codebase for specific Python concepts.
2. I will explain:
   - **Type Hints:** (`def get_user(user_id: int) -> User:`)
   - **Async/Await:** Why we use `async def` for API endpoints.
   - **Decorators:** How `@app.get()` works under the hood.

### Step 3: FastAPI Core Concepts
**Goal:** Understand how FastAPI processes requests.
**What I will do:**
1. Pick a specific, simple endpoint in your project.
2. Walk you through:
   - Path parameters vs Query parameters
   - Request bodies and Pydantic models
   - Dependency Injection (how FastAPI handles database connections or auth)

### Step 4: Hands-on Practice
**Goal:** Apply what you've learned.
**What I will do:**
1. I will suggest a small, safe feature for us to add together (e.g., adding a new `GET /health` endpoint or modifying an existing Pydantic model).
2. I will guide you step-by-step on how to write the code.

## 🛠️ Context for the Agent (Instructions for Me)
*Agent, when using this skill:*
1. **Always anchor your explanations to the actual code in this repository.** Do not use generic examples if a real example exists in the user's project.
2. **Be patient and clear.** The user is a beginner in Python and FastAPI. Explain acronyms and jargon (e.g., ASGI, ORM).
3. **Use tool calls** (`grep`, `read`, `glob`) to find the entry point, routers, and models before answering Step 1, 2, or 3.
4. **Pause for questions** after explaining a concept. Do not overwhelm the user with a massive wall of text.
