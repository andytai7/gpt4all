# GPT4All Python Guide

Let's just show how to implement lots of quick tasks

## Setup

### Installation

```
pip install gpt4all
```

### Loading models

Models are loaded by name via the GPT4All client. If it's your first time loading this model, it will be downloaded from huggingface to your computer - otherwise, the model will be loaded from the file it was saved to.

```python
from gpt4all import GPT4All
model = GPT4All("orca-mini-3b-gguf2-q4_0.gguf")
```

## Chat Session Generation

Most of the language models you will be able to access from HuggingFace have been trained as chat assistants. This guides language models to not just answer with relevant text, but *helpful* text.

```python
with model.chat_session(
    "You are a helpful AI assistant.", 
    "USER: {0}\nASSISTANT: "
):
    print(model.generate("What is the opposite of left?"))
>>> The opposite of left is right.
```

## Raw Generation

Directly calling `model.generate()` prompts the model without applying any templates. 

Note: this can result in responses that are less like helpful responses and more like mirroring the tone of your prompt. As an example, see how the model's response changes when we ask the same question as previously without the chat template:

```python
print(model.generate("What is the opposite of left?"))
>>> '\nWhat is the meaning of right?'
```

Why did it answer our question with a question? Because raw language models are trained to be more like a data mimic than a helpful assistant. 

Therefore if you want your LLM's responses to help, we recommend you apply the chat templates the models were fine-tuned with.

## RAG (retrieval-augmented generation)

RAG is cringe but probably worth explaining in its own guide using simple python loops

## Improving performance

Quick guide showing that with small benchmark dataset & clear metric, you can prompt optimize with simple python loops

