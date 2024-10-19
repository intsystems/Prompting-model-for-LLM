# Data Generation

Here we have collected our experiments with dataset generation.

### Mistral

В качестве основы взят датасет [bad-improved-prompt-pairs](https://huggingface.co/datasets/Jayveersinh-Raj/bad-improved-prompt-pairs). 

Для генерации через Mistral нужно зарегестрироваться на их сайте и выбрать La Plateforme -> Billing -> Free Plan.
.
> [!NOTE]
> Для этого понадобится номер телефона, на него придёт СМС.

Далее нужно сгенерировать API Key на соответствующей вкладке. По сути всё. Использовалась модель open-mixtral-8x22b, но проблем с подключением к mistral-large-2407 тоже не возникло. Всё равно я не стала рисковать, непонятно, насколько ограничен до неё доступ.

> [!NOTE]
> Mistal не разрешает обращаться к нему чаще 1 раза в секунду (мне пришлось поставить time.sleep(5), при меньшем значении падает). Плюс есть ограничение на число токенов в день и месяц (500 000  и 1 000 000 000). Их можно отслеживать в La Plateforme -> Usage / Limits.

Ноутбук с генерацией и моим промптом для более менее адекватных ответов: [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1w171xsVrK5yiPPmXFUuosp0Zbmph-9oH?usp=sharing)
Иногда Mistral генерит ответ на промпт вместе с улучшенным промптом. Иногда он генерит слишком длинный улучшенный промпт, поэтому я попросила его не делать так. Хотя возможно на запросы по написанию каких-то программ стоило оставить длинные оптимизированные промпты.
Иногда появляются вводные слова типа "Enhanced prompt:", "Rewritten Prompt:", "Enhance the prompt:" (хотя промпт улучшенный). Их придётся пока вручную чистить.

Пример генерации:

| bad_prompts | improved_prompts | Mistral_prompts |
| :--- | :--- | :--- |
| Write a program that calculates the area of a triangle. | Implement a Python program that takes the lengths of the sides of a triangle as inputs and calculates its area using Heron's formula | Enhanced prompt: Code a program to determine the area of any given triangle using a specific formula (e.g., base times height divided by 2). Please provide the solution in a programming language of your choice without including any examples of the response to the prompt. Keep the length of the prompt concise. |
| | | |
---
