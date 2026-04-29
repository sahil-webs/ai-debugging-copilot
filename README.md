# ai-debugging-copilot
AI tool that analyzes code, retrieves relevant context using RAG, and suggests bug fixes with explanations.

# AI Debugging Copilot

This project is a small attempt to make debugging less painful.

Instead of manually tracing errors or scanning files, the idea is to let an AI system:

* understand your code
* find relevant parts
* suggest possible fixes
* explain what went wrong

It’s not meant to replace developers — just to speed up the debugging loop.

---

## What it does

Given a piece of code (or a repo), the system:

* indexes the code using embeddings (RAG)
* retrieves only the relevant parts for a query
* sends context + query to an LLM
* returns:

  * possible bug
  * suggested fix
  * explanation

Example:

> "Why is this function returning None?"

→ retrieves related code
→ analyzes logic
→ suggests fix with reasoning

---

## Why I built this

While practicing coding and projects, I noticed:

* Debugging takes more time than writing code
* Most tools either:

  * give generic answers, or
  * don’t understand full context

So I wanted to build something that:

* uses **actual code context (RAG)**
* gives **focused debugging help**

---

## How it works (simple flow)

1. Code is split into chunks
2. Converted into embeddings
3. Stored in vector database
4. User asks a query
5. Relevant chunks are retrieved
6. LLM generates:

   * bug explanation
   * fix suggestion

---

## Tech stack

* Python
* FastAPI (backend)
* LangChain (RAG pipeline)
* ChromaDB (vector database)
* OpenAI API (LLM)

---

## Project structure

```id="2p4k7c"
ai-debugging-copilot/
│
├── app/
│   ├── main.py          # FastAPI entry point
│   ├── rag.py           # retrieval logic
│   ├── embeddings.py    # embedding setup
│   ├── llm.py           # LLM interaction
│   └── utils.py
│
├── data/                # code files / sample repo
├── requirements.txt
└── README.md
```

---

## How to run

```bash id="x3n9md"
git clone https://github.com/your-username/ai-debugging-copilot
cd ai-debugging-copilot

pip install -r requirements.txt
```

Set API key:

```bash id="s9k2df"
export OPENAI_API_KEY=your_key
```

Run server:

```bash id="j2k9fd"
uvicorn app.main:app --reload
```

---

## Example usage

```id="d7k3sd"
Query:
"Fix the bug in calculate_total()"

Response:
- identifies incorrect condition
- suggests corrected code
- explains why bug occurs
```

---

## Current limitations

* Works best on small to medium codebases
* Chunking is basic (can miss context)
* No real code execution/testing yet
* Depends heavily on prompt quality

---

## Future improvements

* Add multi-file reasoning
* Integrate unit test execution
* Improve chunking using AST
* Add simple UI
* GitHub repo integration

---

## Final note

This project is mainly for learning:

* how RAG works on code
* how LLMs behave with real context
* where they fail during debugging

Still a work in progress.

---

If you have suggestions or ideas, feel free to contribute.
