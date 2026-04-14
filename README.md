# DS&A • AI-Powered Study Hub by Batu Koray Masak
### Özyeğin University · CS201

This repository is a self-contained study environment for Özyeğin University's CS201 Data Structures course. It pairs exam-style Java stub implementations and JUnit test suites with a pre-configured AI tutor persona — so that any agentic AI coding assistant (Claude Code, OpenAI Codex CLI, Gemini CLI, etc.) that reads the project automatically becomes a Socratic study partner rather than a solution dispenser.

---

### Overview on how to use this repository to study for CS201
![Overview Screenshot](https://raw.githubusercontent.com/batukoray/assets_of_mine/refs/heads/main/DS%26A_Overview.png)
> We have the code editing in the middle, and terminal on the right hand side with OpenAI Codex (or you can have Claude Code or equivalent) open.
> 
> The file `AGENTS.md` (and its mirror `CLAUDE.md`) is the AI's instruction manual. The moment you open this project in an AI-aware tool, the assistant reads those instructions and operates under a strict set of rules:

## How It Works

- It will **never** write or complete your implementation for you.
- It will **read your code**, **run tests**, and **give targeted hints** — in that order.
- It escalates hints gradually: vague nudge → specific line → behavioral explanation → "move on and come back."
- It asks Socratic questions that force you to reason through the logic yourself.

This mirrors the exam environment: you are expected to write the code, the AI just makes the feedback loop faster than office hours.

---


## Setup

```bash
git clone https://github.com/batukoray/DS-A_Study_Hub.git
cd DS-A_Study_Hub
```

---

## Using the AI Tutor

### Claude Code

[Claude Code](https://claude.ai/code) reads `CLAUDE.md` automatically on startup.

```bash
cd DS-A_Study_Hub
claude
```

Once inside the session, simply describe what you're working on:

> "I'm implementing `bottomTwo()` in `Tree.java`. Here's my attempt, can you check it?"

> "I'm stuck on the edge case for `enqueue` when the circular array is full."

> "Run the Queue tests and tell me what's failing."

Claude will read your implementation, run 1–2 normal test cases and 1 edge case, report what it finds, and guide you with hints — never with solutions.

### OpenAI Codex CLI

Codex CLI picks up `AGENTS.md` automatically as its system-level project instructions.

```bash
cd DS-A_Study_Hub
codex
```

Interact the same way as with Claude Code. The same rules apply — the AI is bound by `AGENTS.md`.

### Other Tools (Gemini CLI, Cursor, etc.)

Any tool that supports project-level instruction files (`AGENTS.md`, `CLAUDE.md`, `.cursorrules`, system prompts, etc.) can be configured to use this repo. Point the tool at the relevant instruction file, or paste the contents of `AGENTS.md` into the system prompt manually.

---

## Exam Rules

These rules apply to all questions in this repository and reflect the actual exam constraints:

1. Write **only one function** per question in Java.
2. **Do not validate input** — assume it is always correct.
3. Unless explicitly stated otherwise:
   - The input data structure is **not empty**.
   - Time complexity **does not matter**.
   - You **cannot use extra data structures**.
   - You **can use any method** already defined in the given data structure class.

---

## Midterm Coverage

| Midterm | Week | Topics                                                 |
|---|---|--------------------------------------------------------|
| Midterm 1 | Week 7 (23–27 Mar 2026) | Introduction, Algorithm Analysis, Linked Lists, Stack  |
| Midterm 2 | Week 10 (13–17 Apr 2026) | Queue, Trees, Hashing                                  |
| Midterm 3 | Week 14 (11–15 May 2026) | Heaps, Disjoint Sets, Graph Basics, DFS, BFS           |

> A topic introduced in the **same week** as a midterm is **probably** not included in that midterm, but it's best practice to ask the course instructor.

---

## Repository Structure

```
DS-A_Study_Hub/
├── src/
│   ├── main/java/
│   │   ├── Array/
│   │   │   ├── Queue.java          # Circular array-based queue
│   │   │   ├── Stack.java
│   │   │   ├── Hash.java           # Open addressing, linear probing
│   │   │   ├── DisjointSet.java
│   │   │   ├── Heap/               # Min/Max heaps, D-heaps
│   │   │   ├── Sort/               # Bubble, Insertion, Merge, Quick, Heap, ...
│   │   │   └── Graph/
│   │   ├── List/
│   │   │   ├── Queue.java          # Linked-list queue
│   │   │   ├── Stack.java
│   │   │   ├── LinkedList.java
│   │   │   ├── DoublyLinkedList.java
│   │   │   ├── Hash.java           # Separate chaining
│   │   │   └── Graph/
│   │   └── Tree/
│   │       ├── Tree.java           # Iterative BST methods
│   │       ├── TreeNode.java       # Recursive BST methods
│   │       ├── AvlTree.java
│   │       ├── BTree.java
│   │       ├── Stack.java          # Tree-local stack helper
│   │       └── Queue.java          # Tree-local queue helper
│   └── test/java/
│       ├── TestArrayQueue.java
│       ├── TestListQueue.java
│       ├── TestTree.java
│       ├── TestArrayHash.java
│       ├── TestListHash.java
│       ├── TestHeap.java
│       ├── TestDisjointSet.java
│       ├── TestSort.java
│       ├── TestArrayGraph.java
│       ├── TestListGraph.java
│       └── ...
├── libs/                           # Bundled JUnit 4 + Hamcrest
├── AGENTS.md                       # AI tutor instructions (Codex CLI / all agents)
├── CLAUDE.md                       # AI tutor instructions (Claude Code)
├── rules.txt                       # Exam rules
└── pom.xml
```

---

## Running Tests Manually

Run all tests for a topic:

```bash
mvn test -Dtest=TestTree
mvn test -Dtest=TestArrayQueue
mvn test -Dtest=TestListQueue
mvn test -Dtest=TestArrayHash
mvn test -Dtest=TestListHash
mvn test -Dtest=TestHeap
mvn test -Dtest=TestDisjointSet
mvn test -Dtest=TestSort
```

Run a specific test method:

```bash
mvn test -Dtest=TestTree#testBottomTwo
mvn test -Dtest=TestArrayQueue#testRotateQueue
```

---

## Recommended Study Workflow

1. **Pick a topic** from the midterm coverage table above.
2. **Open the corresponding implementation file** (e.g., `Tree/Tree.java`).
3. **Read the method stub** and the exam rules, then attempt an implementation on your own.
4. **Ask the AI** to check your work — describe what you tried and where you're stuck.
5. **Act on the hints**, re-run the tests, and iterate.
6. If you're stuck after three rounds of hints, move to a different question and return later. That's what the AI will tell you to do anyway.

> The goal is to leave every session having reasoned through the solution yourself. The AI is a mirror, not an answer key. -Batu Koray Masak
