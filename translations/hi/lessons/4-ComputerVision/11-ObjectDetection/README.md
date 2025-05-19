YOLO एक वास्तविक समय का एक-पास एल्गोरिदम है। इसका मुख्य विचार निम्नलिखित है:

* छवि को $S\times S$ क्षेत्रों में विभाजित किया जाता है
* प्रत्येक क्षेत्र के लिए, **CNN** $n$ संभावित वस्तुओं, *bounding box* के निर्देशांक और *confidence*=*probability* * IoU की भविष्यवाणी करता है।

![YOLO](../../../../../translated_images/yolo.a2648ec82ee8bb4ea27537677adb482fd4b733ca1705c561b6a24a85102dced5.hi.png)
> चित्र [official paper](https://arxiv.org/abs/1506.02640) से

### अन्य एल्गोरिदम

* RetinaNet: [official paper](https://arxiv.org/abs/1708.02002)
   - [Torchvision में PyTorch कार्यान्वयन](https://pytorch.org/vision/stable/_modules/torchvision/models/detection/retinanet.html)
   - [Keras कार्यान्वयन](https://github.com/fizyr/keras-retinanet)
   - [Keras सैंपल में RetinaNet के साथ वस्तु पहचान](https://keras.io/examples/vision/retinanet/)
* SSD (सिंगल शॉट डिटेक्टर): [official paper](https://arxiv.org/abs/1512.02325)

## ✍️ अभ्यास: वस्तु पहचान

अपने अध्ययन को निम्नलिखित नोटबुक में जारी रखें:

[ObjectDetection.ipynb](../../../../../lessons/4-ComputerVision/11-ObjectDetection/ObjectDetection.ipynb)

## निष्कर्ष

इस पाठ में आपने वस्तु पहचान के विभिन्न तरीकों का संक्षिप्त दौरा किया!

## 🚀 चुनौती

इन लेखों और नोटबुकों को YOLO के बारे में पढ़ें और खुद आजमाएं

* YOLO का वर्णन करने वाला [अच्छा ब्लॉग पोस्ट](https://www.analyticsvidhya.com/blog/2018/12/practical-guide-object-detection-yolo-framewor-python/)
 * [आधिकारिक साइट](https://pjreddie.com/darknet/yolo/)
 * Yolo: [Keras कार्यान्वयन](https://github.com/experiencor/keras-yolo2), [कदम-दर-कदम नोटबुक](https://github.com/experiencor/basic-yolo-keras/blob/master/Yolo%20Step-by-Step.ipynb)
 * Yolo v2: [Keras कार्यान्वयन](https://github.com/experiencor/keras-yolo2), [कदम-दर-कदम नोटबुक](https://github.com/experiencor/keras-yolo2/blob/master/Yolo%20Step-by-Step.ipynb)

## [पाठ के बाद का क्विज़](https://red-field-0a6ddfd03.1.azurestaticapps.net/quiz/211)

## समीक्षा & आत्म-अध्ययन

* [वस्तु पहचान](https://tjmachinelearning.com/lectures/1718/obj/) निखिल सर्डाना द्वारा
* [वस्तु पहचान एल्गोरिदम की अच्छी तुलना](https://lilianweng.github.io/lil-log/2018/12/27/object-detection-part-4.html)
* [वस्तु पहचान के लिए गहरे शिक्षण एल्गोरिदम की समीक्षा](https://medium.com/comet-app/review-of-deep-learning-algorithms-for-object-detection-c1f3d437b852)
* [बुनियादी वस्तु पहचान एल्गोरिदम का कदम-दर-कदम परिचय](https://www.analyticsvidhya.com/blog/2018/10/a-step-by-step-introduction-to-the-basic-object-detection-algorithms-part-1/)
* [वस्तु पहचान के लिए Python में Faster R-CNN का कार्यान्वयन](https://www.analyticsvidhya.com/blog/2018/11/implementation-faster-r-cnn-python-object-detection/)

## [असाइनमेंट: वस्तु पहचान](lab/README.md)

**अस्वीकृति**:  
यह दस्तावेज़ मशीन-आधारित एआई अनुवाद सेवाओं का उपयोग करके अनुवादित किया गया है। जबकि हम सटीकता के लिए प्रयास करते हैं, कृपया ध्यान दें कि स्वचालित अनुवादों में त्रुटियाँ या अशुद्धियाँ हो सकती हैं। मूल दस्तावेज़ को उसकी मातृ भाषा में प्राधिकृत स्रोत माना जाना चाहिए। महत्वपूर्ण जानकारी के लिए, पेशेवर मानव अनुवाद की सिफारिश की जाती है। हम इस अनुवाद के उपयोग से उत्पन्न किसी भी गलतफहमी या गलत व्याख्या के लिए उत्तरदायी नहीं हैं।