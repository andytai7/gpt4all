# GPT4All Python

## Installation

To get started, pip-install the `gpt4all` package into your python environment.

```bash
pip install gpt4all
```

We recommend installing `gpt4all` into its own virtual environment using `venv` or `conda`

## Loading models

Models are loaded by name via the GPT4All client. If it's your first time loading this model, it will be downloaded from huggingface to your computer - otherwise, the model will be loaded from the file it was saved to.

```python
from gpt4all import GPT4All
model = GPT4All("orca-mini-3b-gguf2-q4_0.gguf")
# call with model.generate()
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

## Embedding

In addition to language models, you can use the `gpt4all` package to load an embedding model.

```python
from gpt4all import Embed4All
text_embedder = Embed4All("orca-mini-3b-gguf2-q4_0.gguf")
print(text_embedder.embed("plug in a string to embed it"))
>>> [-0.006244505289942026, 0.03100959025323391, ..., 0.0896347388625145]
```