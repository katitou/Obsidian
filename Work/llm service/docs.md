- [[#FastAPI|FastAPI]]
- [[#Milvus|Milvus]]
- [[#GraphRAG|GraphRAG]]
- [[#OpenAI API (контракт взаимодействия FastAPI ↔ LLM)|OpenAI API (контракт взаимодействия FastAPI ↔ LLM)]]
- [[#LLM (промпт, настройка формата ответа)|LLM (промпт, настройка формата ответа)]]
- [[#Redis|Redis]]
- [[#Финальная интеграция|Финальная интеграция]]


## FastAPI

**Задача**: 

**Ресурсы**:
- **Официальная документация FastAPI** → https://fastapi.tiangolo.com/
    - ["First Steps" ](https://fastapi.tiangolo.com/tutorial/first-steps/)
    - ["Request Handling"](https://fastapi.tiangolo.com/tutorial/body/#request-body-path-query-parameters)
    - ["Background Tasks"](https://fastapi.tiangolo.com/tutorial/background-tasks/)
    - ["Dependencies"](https://fastapi.tiangolo.com/tutorial/dependencies/)
- **Статья на Habr**: 
	1. [Построение базы знаний компании и поиска документов на LLM и RAG](https://habr.com/ru/companies/raft/articles/863888/)

- **Работа с внешними API (requests, async)** 
	1. [Параллелизм и асинхрон](https://fastapi.tiangolo.com/async/)


🛠 **Применение**:
1. Поднять FastAPI-сервер и создать базовые эндпойнты.
2. Настроить асинхронные вызовы к Milvus и OpenAI API.
3. Подключить Redis для кэширования.



## Milvus

**Задача**: реализовать хранение и быстрый поиск

**Полезные ресурсы**:
- **Официальная документация Milvus** → https://milvus.io/docs/
    - [Quickstart](https://milvus.io/docs/quickstart.md)
    - [Indexing](https://milvus.io/docs/ru/index.md?tab=floating)
    - [Build an Index](https://milvus.io/docs/v2.0.x/build_index.md)
    - [Search](https://milvus.io/docs/multi-vector-search.md)
    - [Collection](https://milvus.io/docs/manage-collections.md)
    - [Collection Schema](https://milvus.io/docs/schema.md)
    
- **Пример интеграции с FastAPI** 
	- https://github.com/stephen37/Milvus_demo/tree/main/langchain_demos/langserve_demos
	- https://github.com/stephen37/Milvus_demo/tree/main/llama_index_demos

🛠 **Применение**:
1. Поднять Milvus (Docker).
2. Создать коллекцию, загрузить данные, протестировать поиск.
3. Настроить индексы для ускорения поиска.


## GraphRAG

**Задача**: улучшить контекст для LLM, используя графовую структуру данных.

**Полезные ресурсы**:
* medium [what is graph rag](https://medium.com/@zilliz_learn/graphrag-explained-enhancing-rag-with-knowledge-graphs-3312065f99e1)
- Tutorial [Graph RAG with Milvus](https://milvus.io/docs/graph_rag_with_milvus.md)
- [Обзор GraphRAG (Medium, англ.) ]([https://youtu.be/C14DFAlaFIw](https://youtu.be/C14DFAlaFIw))

🛠 **Применение**:

1. Изучить, как GraphRAG формирует связи между документами.
2. Реализовать простой графовый контекст для поиска.
3. Подключить к Milvus и проверить эффективность.


## OpenAI API (контракт взаимодействия FastAPI ↔ LLM)

**Задача**: передавать найденный контекст в LLM и получать качественный ответ.

**Полезные ресурсы**:
- **Официальная документация OpenAI API** → [https://platform.openai.com/docs/](https://platform.openai.com/docs/)
    - [API Reference](https://platform.openai.com/docs/api-reference/authentication)
    - [Chat Completions](https://platform.openai.com/docs/guides/completions)
    - [ Fine-Tuning](https://platform.openai.com/docs/guides/fine-tuning)


🛠 **Применение**:
1. Настроить взаимодействие с OpenAI API.
2. Передавать релевантный контекст из Milvus.
3. Оптимизировать промпт для получения точных ответов.


## LLM (промпт, настройка формата ответа)

**Задача**: создать промпт, обеспечивающий точность и релевантность ответа.

**Полезные ресурсы**:

- [Промпт-инжиниринг для OpenAI](https://platform.openai.com/docs/guides/prompt-engineering) 
- [Лучшие практики генерации ответов ](https://cookbook.openai.com/examples/enhance_your_prompts_with_meta_prompting)

🛠 **Применение**:
1. Разработать промпт-шаблон для генерации ответов.
2. Настроить формат JSON-ответа.
3. Оптимизировать запросы на основе тестов.

## Redis

**Задача**: кэшировать результаты поиска и ответов LLM для ускорения работы сервиса.

**Полезные ресурсы**:

- **Официальная документация Redis** 
    - [Caching](https://redis.io/learn/howtos/solutions/microservices/caching)
    - [Persistence](https://redis.io/docs/latest/operate/oss_and_stack/management/persistence/)
    - [Data Structures](https://redis.io/technology/data-structures/)

- **Статья на Habr**: 
	- [Chache по полочкам](https://habr.com/ru/articles/734660/)
	- [системы кэширования для высоконагруженной системы](https://habr.com/ru/articles/804205/)

🛠 **Применение**:
1. Подключить Redis к FastAPI.
2. Реализовать семантическое кэширование.
3. Настроить TTL и стратегию обновления кэша


## Финальная интеграция

**Задача**: объединить все компоненты в рабочий сервис.

**Полезные ресурсы**:

- [**Docker-compose для FastAPI + Redis + Milvus**](https://github.com/milvus-io/bootcamp)
- [**CI/CD и деплой FastAPI**](https://medium.com/@johnayinde/deploying-a-fastapi-application-with-ci-cd-a-devops-journey-f446c4679bfa)

🛠 **Применение**:
1. Настроить Docker Compose для сервисов.
2. Провести нагрузочное тестирование.
3. Оптимизировать запросы и индексацию Milvus.