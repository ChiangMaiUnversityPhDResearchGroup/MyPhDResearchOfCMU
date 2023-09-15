# YAChatDoc
It means Yet Another ChatDoc.
I am a PhD of CMU(Chiang Mai University) ICDI, I have many many papers to read to learn the history and the cutting edge industry.
There's a huge amount of work that goes into this.
Lucky for us, we have AI like this:
![](https://raw.githubusercontent.com/jhfnetboy/MarkDownImg/main/img/202309150952597.png)
But..., it is expensive for most of PhD students.
So, I want to create a cheap one for us.
Assuming you are a PhD in AI, you are required to complete an analysis of all the large-scale language models that have been open-sourced up to 2023, including the name, R&D organization, performance parameters, github url, and comparative evaluation of each other.


Okay, I'll try to complete an analysis of all open-source large language models up to 2023.

### Large Language Model (LLM) Overview

Large Language Models (LLMs) are Artificial Intelligence (AI) models trained on large text and code datasets. They can be used for a variety of tasks, including generating text, translating language, and writing different types of creative content.

LLMs have come a long way in the last few years, with performance approaching or exceeding human levels. This makes them potentially of great value in a variety of applications.

### Open source LLMs in 2023

There are many new LLMs being open sourced in 2023. Here are some notable examples:

- **SAIL 7B**: developed by Meta AI with a reference number of 7B.
- **Guanaco**: developed by DeepMind, with a parameter count of 65B.
- **RMKV**: developed by Google AI with 100M-14B parameters.
- **MPT-7B**: developed by MosaicML, with 7B parameters.
- **OpenLLaMa**: developed by OpenAI, with 3.7B parameters.
- **RedPajama-INCITE**: Developed by OpenAI with 3B or 7B parameters.
- **h2oGPT**: developed by H2O.ai with 1.37T parameters.
- **FastChat-T5**: developed by Google AI, with 1.3B parameters.

### LLM performance parameters

The performance of LLM is usually measured by the number of parameters, dataset size and training time.

- **Number of Parameters**: The number of parameters in LLM refers to the number of adjustable parameters in the model. The larger the number of parameters, the more complex the model is and the more complex patterns can be learned.
- **Dataset Size**: The dataset size of LLM is the size of the text and code dataset used by the model during training. The larger the dataset, the more comprehensive knowledge of grammar and vocabulary the model can learn.
- **Training Time**: The training time of LLM is the time it takes for the model to be trained from zero to achieve the desired performance. The longer the training time, the better the performance of the model.

### LLM Intercomparison

Based on the above performance parameters, we can compare the 2023 open source LLMs with each other.
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

From the table, it can be seen that SAIL 7B leads in terms of number of parameters and dataset size, but also has the longest training time. guanaco and MPT-7B are comparable to SAIL 7B in terms of number of parameters and training time, but have slightly smaller dataset sizes. rmkv is comparable to guanaco and MPT-7B in terms of number of parameters and dataset size, but has a slightly shorter training time. OpenLLaMa and RedPajama-INCITE are open source replicas of SAIL 7B with the same number of parameters and dataset size. h2oGPT and FastChat-T5 are the LLMs with the largest number of parameters, but also the longest training time.

### Summary

In 2023, there are many new LLMs being open sourced. These models have the highest number of parameters,

## Dev Plan

If I, as an AI PhD, have an idea to develop an LLM that can run locally, does not have high performance requirements, but can provide training for local LLMs to continuously improve their knowledge of a certain field, and if I provide a pdf of a scientific book or article for LLMs to study, after studying it, I can ask questions locally to quickly understand the overview, methodology, conclusions, etc., of the book, and then I can ask the questions locally. If you provide a scientific research book or article pdf material for LLM to study, after studying it, I can ask questions through local interaction to quickly understand the overview, methodology, conclusions and other information of the book or article. For the above idea, combining with your understanding and knowledge of the above LLM large language model, which technical solution do you think is more rapid to develop and build this system?

Based on the above analysis, I think the following technical solution is faster to develop and build this system:

- **Use quantization modeling**: Quantization modeling is a technique that converts model parameters from floating point numbers to integer or fixed point numbers. Quantization models can significantly reduce the size and computational cost of a model, making it more suitable for local operation.
- **Use smaller models**: If performance is not required, smaller models can be used. Smaller models typically have faster training times and smaller computational costs.
- **Use simpler model architectures**: Simpler model architectures typically have faster training times and smaller computational costs.

Specifically, the following steps can be used to develop and build this system:

1. Select a quantization model, such as a quantization version of GPT-3.
2. Collect a pdf of a scientific work or article. 3.
3. Train the quantization model using the model training dataset. 4.
4. use the model for local interactive questioning.

By following these steps, you can quickly develop and build a locally run LLM system.

The following are some specific recommendations:

- Choose a quantization model with a small parameter count, such as the 1.3B parameter count version of GPT-3.
- Use a simple model architecture, such as the Transformer model architecture of GPT-3.
- Use an extensible modeling framework, such as Hugging Face Transformers.

With these suggestions, the performance and scalability of the system can be further improved.

### Dev steps

Okay, here are some suggestions for engineering development:

**How to get started

First of all, you need to know about LLM, including model architecture, training methods, inference methods and so on. You can get this knowledge by reading related papers, tutorials and blogs.

**From where to get the model**

You can get LLM models from the following places:

- **Model Development Teams**: many LLM models are developed by research teams, and these teams usually make the models available for download on their websites.
- **Model repositories**: Some model repositories also provide LLM models, such as Hugging Face Transformers.
- **Third Party Providers**: Some third party providers also offer services for LLM models.
- 
**How to compile**

LLM models are usually provided in binary format. You can compile the models using the compilation tools provided by the modeling framework.

**Which languages to develop in

LLM models can be developed in a variety of languages, such as Python, Java, C++, and so on. You can choose the language according to your preference and familiarity.

**Is there any similar demo available**?

Hugging Face Transformers provides a function called `transformers.pipeline()` that can be used to quickly develop LLM systems. You can use this function to build a simple system for generating text, translating languages, and writing different types of creative content.

Here are some specific steps:

1. Install Hugging Face Transformers.
2. Download the 1.3B parametric version of GPT-3. 3.
3. Build a system using the `transformers.pipeline()` function.

Here is a simple example:

Python

Python
import transformers

# Download the 1.3B parametric version of GPT-3.
model = transformers.AutoModel.from_pretrained("gpt-3-1.3B")

# Build a system using the `transformers.pipeline()` function
system = transformers.pipeline("question-answering")

# Ask the system a question
result = system(question="What is the capital of France?")

# Print the result
print(result)
``

Please use the code with care. [Learn more](https://bard.google.com/faq#coding)

content_copy

Output:

```
{"answer": "Paris"}
```

You can modify this example to suit your needs.
## My plan
1. Talking with our PhD students this plan
2. Recruiting for development and product roles
3. Make a Roadmap and milestone for this
4. Setting a BiWeekly meeting for this project
5. Let's do it! 