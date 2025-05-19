### YOLO - Вы смотрите только один раз

YOLO — это алгоритм реального времени с одним проходом. Основная идея заключается в следующем:

* Изображение делится на $S\times S$ области
* Для каждой области **CNN** предсказывает $n$ возможных объектов, координаты *bounding box* и *confidence*=*вероятность* * IoU.

![YOLO](../../../../../translated_images/yolo.a2648ec82ee8bb4ea27537677adb482fd4b733ca1705c561b6a24a85102dced5.ru.png)
> Изображение из [официальной статьи](https://arxiv.org/abs/1506.02640)

### Другие алгоритмы

* RetinaNet: [официальная статья](https://arxiv.org/abs/1708.02002)
   - [Реализация на PyTorch в Torchvision](https://pytorch.org/vision/stable/_modules/torchvision/models/detection/retinanet.html)
   - [Реализация на Keras](https://github.com/fizyr/keras-retinanet)
   - [Обнаружение объектов с помощью RetinaNet](https://keras.io/examples/vision/retinanet/) в примерах Keras
* SSD (Single Shot Detector): [официальная статья](https://arxiv.org/abs/1512.02325)

## ✍️ Упражнения: Обнаружение объектов

Продолжите обучение в следующем ноутбуке:

[ObjectDetection.ipynb](../../../../../lessons/4-ComputerVision/11-ObjectDetection/ObjectDetection.ipynb)

## Заключение

На этом уроке вы сделали стремительный обзор всех различных способов, которыми можно осуществить обнаружение объектов!

## 🚀 Вызов

Прочитайте эти статьи и ноутбуки о YOLO и попробуйте сами

* [Хорошая статья в блоге](https://www.analyticsvidhya.com/blog/2018/12/practical-guide-object-detection-yolo-framewor-python/) о YOLO
 * [Официальный сайт](https://pjreddie.com/darknet/yolo/)
 * Yolo: [реализация на Keras](https://github.com/experiencor/keras-yolo2), [пошаговый ноутбук](https://github.com/experiencor/basic-yolo-keras/blob/master/Yolo%20Step-by-Step.ipynb)
 * Yolo v2: [реализация на Keras](https://github.com/experiencor/keras-yolo2), [пошаговый ноутбук](https://github.com/experiencor/keras-yolo2/blob/master/Yolo%20Step-by-Step.ipynb)

## [Викторина после лекции](https://red-field-0a6ddfd03.1.azurestaticapps.net/quiz/211)

## Обзор и самостоятельное изучение

* [Обнаружение объектов](https://tjmachinelearning.com/lectures/1718/obj/) от Нихила Сарданы
* [Хорошее сравнение алгоритмов обнаружения объектов](https://lilianweng.github.io/lil-log/2018/12/27/object-detection-part-4.html)
* [Обзор алгоритмов глубокого обучения для обнаружения объектов](https://medium.com/comet-app/review-of-deep-learning-algorithms-for-object-detection-c1f3d437b852)
* [Пошаговое введение в основные алгоритмы обнаружения объектов](https://www.analyticsvidhya.com/blog/2018/10/a-step-by-step-introduction-to-the-basic-object-detection-algorithms-part-1/)
* [Реализация Faster R-CNN на Python для обнаружения объектов](https://www.analyticsvidhya.com/blog/2018/11/implementation-faster-r-cnn-python-object-detection/)

## [Задание: Обнаружение объектов](lab/README.md)

**Отказ от ответственности**:  
Этот документ был переведен с использованием услуг машинного перевода на основе ИИ. Хотя мы стремимся к точности, пожалуйста, имейте в виду, что автоматические переводы могут содержать ошибки или неточности. Оригинальный документ на родном языке должен считаться авторитетным источником. Для критически важной информации рекомендуется профессиональный человеческий перевод. Мы не несем ответственности за любые недоразумения или неправильные толкования, возникающие в результате использования этого перевода.