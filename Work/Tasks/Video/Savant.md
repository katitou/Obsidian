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


```
def main(args):

logger = get_logger('index_client')
logger.info('Starting Savant client...')

source = SourceBuilder().with_socket(args.zmq_src_socket).build()

sink =SinkBuilder().with_socket(args.zmq_sink_socket).with_idle_timeout(10).build()
# process image
...

img = BytesIO(img.tobytes())

# attach image path to metadata # finish sending frames
  
# Init index

index = hnswlib.Index(space=args.index_space, dim=args.index_dim)


logger.info('Receiving results from the module...')


# get location tag from metadata

loc_attr = result.frame_meta.get_attribute('default', 'location')

...


# get the face feature vector from metadata

...

  

# assign person_id to person_name in the order of appearance

...

  
img = np.frombuffer(result.frame_content, dtype=np.uint8)

for obj in objs:

feature_attr = obj.get_attribute(args.feature_namespace, args.feature_name)

feature = feature_attr.values[0].as_floats()

# index stores single int label for each feature

feature_id = pack_person_id_img_n(person_id, img_n)

index.add_items(feature, feature_id)

  

left, top, right, bottom = obj.detection_box.as_ltrb_int()


try:

face_img = img[top:bottom, left:right]

except IndexError:

logger.error('%s: detection box out of image bounds.', file_name)

else:

face_img = cv2.cvtColor(face_img, cv2.COLOR_RGBA2BGR)

img_path = os.path.join(

processed_gallery_dir,

f'{person_name}_{person_id:03d}_{img_n:03d}.jpeg',

)

logger.info('All images processed, stopping the module.')


source.send_shutdown(args.source_id, args.shutdown_auth)


```