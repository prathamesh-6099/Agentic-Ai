# LangGraph Learning Projects

This repository is a set of hands-on LangGraph learning examples. Each script explores a different workflow pattern, from simple sequential pipelines to conditional routing, human-in-the-loop review, tool use, and parallel analysis. The main idea of the repo is to understand how LangGraph controls state, edges, routing, and model calls in practical projects.

## What’s Inside

- `app.py` - a Streamlit-based college assistant that classifies questions and routes them to academic RAG, fee RAG, or direct LLM answers.
- `conditional_Rag.py` - the console version of the same conditional RAG workflow.
- `humanintheloop.py` - a LinkedIn post generator that pauses for human approval or feedback and loops until approved or a retry limit is reached.
- `iterative_tools.py` - a tool-using content generator that can search the web, then rewrites and reviews the draft in iterations.
- `parallel_reducers.py` - a fan-out workflow that runs multiple safety checks in parallel and merges the results into one state object.
- `sequential_base.py` - a simple editor -> scriptwriter -> translator pipeline for learning the basics of sequential graphs.
- `states.py` - notes and examples for different state definition styles in LangGraph.
- `academics_handbook.pdf` and `fee_structure.pdf` - the source documents used by the RAG examples.

## Learning Goals

This repo is useful if you want to understand:

- how to define graph state with `TypedDict`
- how to connect nodes with `START`, `END`, and conditional edges
- how to route requests based on classification
- how to build retrieval-augmented generation with PDF documents
- how to use memory and interrupt/resume patterns for human review
- how to run multiple branches in parallel and merge their outputs
- how to combine LangGraph with Streamlit for an interactive app

## Project Structure

```text
LangGraph/
├── app.py
├── conditional_Rag.py
├── humanintheloop.py
├── iterative_tools.py
├── parallel_reducers.py
├── sequential_base.py
├── states.py
├── academics_handbook.pdf
├── fee_structure.pdf
├── requirements.txt
└── README.md
```

## Setup

1. Create and activate a Python environment.
2. Install the dependencies:

```bash
pip install -r requirements.txt
```

3. Add your API keys to a `.env` file in the project root.

## Required Environment Variables

Depending on which script you run, you may need some or all of these keys:

- `GROQ_API_KEY` for `ChatGroq`
- `GOOGLE_API_KEY` for `ChatGoogleGenerativeAI`
- `TAVILY_API_KEY` for web search in `iterative_tools.py`

## How To Run

Run any example directly with Python:

```bash
python sequential_base.py
python conditional_Rag.py
python humanintheloop.py
python iterative_tools.py
python parallel_reducers.py
```

Run the Streamlit app:

```bash
streamlit run app.py
```

## Notes About The Streamlit App

The main app is a college assistant that asks the user to choose a programme once at the start of the chat. It then:

- classifies the question as academic, fee-related, or general
- retrieves context from the correct PDF when needed
- uses the selected programme to personalize the answer
- keeps chat history in Streamlit session state

Make sure `academics_handbook.pdf` and `fee_structure.pdf` stay in the same folder as `app.py`, because the app loads them directly from the project root.

## Why I Built This

This repository is mainly for learning. Each file demonstrates one workflow pattern in isolation so it is easier to understand how LangGraph behaves before combining everything into a larger agent or application.

