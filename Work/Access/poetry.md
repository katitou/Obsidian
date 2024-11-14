
**Найдите путь к окружению**: Используйте команду `poetry env info --path`, чтобы узнать, где `poetry` хранит виртуальное окружение для вашего проекта:
```bash 
poetry env info --path
```

Эта команда выведет путь к виртуальному окружению, например:
```
/home/username/.cache/pypoetry/virtualenvs/your-project-name-py3.10
```

**Активируйте окружение вручную**: Используя путь из предыдущего шага, активируйте окружение, выполнив команду в терминале (например, для bash):
```bash 
source /home/username/.cache/pypoetry/virtualenvs/your-project-name-py3.10/bin/activate

```

**Декативация**:

```bash
deactivate
```
