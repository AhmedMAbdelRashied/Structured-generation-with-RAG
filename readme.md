# Structured generation with RAG
is a method that forces the LLM output to follow certain constraints, for instance to follow a specific pattern.

This has numerous use cases:

- ✅ Output a dictionary with specific keys
📏 Make sure the output will be longer than N characters
- ⚙️ More generally, force the output to follow a certain regex pattern for downtream processing.
- 💡 Highlight sources supporting the answer in Retrieval-Augmented-Generation (RAG)

In this notebook, we demonstrate specifically the last use case:

## Prompting the model
To get structured outputs from your model, you can simply prompt a powerful enough models with appropriate guidelines, and it should work directly… most of the time.

In this case, we want the RAG model to generate not only an answer, but also a confidence score and some source snippets. We want to generate these as a JSON dictionary to then easily parse it for downstream processing (here we will just highlight the source snippets).


# Constrained decoding
To force a JSON output, we’ll have to use constrained decoding where we force the LLM to only output tokens that conform to a set of rules called a grammar.

This grammar can be defined using Pydantic models, JSON schema, or regular expressions. The AI will then generate a response that conforms to the specified grammar.

Here for instance we follow[Pydantic types](https://docs.pydantic.dev/latest/api/types/)

