
Изменить структуру архива так, чтобы его содержимое (например, `yolov8n-face.txt`) находилось в корне, а не внутри дополнительной папки:

```bash
# находитесь в директории folder, внутри которой лежит архив

| folder
		|
		|___yolov8n-face.zip
		|___yolov8n-face
						|___file.*
						|___file.*
						|___file.*
		|___other_file.*




zip -d yolov8n-face.zip yolov8n-face/*
cd yolov8n-face
zip -r yolov8n-face.zip *

```
