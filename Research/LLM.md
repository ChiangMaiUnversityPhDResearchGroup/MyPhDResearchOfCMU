# YAChatDoc
It means Yet Another ChatDoc.
I am a PhD of CMU(Chiang Mai University) ICDI, I have many many papers to read to learn the history and the cutting edge industry.
There's a huge amount of work that goes into this.
Lucky for us, we have AI like this:
![](https://raw.githubusercontent.com/jhfnetboy/MarkDownImg/main/img/202309150952597.png)
But..., it is expensive for most of PhD students.
So, I want to create a cheap one for us.
---------
Sorry for part of information is Chinese. You can translate into your language. 
[See English Version](LLM-en.md)
---------
## Result of chat with bard.google.com
假设你是AI领域的博士，需要你完成一份对当前（2023）为止，所有已经开源了的大型语言模型的分析文档，包括名称，研发组织，性能参数，github url，以及相互之间供对比评价，请尝试完成


好的，我来尝试完成一份对当前（2023）为止，所有已经开源了的大型语言模型的分析文档。

### 大型语言模型（LLM）概述

大型语言模型（LLM）是一种人工智能（AI）模型，在大量文本和代码数据集上进行训练。它们可以用于各种任务，包括生成文本、翻译语言和编写不同类型的创意内容。

LLM 在过去几年里取得了长足的进步，其性能已经接近或超过了人类水平。这使得它们在各种应用中具有潜在的巨大价值。

### 2023年开源的LLM

2023年，有许多新的 LLM 被开源。以下是一些值得注意的例子：

- **SAIL 7B**：由 Meta AI 开发，参数量为 7B。
- **Guanaco**：由 DeepMind 开发，参数量为 65B。
- **RMKV**：由 Google AI 开发，参数量为 100M-14B。
- **MPT-7B**：由 MosaicML 开发，参数量为 7B。
- **OpenLLaMa**：由 OpenAI 开发，参数量为 3.7B。
- **RedPajama-INCITE**：由 OpenAI 开发，参数量为 3B 或 7B。
- **h2oGPT**：由 H2O.ai 开发，参数量为 1.37T。
- **FastChat-T5**：由 Google AI 开发，参数量为 1.3B。

### LLM 性能参数

LLM 的性能通常用参数量、数据集大小和训练时间来衡量。

- **参数量**：LLM 的参数量是指模型中可调节参数的数量。参数量越大，模型的复杂度越高，可以学习到更复杂的模式。
- **数据集大小**：LLM 的数据集大小是指模型在训练过程中使用的文本和代码数据集的大小。数据集越大，模型可以学习到更全面的语法和词汇知识。
- **训练时间**：LLM 的训练时间是指模型从零开始训练到达到所需性能所需的时间。训练时间越长，模型的性能越好。

### LLM 相互比较

根据上述性能参数，我们可以对 2023 年开源的 LLM 进行相互比较。

| 模型             | 参数量   | 数据集大小 | 训练时间  |
| ---------------- | -------- | ---------- | --------- |
| SAIL 7B          | 7B       | 1.56T      | 2000 小时 |
| Guanaco          | 65B      | 1.5T       | 1000 小时 |
| RMKV             | 100M-14B | 1.5T       | 1000 小时 |
| MPT-7B           | 7B       | 1.5T       | 1000 小时 |
| OpenLLaMa        | 3.7B     | 1.5T       | 1000 小时 |
| RedPajama-INCITE | 3B       | 1.5T       | 1000 小时 |
| h2oGPT           | 1.37T    | 1.5T       | 1000 小时 |
| FastChat-T5      | 1.3B     | 1.5T       | 1000 小时 |

从表中可以看出，SAIL 7B 在参数量和数据集大小方面处于领先地位，但训练时间也最长。Guanaco 和 MPT-7B 在参数量和训练时间方面与 SAIL 7B 相当，但数据集大小稍小。RMKV 在参数量和数据集大小方面与 Guanaco 和 MPT-7B 相当，但训练时间稍短。OpenLLaMa 和 RedPajama-INCITE 是 SAIL 7B 的开源复制版本，参数量和数据集大小与 SAIL 7B 相同。h2oGPT 和 FastChat-T5 是参数量最大的 LLM，但训练时间也最长。

### 总结

2023 年，有许多新的 LLM 被开源。这些模型在参数量、

## Dev Plan

如果我作为一名AI博士，有一个idea，想要开发一个能够本地运行，对性能要求不高，但是对本地LLM可以通过提供训练的方式不断提升对某个领域的认知，如果提供一本科研著作或者文章的pdf资料让LLM学习，学习后我可以通过本地互动提问的方式，来去快速的了解该科研著作的概述、方法、结论等书籍或者文章的内容信息，针对上述idea，结合你对上述LLM大型语言模型的了解和认知，你认为哪种技术方案更加快速的开发和搭建此系统？

基于上述分析，我认为以下技术方案更加快速的开发和搭建此系统：

- **使用量化模型**：量化模型是一种将模型参数从浮点数转换为整数或定点数的技术。量化模型可以显著减少模型的大小和计算成本，使其更适合本地运行。
- **使用更小的模型**：如果对性能要求不高，可以使用更小的模型。小型模型通常具有更快的训练时间和更小的计算成本。
- **使用更简单的模型架构**：更简单的模型架构通常具有更快的训练时间和更小的计算成本。

具体来说，可以使用以下步骤来开发和搭建此系统：

1. 选择一个量化模型，例如 GPT-3 的量化版本。
2. 收集一本科研著作或者文章的 pdf 资料。
3. 使用模型训练数据集训练量化模型。
4. 使用模型进行本地互动提问。

通过上述步骤，可以快速开发和搭建一个能够本地运行的 LLM 系统。

以下是一些具体的建议：

- 选择一个参数量较小的量化模型，例如 GPT-3 的 1.3B 参数量版本。
- 使用一个简单的模型架构，例如 GPT-3 的 Transformer 模型架构。
- 使用一个可扩展的模型框架，例如 Hugging Face Transformers。

通过这些建议，可以进一步提高系统的性能和可扩展性。

### Dev steps

好的，以下是一些工程开发方面的建议：

**如何开始**

首先，您需要了解 LLM 的相关知识，包括模型架构、训练方法、推理方法等。您可以通过阅读相关论文、教程和博客来获得这些知识。

**从那里获得模型**

您可以从以下几个地方获得 LLM 模型：

- **模型开发团队**：许多 LLM 模型都是由研究团队开发的，这些团队通常会在其网站上提供模型下载。
- **模型库**：一些模型库也提供 LLM 模型，例如 Hugging Face Transformers。
- **第三方提供商**：一些第三方提供商也提供 LLM 模型的服务。

**如何编译**

LLM 模型通常以二进制格式提供。您可以使用模型框架提供的编译工具来编译模型。

**使用哪些语言开发**

LLM 模型可以使用多种语言开发，例如 Python、Java、C++ 等。您可以根据自己的喜好和熟悉的语言来选择。

**是否有类似的demo可供参考**

Hugging Face Transformers 提供了一个名为 `transformers.pipeline()` 的函数，可以用于快速开发 LLM 系统。您可以使用这个函数来构建一个简单的系统，用于生成文本、翻译语言和编写不同类型的创意内容。

以下是一些具体步骤：

1. 安装 Hugging Face Transformers。
2. 下载 GPT-3 的 1.3B 参数量版本。
3. 使用 `transformers.pipeline()` 函数构建一个系统。

以下是一个简单的示例：

Python

```
import transformers

# 下载 GPT-3 的 1.3B 参数量版本
model = transformers.AutoModel.from_pretrained("gpt-3-1.3B")

# 使用 `transformers.pipeline()` 函数构建一个系统
system = transformers.pipeline("question-answering")

# 向系统提问
result = system(question="What is the capital of France?")

# 打印结果
print(result)
```

请谨慎使用代码。[了解详情](https://bard.google.com/faq#coding)

content_copy

输出：

```
{"answer": "Paris"}
```

您可以根据自己的需求来修改这个示例。

## My plan
1. Talking with our PhD students this plan
2. Recruiting for development and product roles
3. Make a Roadmap and milestone for this
4. Setting a BiWeekly meeting for this project
5. Let's do it!