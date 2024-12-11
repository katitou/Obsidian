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

Savant [https://github.com/insight-platform/Savant](https://github.com/insight-platform/Savant) —  открытый фреймворк, предназначенный для создания систем обработки и анализа видеопотоков в реальном времени. 

**Проблема:**  
Требуется настроить пайплайн для задачи детекции и идентификации лиц (face-detect/face-reid)  в рамках использования фреймворка Savant с последующей интеграцией модуля в целевую архитектуру https://confluence.dns-shop.ru/pages/viewpage.action?pageId=233604452 . 

**Задачи:**
1. Настроить и протестировать существующий модуль face_reid в Savant
2. Настроить пайплайн для задачи face-detect в соответствии с целевой архитектурой
3. Интегрировать face-detect/face-reid с компонентом tracking-group
4. Исследовать возможности интеграции с векторной БД Milvus 
5. Провести тестирование на данных видеопотоков 


Проведена отладка для корректного запуска модуля, тестирование пайплайна face_reid на внутренних данных (материал с видеокамер разных филиалов) для проверки функциональности и производительности. Начата работа по формированию отдельной ветки для функции face-detection в streamio-templates. Планируется изучить и протестировать работу с компонентами отслеживания (tracking-group).