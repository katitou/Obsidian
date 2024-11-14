Например, **RetinaFace**, **MTCNN**, **Dlib**, YOLOv11-face

- **InsightFace**  
    Эта библиотека применяет архитектуры RetinaFace для детекции и SubCenter-ArcFace для распознавания лиц. InsightFace отличается высокой точностью (99.86% на датасете LFW) и поддерживает глубокую встраиваемую детекцию лиц, что позволяет использовать её в приложениях с высоким требованием к точности и скорости. [InsightFace на GitHub](https://github.com/deepinsight/insightface).
    
- **RetinaFace**  
    RetinaFace, являясь частью InsightFace, фокусируется на детекции лиц с высокой точностью и включает поддержку для анализа лиц, таких как поворот и позиции ключевых точек лица. Она отлично подходит для задач предобработки перед распознаванием и может быть использована как отдельная модель. [RetinaFace на GitHub](https://github.com/serengil/retinaface).
    
- **FaceNet**  
    FaceNet использует архитектуру Inception, достигая точности 99.65% на LFW и предоставляет детальные представления лиц, которые можно использовать для классификации или сверки. Однако, FaceNet больше не обновляется, поэтому лучше проверять совместимость для конкретных задач. [FaceNet на GitHub](https://github.com/davidsandberg/facenet).
    
- **CompreFace**  
    Это решение предлагает REST API и удобный интерфейс для управления коллекциями лиц и ролями пользователей. CompreFace поддерживает модели FaceNet и InsightFace, что делает его универсальным инструментом, особенно в проектах с распределенными вычислениями. Установка возможна через Docker. [CompreFace на GitHub](https://github.com/exadel-inc/CompreFace).
    
- **DeepFace**  
    Библиотека DeepFace поддерживает несколько методов, включая FaceNet, VGG-Face и другие, что делает её универсальной для различных задач. Она имеет встроенный REST API, что упрощает интеграцию с Python-приложениями и делает её хорошим выбором для общего распознавания лиц. [DeepFace на GitHub](https://github.com/serengil/deepface)
    
    ![[Pasted image 20241113152131.png]]
    .



## List of Face Recognition Datasets

The following is a [list](https://www.geeksforgeeks.org/list-cpp-stl/) of ten important datasets that are widely used in the field of face recognition:

- Labeled Faces in the Wild (LFW)
- YouTube Faces DB
- CelebA
- CASIA WebFace
- FERET Database
- PubFig
- MS-Celeb-1M
- VGGFace2
- MegaFace
- UMDFaces
- у меня есть 2 файла из opensource dataset Labeled Faces in the Wild: peopleDevTrain.csv и peopleDevTest.csv, а также датасет, где каждая папка содержит изображения лиц с определенным количеством изображений для каждого человека.
  пример записи из файла
name,images
AJ_Lamas,1
Aaron_Guiel,1
Abdullah_Gul,19
	как в коде сформировать тренировочный и тестовый датасет? 

есть:
датафрейм с именем и путь к изображению
файл peopleDevTrain.csv с именами и количеством изображений для обучающей выборки
файл peopleDevTest.csv с именем и числом изображений для тестовой выборки 
модель insight face для которой нужно измерить ее показатели по детекции лица
можешь помочь написать код для этого? 