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

Ноутбук с генерацией и моим промптом для более менее адекватных ответов: [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1I-jj2riyarklCB1Bg_COto9EcQRtPbRX?usp=sharing)
Иногда Mistral генерит ответ на промпт вместе с улучшенным промптом. Иногда он генерит слишком длинный улучшенный промпт, поэтому я попросила его не делать так (не всегда помогает). Хотя возможно на запросы по написанию каких-то программ стоит оставить длинные оптимизированные промпты. Плюс я заметила, что в датасете для модели не используется I (только you, т.е. "Сделай", "Напиши" и т.д).
Иногда появляются вводные слова типа "Enhanced prompt:", "Rewritten Prompt:", "Enhance the prompt:" (хотя промпт улучшенный). Их придётся пока вручную чистить.
Ещё Mistral любит добавить эпитетов от себя.

Пример генерации:

| bad_prompts | improved_prompts | Mistral_prompts |
| :--- | :--- | :--- |
| Write a program that calculates the area of a triangle. | Implement a Python program that takes the lengths of the sides of a triangle as inputs and calculates its area using Heron's formula | Enhanced prompt: Code a program to determine the area of any given triangle using a specific formula (e.g., base times height divided by 2). Please provide the solution in a programming language of your choice without including any examples of the response to the prompt. Keep the length of the prompt concise. |
| I want to write a grpc sever and client in python | Implement a simple proto file, and the command to execute it in python for server and client. | I aim to develop a gRPC server and client application in Python. I need guidance on the steps and best practices for setting up the project, defining the service and messages in the .proto file, generating the Python code, implementing the server, and finally, creating the client to communicate with the server. I would appreciate advice on error handling, testing, and deploying the gRPC application. |
| You're a detective. What's the city like? | Imagine you are a detective in a noir film. Describe the city at night. | You're a seasoned detective in a bustling metropolis. Describe the unique characteristics and atmosphere of the city that shape your investigations. |
| What's hard about space travel? | Describe the challenges of space travel for astronauts. | Challenges of Space Travel: Explain the difficulties and obstacles. |
| Write a story about the Gold Rush. | Write a historical fiction story set during the Gold Rush. | Craft a narrative set during the historic Gold Rush era, detailing the challenges, triumphs, and transformations experienced by its participants. |

---
