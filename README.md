# Offline RAG

Ask questions of your own documents and get answers with sources, running
entirely on your own machine. No cloud services, and your documents never
leave your hardware.

> **Status: early.** The explainer is published. The code and benchmarks
> are coming, in that order.

## What is this?

Retrieval Augmented Generation (RAG) lets a language model answer questions
using your documents instead of guessing. This project is a free, open
implementation designed to run fully offline, for people whose documents
can't be sent to a third-party API.

New to RAG? Start with the plain-language explainer:
**[Talking to Your Documents: What RAG Is and Why It Matters](https://shankar-rao.github.io/airgap-rag/what-is-rag/)**

## Roadmap

- [x] Explainer post: what RAG is, and where it goes wrong
- [ ] Code: a working offline pipeline with a quickstart
- [ ] Benchmarks: retrieval and answer quality, with hardware, models,
      baselines and limitations stated openly

## What to expect

- The code will be free to use under the Apache 2.0 license.
- Benchmarks will report failures as well as successes. If a published
  result turns out to be wrong, it will be corrected in the open.
- Questions and bug reports about the code will go in
  [Issues](../../issues) once the code is released.

## License

Licensed under the [Apache License 2.0](LICENSE).
