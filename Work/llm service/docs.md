## FastAPI

**Задача**: создать FastAPI-сервис, который принимает запросы, взаимодействует с Milvus, LLM и Redis.

📚 **Ресурсы**:

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
    - Search
    - [Collection](https://milvus.io/docs/manage-collections.md)
    - [Collection Schema](https://milvus.io/docs/schema.md)

    - Разделы: _"Get Started"_, _""_, _""_, _""_.
- **Пример интеграции с FastAPI** → https://zilliz.com/blog/how-to-build-a-scalable-ai-search-system
- **Видео-разбор Milvus (YouTube, англ.)** → ["Building a Vector Search System"](https://www.youtube.com/watch?v=X9GVa6CDidY)

🛠 **Применение**:

1. Поднять Milvus (Docker).
2. Создать коллекцию, загрузить данные, протестировать поиск.
3. Настроить индексы для ускорения поиска.