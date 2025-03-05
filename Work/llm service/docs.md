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

- **Работа с внешними API (requests, async)** → https://fastapi.tiangolo.com/advanced/async-sql-databases/

🛠 **Применение**:

1. Поднять FastAPI-сервер и создать базовые эндпойнты.
2. Настроить асинхронные вызовы к Milvus и OpenAI API.
3. Подключить Redis для кэширования.