 установить savant. в документации написано we provide the instruction on how to configure Ubuntu 22.04 runtime. If you use another operation system, adapt the instructions to your OS. 

Update Packages and Install Basic Tools
sudo apt-get update
sudo apt-get install -y git git-lfs curl -y

Install Docker
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh



Install Nvidia Container Toolkit
distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add -
curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list

sudo apt-get update
sudo apt-get install -y nvidia-container-toolkit
sudo systemctl restart docker


# Face detection pipline

**Issue: Настройка пайплайна для face_reid в Savant**

Savant [https://github.com/insight-platform/Savant](https://github.com/insight-platform/Savant) —  открытый фреймворк, предназначенный для создания систем обработки и анализа видеопотоков в реальном времени. В нем реализована поддержка работы с компонентами детекции сущностей, такими как лица, люди и другие объекты.

**Проблема:**  
Отсутствует корректно настроенный пайплайн для задачи детекции и идентификации лиц (face-detect/face-reid) в рамках использования фреймворка Savant. Требуется интеграция модуля в целевую архитектуру (_ссылка_), включая работу с компонентами отслеживания (tracking-group) для обработки видеопотока.

**Цель:**  
Настроить и протестировать пайплайн face-detect/face-reid в Savant, чтобы обеспечить его соответствие требованиям целевой архитектуры, включая корректную обработку данных и интеграцию с компонентами трекинга.

**Аргументация:**

1. Реализация face-detect/face-reid позволит расширить функциональность системы, добавив возможность детекции и идентификации лиц.
2. Интеграция с компонентами трекинга улучшит точность и производительность при работе с видеопотоками, обеспечив поддержку групповой обработки и анализа данных.
3. Настройка пайплайна и тестирование на целевой архитектуре необходимы для дальнейшего масштабирования решения и внедрения в продуктивную среду.

**Задачи:**

1. Выполнить диагностику существующего модуля face_reid в Savant.
2. Настроить пайплайн для задачи face-detect в соответствии с целевой архитектурой.
3. Интегрировать face-detect/face-reid с компонентом tracking-group.
4. Провести тестирование на данных видеопотоков для проверки корректности работы.
5. Подготовить документацию по настройке и интеграции.