# LinkReview

- Here we have collect info about all the works that may be useful for writing our paper

> [!NOTE]
> This review table will be updated, so it is not a final version

| Title | Year | Authors | Paper | Code | Summary |
| :--- | ---: | :--- | :--- | :--- | :--- |
| LLM-Informed Discrete Prompt Optimization | 2024 | Zeeshan Memon | [paper](https://openreview.net/pdf?id=d0jQuZe6k0) | [GitHub](https://www.youtube.com/watch?v=MuRa3tlyzq8) | Это работа является ключевой для нашего исследование. В ней авторы разбивают обучение prompt'ов на 2 части: первая часть общая для всех LLM, в ней подразумевается наличие датасета с простыми prompt'ами и улучшенными, чтобы легкий Backbone затюнился лучше сэмплировать хорошие подсказки. Вторая часть обучения проводится для каждой LLM отдельно, в ней MLP и HEAD дообучаются для конкретной LLM для генерации ключевых слов. Авторы утверждают, что у каждой LLM есть набор ключевых слов, использование которых может существенно улучшить prompt'ы и, соответственно, ответы LLM. |
| Model-Agnostic Meta-Learning for Fast Adaptation of Deep Networks | 2017 | Chelsea Finn | [paper](https://proceedings.mlr.press/v70/finn17a/finn17a.pdf) | [GitHub]() | [Simple explaination](https://interactive-maml.github.io/maml.html) TODO |
| Hard Prompts Made Easy: Gradient-Based Discrete Optimization for Prompt Tuning and Discovery | 2023 | Yuxin Wen, Neel Jain, John Kirchenbauer | [paper](https://proceedings.neurips.cc/paper_files/paper/2023/file/a00548031e4647b13042c97c922fadf1-Paper-Conference.pdf) | [GitHub](https://github.com/YuxinWenRick/hard-prompts-made-easy) | Learning hard prompts for image generation using continuous optimization. The scheme builds on existing gradient reprojection schemes for optimizing text. Берут непрерывные промпты и на каждом шагу проецируют на дискретное пространство, затем оптимизируют градиентым спуском как непрерывные. |
| How Hard Can It Prompt? Adventures in Cross-model Prompt Transferability | 2024 | Lola Solovyeva | [paper](https://essay.utwente.nl/103206/1/Solovyeva_MA_EEMCS.pdf) | [GitHub]() | Discretizing soft prompts by leveraging cosine similarity between the embeddings of soft and hard tokens. Algorithm designed to identify a set of hard tokens using gradients obtained through the tuning of soft prompts. Testing the transferability of the derived hard prompts between different models. Написано примерно то же, что и в предыдущей статье, но в виде более подробной книжки с усложнением алгоритма из статьи выше. |
| Dynamic Prompting: A Unified Framework for Prompt Tuning | 2023 | Xianjun Yang | [paper](https://arxiv.org/pdf/2303.02909) | [GitHub](https://interactive-maml.github.io/maml.html) | TODO |
| Automatic Prompt Optimization with “Gradient Descent” and Beam Search | 2023 | R Pryzant, D Iter | [paper](https://aclanthology.org/2023.emnlp-main.494.pdf) | [GitHub]() | TODO |
| Differentiable Prompt Makes Pre-trained Language Models Better Few-shot Learners | 2022 | Ningyu Zhang Luoqiu Li | [paper](https://arxiv.org/pdf/2108.13161) | [GitHub]() | TODO |
