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

### Open Ai, gpt-4o
Подобные эксперименты были проведены с моделью gpt-4o от open ai. gpt-4o обладает великолепными обобщающими способностями, поэтому при просьбах генерации, если не упоминать, что инструкция должна быть короткая, то она генерирует детальный план по шагам, который по сути уже почти является решением поставленной задачи, поэтому в инструкции были добавлены слова о том, что инструкции должны быть простые и не слишком длинные. Ноутбук с генерацией промптов с помощью gpt-4o-mini [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1bxfI3a-jtnWyS4z9KyY08H261fqB1XST?usp=sharing)

Пример инструкции, если просить выдать лучший промпт, не ставя ограничения на его длину и сложность:
Create a Python program that performs the following tasks: Takes three numerical inputs from the user, representing the lengths of the sides of a triangle. Validates that the inputs form a valid triangle using the triangle inequality theorem. If the inputs are valid, calculates the area of the triangle using Heron's formula. Outputs the area of the triangle with an appropriate message. Heron's formula for the area (A) of a triangle with side lengths (a), (b), and (c) is: $[ s = \frac{a + b + c}{2} ] [ A = \sqrt{s(s - a)(s - b)(s - c)} ] $. Ensure the program includes appropriate error handling for invalid inputs (e.g., non-numeric values or values that do not form a valid triangle). 

Пример инструкции, если просить выдать лучший промпт, ставя ограничения на его длину и сложность: 
Please write a Python program that calculates the area of a triangle. The program should prompt the user to input the lengths of the triangle's base and height, and then it should compute and display the area using the Heron's formula. Ensure the program includes error handling for invalid inputs and provides clear instructions to the user.


В таблице ниже приведены примеры генерации. 


Пример генерации:


| bad_prompts | improved_prompts | Mistral_prompts | gpt-4o_prompts |
| :--- | :--- | :--- | :--- |
| Write a program that calculates the area of a triangle. | Implement a Python program that takes the lengths of the sides of a triangle as inputs and calculates its area using Heron's formula | Enhanced prompt: Code a program to determine the area of any given triangle using a specific formula (e.g., base times height divided by 2). Please provide the solution in a programming language of your choice without including any examples of the response to the prompt. Keep the length of the prompt concise. | Please write a Python program that calculates the area of a triangle. The program should prompt the user to input the lengths of the triangle's base and height, and then it should compute and display the area using the Heron's formula. Ensure the program includes error handling for invalid inputs and provides clear instructions to the user.|
| I want to write a grpc sever and client in python | Implement a simple proto file, and the command to execute it in python for server and client. | I aim to develop a gRPC server and client application in Python. I need guidance on the steps and best practices for setting up the project, defining the service and messages in the .proto file, generating the Python code, implementing the server, and finally, creating the client to communicate with the server. I would appreciate advice on error handling, testing, and deploying the gRPC application. | Develop a Python application that includes both a gRPC server and client. The tasks should be as follows: 1. Define a simple .proto file that specifies a gRPC service with at least one RPC method. For example, a method that takes a name as input and returns a greeting message. <br> 2. Provide the necessary commands to compile the .proto file using protoc to generate Python code for both the server and client. <br> 3. Implement the gRPC server in Python: Load the generated server-side code. Implement the service defined in the .proto file. Start the server and make it listen on a specified port. <br> 4. Implement the gRPC client in Python: Load the generated client-side code. Create a client that connects to the server. Call the RPC method defined in the .proto file and print the response. 5. Include error handling to manage common issues such as connection failures and invalid inputs. <br> 6. Provide detailed instructions on how to run both the server and client, including the installation of necessary dependencies. Example .proto file content:  <br> ``` syntax = "proto3"; service Greeter {  rpc SayHello (HelloRequest) returns (HelloReply);  }; message HelloRequest {  string name = 1;  }; message HelloReply {  string message = 1;  }; ``` <br> Ensure that the instructions are clear and easy to follow, and that the provided code is well-documented.|
| You're a detective. What's the city like? | Imagine you are a detective in a noir film. Describe the city at night. | You're a seasoned detective in a bustling metropolis. Describe the unique characteristics and atmosphere of the city that shape your investigations. | Imagine you are a seasoned detective in a classic noir film. Your trench coat is damp from the incessant drizzle, and your fedora casts a shadow over your eyes. Describe the city at night in vivid detail, capturing the atmosphere, sounds, and sights. Consider elements such as: <br> The dimly lit streets and flickering neon signs <br> The distant hum of city life mixed with the occasional siren <br> The silhouettes of shadowy figures moving through narrow alleys <br> The interplay of light and shadow, creating a sense of mystery and tension <br> The smells of rain-soaked pavement and distant cigarette smoke <br> The overall mood and feeling of the city, reflecting its hidden dangers and secrets <br> Use rich, evocative language to create an immersive scene that transports the reader into the heart of a noir-inspired urban landscape.|
| What's hard about space travel? | Describe the challenges of space travel for astronauts. | Challenges of Space Travel: Explain the difficulties and obstacles. | Describe the key challenges astronauts face during space travel. Cover the following aspects: <br>  1. Physical challenges (e.g., effects of microgravity, radiation exposure) <br>  2. Psychological challenges (e.g., isolation, confinement) <br>  3. Technical challenges (e.g., spacecraft maintenance, life support systems) <br>  4. Environmental challenges (e.g., extreme temperatures, space debris) <br> Use clear and concise language to explain these challenges.
| Write a story about the Gold Rush. | Write a historical fiction story set during the Gold Rush. | Craft a narrative set during the historic Gold Rush era, detailing the challenges, triumphs, and transformations experienced by its participants. | Write a historical fiction story set during the Gold Rush. Focus on a prospector's journey, the challenges they face, and the people they encounter. Include vivid descriptions and authentic details to bring the era to life. |

### Promt Optimizer
Имплементированный оптимизатор подсказок, позволяет автоматически генерировать оптимизированные подсказки для LLM (можно выбрать модель из огромного списка): [prompt_optimizer](https://app.hamming.ai/prompt-optimizer). 

> [!NOTE]
> Исходный код не доступен. Можно использовать для ручной генерации небольшого датасета.

### AutoPromt Optimizer
По всей видимости, статья [Automatic Prompt Optimization with "Gradient Descent" and Beam Search](https://arxiv.org/abs/2305.03495) - передовой край нашей науки по созданию универсальных помптов. Для оптимизации промптов авторы используют алгоритм "Prompt Optimization with Textual Gradients" (ProTeGi): формируются «градиенты» естественного языка, которые критикуют текущую подсказку (указывают в направлении возрастания ошибки).

Этот алгоритм реализован во фреймворке: [AutoPromt](https://github.com/Eladlev/AutoPrompt?tab=readme-ov-file).

> [!NOTE]
> Чтобы воспользоваться фреймворком необходимо иметь OpenAI API key. Но аккаунт на [OpenAI](https://openai.com/index/openai-api/) нельзя зарегистрировать на российский номер телефона.

### Black-Box Prompt Optimization (BPO)
Дугая интересная статья о создании оптимальных универсальных промптов: [Black-Box Prompt Optimization: Aligning Large Language Models without Model Training](https://arxiv.org/abs/2311.04155). Модель BPO пытается "подогнать" промпт под предпочтения человека, тем самым создавая оптимальные промпты. А именно, модель обучается на триплетах $(X_{user}, Y_{good}, Y_{bad})$, где $X_{user}$ - промпт созданный человеком, $Y_{good}$ - хороший ответ на запрос с точки зрения человека, $Y_{good}$ - плохой ответ на запрос с точки зрения человека; на выход модель выдает $X_{opt}$ - оптимальную версию помпта.

Этот алгоритм реализован во фреймворке: [BPO](https://github.com/thu-coai/BPO/tree/main).

Авторы самостоятельно сгенерировали датасет из 14,395 оптимальных промптов на основании своего алгоритма: [BPOdataset](https://huggingface.co/datasets/THUDM/BPO).

> [!NOTE]
> Чтобы воспользоваться фреймворком необходимо иметь OpenAI API key. Но аккаунт на [OpenAI](https://openai.com/index/openai-api/) нельзя зарегистрировать на российский номер телефона.







---
