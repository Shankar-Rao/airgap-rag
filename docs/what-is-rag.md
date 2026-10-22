---
layout: default
title: "Talking to Your Documents: What RAG Is and Why It Matters"
description: "A plain language explanation of Retrieval Augmented Generation (RAG): how it lets an AI answer questions from your own documents, with sources, and where it goes wrong."
permalink: /what-is-rag/
---

Finding one key detail across a pile of similar documents is slow, repetitive work that eats hours. What if you could just ask a question and get an answer, the way you would from a colleague who had read everything?

That’s what Retrieval Augmented Generation (RAG) makes possible. Many organisations hold documents that can’t be sent to a cloud service, so I’m particularly interested in doing this privately and offline. This post explains the idea in plain terms. The code and benchmarks follow in the next two posts.

### What is RAG?

Imagine handing a stack of documents to a colleague who'd read everything and saying, “Answer questions using only these.” RAG does the same thing with a Large Language Model (LLM). The model wasn’t trained on your contracts, policies or reports, so instead of guessing, it looks things up in them first and then writes the answer.

The name describes the two steps: **retrieval** (find the relevant passages) and **generation** (write an answer from them).

### Step 1: Retrieval

Before anyone asks a question, the system prepares your documents once:

- **Chunking**: Each document is split into small passages.
- **Embedding**: Each passage is converted into a list of numbers, called an embedding, that captures its _meaning_. Passages about similar things end up with similar numbers.
- **Indexing**: The passages are stored in a vector database along with where they came from, such as the file name and page number. This only needs repeating when you add new documents.

When you ask a question, it is converted the same way, and the system finds the passages whose meaning is closest to it.

This is different from keyword search. If you ask about the “termination notice period,” the system can find a paragraph about “ending the contract with 60 days’ written notice,” even though the words barely overlap.

### Step 2: Generation

The best-matching passages are handed to the LLM along with your question. The model reads them and writes an answer you can cite and check in seconds.

### An example

Suppose you ask: _“What’s the notice period in our supplier contract with Acme?”_

> The contract requires 60 days’ written notice to terminate. _(Source: Acme_Supply_Agreement.pdf, page 14)_

The citation is what makes this useful. You can check the answer against the original in seconds.

Documents → chunks → search by meaning → LLM → answer with source

### Where RAG goes wrong

RAG is far better than asking a bare chatbot, but it isn’t magic:

- **Retrieval can miss.** If the right passage isn’t found, the answer will be built on the wrong one.
- **The model can still misread or invent details**, even with the right text in front of it.
- **Messy documents hurt.** Scanned pages, odd layouts and badly extracted tables cause problems before the model sees anything.

That’s why good systems show their sources, and why you should measure performance on your own documents rather than take anyone’s word for it. That is exactly what the benchmarks in a later post are for.

### Why it’s worth it

- **Saves time**: Questions that took hours of reading take seconds.
- **Grounded in your documents**: Answers come from your material and can be traced back to it.
- **Scales**: It can handle many questions at once, at any hour.
- **Easy to update**: Add new documents, index them (usually quick), and the system can use them without retraining the model.

### What’s next

This is the first of three posts. Next, I’ll share the code, free, for running RAG entirely offline. After that come benchmarks, with the hardware, models and limitations spelled out.

### Author's note
I built and tested the offline systems described here. Benchmarks on multiple document types and model sizes follow in the next post.
