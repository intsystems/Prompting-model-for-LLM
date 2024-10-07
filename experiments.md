# Experiments

- Here we have collected information about the experiments carried out during the work on the paper

| Name | Description | Model | Dataset | Paper | Code | Status | Summary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Base | Model from the first paper | Model to generate fine-tune dataset: ChatGPT-3.5-Turbo API<br>Prompter model: [Microsoft Phi-2](https://huggingface.co/microsoft/phi-2)<br>Models for evaluation: Gemma7B, Vicuna7B, Llama3-8B, Qwen1.5-14B, Mistral8X7B, ChatGPT3.5 | [dataset](https://huggingface.co/datasets/teknium/GPTeacher-General-Instruct) | [paper](https://openreview.net/pdf?id=d0jQuZe6k0) | TODO | First attempts | Запущен Microsoft Phi-2 и ChatGPT3.5 API для генерации (платный). Теперь вопрос в том, как генерировать датасет с его помощью. |
| Dataset Generation | Выглядит как полноценный фреймворк для обучения промптов, есть модуль для генерации датасета. | [OpenPrompt](https://github.com/thunlp/OpenPrompt) | [paper]([https://openreview.net/pdf?id=d0jQuZe6k0](https://arxiv.org/pdf/2111.01998)) | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1w171xsVrK5yiPPmXFUuosp0Zbmph-9oH?usp=sharing)<br>[Tutorial](https://github.com/thunlp/OpenPrompt/tree/main/tutorial) | First attempts | Библиотека устанавливается через pip. Нужна верия transformers <= 4.27.1 |
