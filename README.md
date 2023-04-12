## 🐥 🇧🇷 Canarim Instruct Dataset

<p align="center">
  <img width="250" alt="Camarim Logo" src="https://raw.githubusercontent.com/DominguesM/Canarim-Instruct-PTBR/main/assets/canarim.png">
</p>

<p align="center">
  <a href="https://huggingface.co/datasets/dominguesm/Canarim-Instruct-PTBR-Dataset">[🐱 HuggingFace]</a>
</p>

<hr>

## What's Canarim?

Canarim is a dataset with over 300,000 instructions in Portuguese, ranging from simple instructions like "Descreva os efeitos do aquecimento global" to more complex instructions like "Nesta tarefa, você precisa ser capaz de resumir uma determinada lista de pontos-chave" where additional context is provided.

## Why it's called Canarim?

Canarim is a dataset with over 300,000 instructions in Portuguese, ranging from simple instructions like "Canarim (is pronounced: kɑnɑrɪm) or canary is a bird very present in Brazilian daily life, living for up to 30 years. Every Brazilian at some point in their life has come across this bird, which is why I chose this name for my project.

"Canarim" is spoken in some regions of Brazil (mainly by grandparents), and it could be translated as "canáriozinho," which means "little canary" in English.

## Source Data

This dataset was created through translation and adaptation from the following sources:

* [**dominguesm/alpaca-data-pt-br**](https://huggingface.co/datasets/dominguesm/alpaca-data-pt-br) (*51759 rows*)
* [**cahya/instructions-pt**](https://huggingface.co/datasets/cahya/instructions-pt) (*57692 rows*)
* [**HuggingFaceH4/self_instruct**](https://huggingface.co/datasets/HuggingFaceH4/self_instruct) (*74350 rows*)
* [**HuggingFaceH4/helpful_instructions (self_instruct)**](https://huggingface.co/datasets/HuggingFaceH4/helpful_instructions/viewer/self_instruct/train) (*82612 rows*)
* [**HuggingFaceH4/helpful_instructions (super_natural_instructions)**](https://huggingface.co/datasets/HuggingFaceH4/helpful_instructions/viewer/super_natural_instructions/train) (*50000 rows*)

Totaling 316k lines in the training split and 1519 lines in the test split, all lines must contain an "instruction" and an "output", and may or may not also contain a "context".

There may be translation errors in the data.

## How to use

```python
!pip install datasets
from datasets import load_dataset

ds = load_dataset("dominguesm/Canarim-Instruct-PTBR-Dataset")
```

## Prompt

Below is the prompt template I am using with this dataset:

```python
def generate_prompt(instruction, input=None):
    if input:
        return f"""Abaixo está uma instrução que descreve uma tarefa, emparelhada com uma entrada que fornece mais contexto. Escreva uma resposta que conclua adequadamente a solicitação.
### Instruções:
{instruction}
### Entrada:
{input}
### Resposta:"""
    else:
        return f"""Abaixo está uma instrução que descreve uma tarefa. Escreva uma resposta que conclua adequadamente a solicitação.
### Instruções:
{instruction}
### Resposta:"""
```

## Examples of prompts

```json
{
    "instruction": "Sugira uma estratégia de marketing eficaz para um programa de TV.",
    "input": "",
    "output": "Uma estratégia de marketing eficaz para um programa de TV é criar um trailer de teaser a ser lançado antes da estréia do programa na televisão e outras plataformas digitais. O trailer de teaser deve ser curto, dinâmico e atraente, a fim de desencadear a curiosidade e o interesse nos espectadores. Ele também deve conter uma linha de tags convincente ou "gancho" que resume a premissa do programa. Além disso, criar uma hashtag associada ao programa de conteúdo da TV e pedir aos espectadores que se juntem à conversa nas mídias sociais."
}
```

```json
{
    "instruction": "Compare os dois assuntos a seguir",
    "input": "Inteligência Artificial e Machine Learning",
    "output": "Inteligência Artificial (IA) e Machine Learning (ML) são campos da ciência da computação que envolvem o desenvolvimento de máquinas inteligentes que podem aprender com dados e executar tarefas de forma autônoma. A IA se concentra no comportamento semelhante ao humano e envolve o desenvolvimento de algoritmos e estruturas de dados que permitem que as máquinas aprendam através do reconhecimento de padrões e do raciocínio lógico. A ML, por outro lado, é um subconjunto de IA que se concentra em ensinar computadores a otimizar tarefas com um certo grau de precisão."
}
```


```
@misc {dominguesm2023canarim,
    title        = { Canarim: An Instruction-Based LLM Training Data Set in Portuguese },
    author       = { {Maicon Domingues} },
    year         = 2023,
    url          = { https://huggingface.co/datasets/dominguesm/Canarim-Instruct-PTBR-Dataset },
}
```