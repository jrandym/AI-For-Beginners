# कंप्यूटर दृष्टि का परिचय

[कंप्यूटर दृष्टि](https://wikipedia.org/wiki/Computer_vision) एक ऐसा क्षेत्र है जिसका उद्देश्य कंप्यूटर को डिजिटल छवियों की उच्च-स्तरीय समझ प्राप्त करने में सक्षम बनाना है। यह एक व्यापक परिभाषा है, क्योंकि *समझना* कई अलग-अलग चीजों का मतलब हो सकता है, जिसमें एक चित्र में एक वस्तु को ढूंढना (**वस्तु पहचान**), यह समझना कि क्या हो रहा है (**घटना पहचान**), चित्र का पाठ में वर्णन करना, या 3D में दृश्य का पुनर्निर्माण करना शामिल है। मानव छवियों से संबंधित विशेष कार्य भी हैं: उम्र और भावना का अनुमान, चेहरे की पहचान और पहचान, और 3D मुद्रा का अनुमान, कुछ नाम रखने के लिए।

## [प्री-लेचर क्विज़](https://red-field-0a6ddfd03.1.azurestaticapps.net/quiz/106)

कंप्यूटर दृष्टि के सबसे सरल कार्यों में से एक है **छवि वर्गीकरण**।

कंप्यूटर दृष्टि को अक्सर एआई की एक शाखा माना जाता है। आजकल, अधिकांश कंप्यूटर दृष्टि कार्यों को न्यूरल नेटवर्क का उपयोग करके हल किया जाता है। इस अनुभाग में, हम कंप्यूटर दृष्टि के लिए उपयोग किए जाने वाले विशेष प्रकार के न्यूरल नेटवर्क, [संवहन न्यूरल नेटवर्क](../07-ConvNets/README.md) के बारे में और अधिक जानेंगे।

हालांकि, जब आप छवि को न्यूरल नेटवर्क में पास करते हैं, तो कई मामलों में छवि को बढ़ाने के लिए कुछ एल्गोरिदम तकनीकों का उपयोग करना समझदारी है।

छवि प्रसंस्करण के लिए कई Python पुस्तकालय उपलब्ध हैं:

* **[imageio](https://imageio.readthedocs.io/en/stable/)** विभिन्न छवि प्रारूपों को पढ़ने/लिखने के लिए उपयोग किया जा सकता है। यह ffmpeg का भी समर्थन करता है, जो वीडियो फ़्रेमों को छवियों में परिवर्तित करने के लिए एक उपयोगी उपकरण है।
* **[Pillow](https://pillow.readthedocs.io/en/stable/index.html)** (जिसे PIL के नाम से भी जाना जाता है) थोड़ा अधिक शक्तिशाली है, और इसमें कुछ छवि हेरफेर जैसे रूपांतरण, पैलेट समायोजन आदि का समर्थन भी है।
* **[OpenCV](https://opencv.org/)** एक शक्तिशाली छवि प्रसंस्करण पुस्तकालय है जो C++ में लिखा गया है, जो छवि प्रसंस्करण के लिए *de facto* मानक बन गया है। इसमें एक सुविधाजनक Python इंटरफ़ेस है।
* **[dlib](http://dlib.net/)** एक C++ पुस्तकालय है जो कई मशीन लर्निंग एल्गोरिदम को लागू करता है, जिसमें कुछ कंप्यूटर दृष्टि एल्गोरिदम भी शामिल हैं। इसमें एक Python इंटरफ़ेस भी है, और इसे चेहरे और चेहरे के लैंडमार्क पहचान जैसी चुनौतीपूर्ण कार्यों के लिए उपयोग किया जा सकता है।

## OpenCV

[OpenCV](https://opencv.org/) को छवि प्रसंस्करण के लिए *de facto* मानक माना जाता है। इसमें बहुत सारे उपयोगी एल्गोरिदम शामिल हैं, जो C++ में लागू किए गए हैं। आप Python से भी OpenCV को कॉल कर सकते हैं।

OpenCV सीखने के लिए एक अच्छा स्थान है [यह Learn OpenCV कोर्स](https://learnopencv.com/getting-started-with-opencv/)। हमारे पाठ्यक्रम में, हमारा लक्ष्य OpenCV सीखना नहीं है, बल्कि आपको कुछ उदाहरण दिखाना है जब इसका उपयोग किया जा सकता है, और कैसे।

### छवियों को लोड करना

Python में छवियों को NumPy ऐरे के माध्यम से सुविधाजनक रूप से प्रस्तुत किया जा सकता है। उदाहरण के लिए, 320x200 पिक्सल के आकार की ग्रेस्केल छवियों को 200x320 ऐरे में संग्रहीत किया जाएगा, और समान आकार की रंगीन छवियों का आकार 200x320x3 होगा (3 रंग चैनलों के लिए)। एक छवि को लोड करने के लिए, आप निम्नलिखित कोड का उपयोग कर सकते हैं:

```python
import cv2
import matplotlib.pyplot as plt

im = cv2.imread('image.jpeg')
plt.imshow(im)
```

परंपरागत रूप से, OpenCV रंगीन छवियों के लिए BGR (नीला-हरा-लाल) एनकोडिंग का उपयोग करता है, जबकि बाकी Python उपकरण अधिक पारंपरिक RGB (लाल-हरा-नीला) का उपयोग करते हैं। छवि को सही दिखने के लिए, आपको इसे RGB रंग स्थान में परिवर्तित करना होगा, या तो NumPy ऐरे में आयामों को बदलकर, या OpenCV फ़ंक्शन को कॉल करके:

```python
im = cv2.cvtColor(im,cv2.COLOR_BGR2RGB)
```

एक ही `cvtColor` function can be used to perform other color space transformations such as converting an image to grayscale or to the HSV (Hue-Saturation-Value) color space.

You can also use OpenCV to load video frame-by-frame - an example is given in the exercise [OpenCV Notebook](../../../../../lessons/4-ComputerVision/06-IntroCV/OpenCV.ipynb).

### Image Processing

Before feeding an image to a neural network, you may want to apply several pre-processing steps. OpenCV can do many things, including:

* **Resizing** the image using `im = cv2.resize(im, (320,200),interpolation=cv2.INTER_LANCZOS)`
* **Blurring** the image using `im = cv2.medianBlur(im,3)` or `im = cv2.GaussianBlur(im, (3,3), 0)`
* Changing the **brightness and contrast** of the image can be done by NumPy array manipulations, as described [in this Stackoverflow note](https://stackoverflow.com/questions/39308030/how-do-i-increase-the-contrast-of-an-image-in-python-opencv).
* Using [thresholding](https://docs.opencv.org/4.x/d7/d4d/tutorial_py_thresholding.html) by calling `cv2.threshold`/`cv2.adaptiveThreshold` फ़ंक्शन, जो अक्सर चमक या कंट्रास्ट को समायोजित करने के लिए पसंद किया जाता है।
* छवि पर विभिन्न [रूपांतरणों](https://docs.opencv.org/4.5.5/da/d6e/tutorial_py_geometric_transformations.html) को लागू करना:
    - **[Affine transformations](https://docs.opencv.org/4.5.5/d4/d61/tutorial_warp_affine.html)** उपयोगी हो सकते हैं यदि आपको छवि में घुमाव, आकार बदलने और झुकाव को संयोजित करने की आवश्यकता है और आपको छवि में तीन बिंदुओं के स्रोत और गंतव्य स्थान ज्ञात हैं। अफाइन रूपांतरण समानांतर रेखाओं को समानांतर रखते हैं।
    - **[Perspective transformations](https://medium.com/analytics-vidhya/opencv-perspective-transformation-9edffefb2143)** उपयोगी हो सकते हैं जब आप छवि में 4 बिंदुओं के स्रोत और गंतव्य स्थितियों को जानते हैं। उदाहरण के लिए, यदि आप किसी स्मार्टफोन कैमरे से किसी आयताकार दस्तावेज़ की तस्वीर लेते हैं और आप दस्तावेज़ की एक आयताकार छवि बनाना चाहते हैं।
* **[Optical flow](https://docs.opencv.org/4.5.5/d4/dee/tutorial_optical_flow.html)** का उपयोग करके छवि के अंदर आंदोलन को समझना।

## कंप्यूटर दृष्टि के उपयोग के उदाहरण

हमारे [OpenCV नोटबुक](../../../../../lessons/4-ComputerVision/06-IntroCV/OpenCV.ipynb) में, हम कुछ उदाहरण देते हैं जब कंप्यूटर दृष्टि का उपयोग विशिष्ट कार्यों को करने के लिए किया जा सकता है:

* **ब्रेल पुस्तक की एक तस्वीर को पूर्व-प्रसंस्कृत करना**। हम इस पर ध्यान केंद्रित करते हैं कि हम कैसे थ्रेशोल्डिंग, फीचर डिटेक्शन, परिप्रेक्ष्य रूपांतरण और NumPy हेरफेर का उपयोग करके व्यक्तिगत ब्रेल प्रतीकों को अलग कर सकते हैं ताकि उन्हें न्यूरल नेटवर्क द्वारा आगे वर्गीकृत किया जा सके।

![Braille Image](../../../../../translated_images/braille.341962ff76b1bd7044409371d3de09ced5028132aef97344ea4b7468c1208126.hi.jpeg) | ![Braille Image Pre-processed](../../../../../translated_images/braille-result.46530fea020b03c76aac532d7d6eeef7f6fb35b55b1001cd21627907dabef3ed.hi.png) | ![Braille Symbols](../../../../../translated_images/braille-symbols.0159185ab69d533909dc4d7d26a1971b51401c6a80eb3a5584f250ea880af88b.hi.png)
----|-----|-----

> छवि [OpenCV.ipynb](../../../../../lessons/4-ComputerVision/06-IntroCV/OpenCV.ipynb) से

* **फ्रेम अंतर का उपयोग करके वीडियो में गति का पता लगाना**। यदि कैमरा स्थिर है, तो कैमरा फीड से फ्रेम एक-दूसरे के समान होने चाहिए। चूंकि फ्रेमों का प्रतिनिधित्व ऐरे के रूप में किया जाता है, इसलिए दो लगातार फ्रेमों के लिए उन ऐरे को घटाकर हम पिक्सेल का अंतर प्राप्त करेंगे, जो स्थिर फ्रेम के लिए कम होना चाहिए, और छवि में महत्वपूर्ण गति होने पर अधिक हो जाएगा।

![Image of video frames and frame differences](../../../../../translated_images/frame-difference.706f805491a0883c938e16447bf5eb2f7d69e812c7f743cbe7d7c7645168f81f.hi.png)

> छवि [OpenCV.ipynb](../../../../../lessons/4-ComputerVision/06-IntroCV/OpenCV.ipynb) से

* **ऑप्टिकल फ्लो का उपयोग करके गति का पता लगाना**। [ऑप्टिकल फ्लो](https://docs.opencv.org/3.4/d4/dee/tutorial_optical_flow.html) हमें यह समझने की अनुमति देता है कि वीडियो फ़्रेम पर व्यक्तिगत पिक्सेल कैसे चलते हैं। ऑप्टिकल फ्लो के दो प्रकार हैं:

   - **Dense Optical Flow** उस वेक्टर फ़ील्ड की गणना करता है जो दिखाता है कि प्रत्येक पिक्सेल कहाँ जा रहा है
   - **Sparse Optical Flow** छवि में कुछ विशिष्ट विशेषताओं (जैसे किनारों) को लेने और फ्रेम से फ्रेम उनकी गति बनाने पर आधारित है।

![Image of Optical Flow](../../../../../translated_images/optical.1f4a94464579a83a10784f3c07fe7228514714b96782edf50e70ccd59d2d8c4f.hi.png)

> छवि [OpenCV.ipynb](../../../../../lessons/4-ComputerVision/06-IntroCV/OpenCV.ipynb) से

## ✍️ उदाहरण नोटबुक: OpenCV [OpenCV in Action का प्रयास करें](../../../../../lessons/4-ComputerVision/06-IntroCV/OpenCV.ipynb)

आइए OpenCV के साथ कुछ प्रयोग करें [OpenCV नोटबुक](../../../../../lessons/4-ComputerVision/06-IntroCV/OpenCV.ipynb) की खोज करके

## निष्कर्ष

कभी-कभी, गति पहचान या fingertip पहचान जैसी अपेक्षाकृत जटिल कार्यों को पूरी तरह से कंप्यूटर दृष्टि द्वारा हल किया जा सकता है। इसलिए, कंप्यूटर दृष्टि की बुनियादी तकनीकों को जानना और OpenCV जैसी पुस्तकालयों द्वारा क्या किया जा सकता है, बहुत सहायक है।

## 🚀 चुनौती

[इस वीडियो](https://docs.microsoft.com/shows/ai-show/ai-show--2021-opencv-ai-competition--grand-prize-winners--cortic-tigers--episode-32?WT.mc_id=academic-77998-cacaste) को देखें AI शो से, ताकि आप Cortic Tigers परियोजना के बारे में जान सकें और कैसे उन्होंने एक ब्लॉक-आधारित समाधान बनाया ताकि रोबोट के माध्यम से कंप्यूटर दृष्टि कार्यों का लोकतंत्रीकरण किया जा सके। इस क्षेत्र में नए शिक्षार्थियों को शामिल करने में मदद करने वाले अन्य परियोजनाओं पर कुछ शोध करें।

## [पोस्ट-लेचर क्विज़](https://red-field-0a6ddfd03.1.azurestaticapps.net/quiz/206)

## समीक्षा और आत्म अध्ययन

ऑप्टिकल फ्लो के बारे में अधिक पढ़ें [इस शानदार ट्यूटोरियल में](https://learnopencv.com/optical-flow-in-opencv/)।

## [असाइनमेंट](lab/README.md)

इस प्रयोगशाला में, आप सरल इशारों के साथ एक वीडियो लेंगे, और आपका लक्ष्य ऑप्टिकल फ्लो का उपयोग करके ऊपर/नीचे/बाएं/दाएं आंदोलनों को निकालना है।

<img src="images/palm-movement.png" width="30%" alt="Palm Movement Frame"/>

**अस्वीकृति**:  
यह दस्तावेज़ मशीन-आधारित एआई अनुवाद सेवाओं का उपयोग करके अनुवादित किया गया है। जबकि हम सटीकता के लिए प्रयासरत हैं, कृपया ध्यान दें कि स्वचालित अनुवादों में त्रुटियाँ या गलतियाँ हो सकती हैं। मूल दस्तावेज़ को उसकी मूल भाषा में प्राधिकृत स्रोत माना जाना चाहिए। महत्वपूर्ण जानकारी के लिए, पेशेवर मानव अनुवाद की सिफारिश की जाती है। इस अनुवाद के उपयोग से उत्पन्न किसी भी गलतफहमी या गलत व्याख्या के लिए हम जिम्मेदार नहीं हैं।