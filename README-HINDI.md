<p align="center"><img width="300" src="https://raw.githubusercontent.com/Jaysmito101/cgl/main/images/CGL_logo_low_mid_res.png" border="0">
</p>



<p align="center">

<img src="https://img.shields.io/github/issues-pr/Jaysmito101/cgl?style=for-the-badge" />
<img alt="Lines of code" src="https://img.shields.io/tokei/lines/github/Jaysmito101/cgl?style=for-the-badge" />
<img src="https://img.shields.io/github/repo-size/Jaysmito101/cgl?style=for-the-badge" />
<img alt="Maintenance" src="https://img.shields.io/maintenance/yes/2023?style=for-the-badge" />
<a href="https://patreon.com/jaysmito101"><img src="https://img.shields.io/endpoint.svg?url=https%3A%2F%2Fshieldsio-patreon.vercel.app%2Fapi%3Fusername%3Djaysmito101%26type%3Dpledges&style=for-the-badge" alt="Support me on Patreon" /></a>

</p>

<br/>



# अनुक्रमणिका
* [पहचान](#cgl)
* [प्लैटफ़ॉर्म](#target-platforms)
* [विशेषताएँ](#what-does-cgl-provide)
* [शोरील](#शोरील)

<br>


# सीजीएल
सीजीएल (सी ग्राफिक्स लाइब्रेरी) मुख्य रूप से मनोरंजक कोडिंग/डेमो दृश्यों/प्रोटोटाइपिंग/छोटे खेलों/प्रयोगों के लिए एक बहुउद्देशीय पुस्तकालय है। इसमें **ग्राफ़िक्स के लिए ढेर सारी उपयोगिताएँ** हैं। और सबसे अच्छी बात यह है कि यह एक हेडर फ़ाइल `cgl.h` के अंदर है। साथ ही CGL विशुद्ध रूप से C में बनाया गया है, लेकिन C ++ के साथ भी संगत है।

**ध्यान दें**: यह न सोचें कि शीर्षलेख का अर्थ केवल संकलन समय को बढ़ाने वाला है क्योंकि कार्यान्वयन की आवश्यकता `#define CGL_IMPLEMENTATION` का उपयोग करके केवल 1 फ़ाइल के लिए सक्षम होनी चाहिए। [उदाहरण](./examples) देखें

<br>

## लक्ष्य प्लेटफार्म

- <b><i>विंडोज़</b></i>
- <b><i>लिनक्स</b></i>
- <b><i>MacOS (अप्रयुक्त)</b></i>
- <b><i>वेबअसेंबली (बीटा)</b></i>
- <b><i>Android (जल्द ही आ रहा है)</b></i>

<br>

## सीजीएल क्या प्रदान करता है?

* वाइंडिंग लाइब्रेरी (वैकल्पिक)
   - आप इसे `#define CGL_EXCLUDE_WINDOW_API` द्वारा पूरी तरह से अक्षम कर सकते हैं
   - यह विंडोिंग लाइब्रेरी मुख्य रूप से कुछ अतिरिक्त कार्यात्मकताओं के साथ एक रैपर GLFW है। **उदाहरण**: यदि आप जीयूआई के लिए `nuklear` जैसी कुछ लाइब्रेरी का उपयोग कर रहे हैं तो यह सभी `glfw` कॉलबैक को गड़बड़ कर देगा, इसलिए CGL के साथ आप CGL कॉलबैक को `CGL_window_resecure_callbacks` पर कॉल करके पुनर्स्थापित कर सकते हैं

* उपयोगिता कार्यक्षमता
  - फ़ाइलें पढ़ना/लिखना
  - अनियमित float/int/bool/vec2/vec3/color उत्पादन
  - CRC32/CRC64
  - ROT13 कूटलेखन
  - सामान्य प्रयोजन हैशिंग कार्य [यहाँ देखें]( http://www.azillionmonkeys.com/qed/hash.html)
  - रंगीन printf (लाल, हरा, नीला, ग्रे / पीला)
  - बिंदु/त्रिकोण चौराहे की जाँच
  - कार्य करने की सूची: [ MD5 / SHA 256 / SHA 128 / AES ]

* Noise API
  - libc's rand के लिए कई तेज विकल्प
  - Procedural Coherent Noise Algorithms
    - Perlin's Noise (Improved Version)
    - OpenSimplex2
    - Value Noise
    - Worley Noise (or Cellular Noise)
  - Fractals like FBm, Rigid, Billow, PingPong
  - Parameters for Octaves/Lacunarity/Weighted Strength/Gain
 
* त्रिकोणासन
    - डेलॉने ट्राइएंगुलेटर के लिए बोवर वाटसन एल्गोरिथम
   
* आर्टिफिशियल इंटेलिजेंस
  - न्यूरल नेटवर्क्स
  - बैकप्रॉपैगेशन
  - सीरियलाइज़िंग / डिसेरिएलाइज़िंग नेटवर्क्स
  - मल्टीवेरिएबल लीनियर रिग्रेशन


* ग्राफ एल्गोरिदम
   - ए * पथ खोज (सामान्य उद्देश्य)

* डेटा संरचनाएं
   - सूची (गतिशील सरणी) + ढेर (एक साथ लागू)
   - हैशटेबल -> यह जल्दबाजी सामान्य उद्देश्य है। कुंजी स्ट्रिंग या एन-बिट बफर हो सकती है। मान कुछ भी int, string, float, कस्टम प्रकार, हो सकता है ...
      - हैशटेबल इटरेटर -> [सरल](https://github.com/Jaysmito101/cgl/blob/main/examples/using_hashtable_iterator.c) API का उपयोग करके हैशटेबल के माध्यम से पुनरावृति करें
  
* लकड़हारा
  - `#define CGL_DISABLE_LOGGER` द्वारा सक्षम/अक्षम किया जा सकता है
  - एक साथ कई लॉग फाइलों में लॉग इन करें
  - अलग लॉग स्तरों के लिए रंगीन आउटपुट के साथ कंसोल में लॉग इन करें
  - ऑटो टाइमस्टैम्प के साथ लकड़हारा
  
* क्रॉस प्लेटफार्म नेटवर्किंग (वैकल्पिक)
  - आप सभी नेटवर्किंग को `#define CGL_EXCLUDE_NETWORKING` द्वारा अक्षम कर सकते हैं
  - निम्न-स्तरीय सॉकेट
  - एसएसएल सॉकेट (वैकल्पिक) (ओपनएसएसएल की आवश्यकता है)
  - HTTP/HTTPS अनुरोध (बीटा)

* सामान्य उद्देश्य मार्कोव चेन (वैकल्पिक) [उदाहरण](./examples/markov_text_generation.c)
  - किसी भी प्रकार के डेटा (पाठ / छवि / आदि) के साथ काम कर सकते हैं
  - कोड की 3 - 4 पंक्तियों के साथ ट्रेन/उत्पन्न करें
  - टेक्स्ट जनरेशन (एन-ग्राम आधारित) के लिए ट्रेनर लागू किया गया
  - कस्टम परिदृश्यों के लिए कस्टम ट्रेनर एपीआई

* Cross Platform Threading
  - Threads
  - Mutex
  - Condition Variables (TODO)
  - नोट: विंडोज पर `Win32 थ्रेड्स` और लिनक्स पर `पथ्रेड` का उपयोग करके कार्यान्वित किया गया। (लिनक्स पर आपको `pthread` बनाने के लिए लिंक करने की आवश्यकता है)

* Bloom
  - कोड की केवल 1 पंक्ति के साथ किसी भी बनावट पर ब्लूम लागू करें
  - एकता के खिलने के आधार पर कार्यान्वयन
  - कस्टम थ्रेशोल्डिंग
  - कस्टम डाउनसैंपल/अपसैंपल पास
  - पूरी तरह से कंप्यूट शेडर्स में किया गया
  
* 2डी टक्कर का पता लगाने
  - 2डी बहुभुजों के बीच टकराव का पता लगाएं
  - बहुभुजों के लिए अलग अक्ष उत्पन्न करें
  - ओवरलैप दूरी प्राप्त करें
  - GJK (Gilbert–Johnson–Keerthi distance algorithm)
  - EPA (Expanding Polytope Algorithm)
  - SAT (Seperate Axis Theorem)

* मार्चिंग स्क्वायर
   - पूरी तरह से कस्टमाइज़ेबल मार्चर
   - रैखिक इंटरपोलेशन समर्थित
   - CGL के लिए 2D मेश (त्रिकोण) बनाता है

* तून पोस्ट प्रोसेसर
  - रूपरेखा प्रभाव
  - तून छायांकन प्रभाव
  - हैचिंग प्रभाव
  - सभी एक ही पोस्ट प्रोसेस कॉल में (प्रति वस्तु गणना नहीं)
  - कंप्यूट शेडर में पूरी तरह से लागू
  - अनुकूलन योग्य

* सीजीएल रे कास्ट
  - फास्ट 2डी रे कास्ट
  - कस्टम दीवारें
  - त्रिकोण जाल को बेक करें
  - पब्लिक रे कास्ट फंक्शन

* सीजीएल नोड संपादक
  - सीजीएल विजेट्स द्वारा संचालित के रूप में बहुत तेजी से
  - कस्टम नोड्स, पिन, लिंक
  - न्यूनतम और शक्तिशाली
  - अपने स्वयं के नोड्स और लिंक प्रकार एपीआई प्रस्तुत करें
  - ज़ूम इन/आउट करें
  - वैश्विक ऑफसेट
 
* सीजीएल ऑडियो एपीआई
  - क्रॉस प्लेटफार्म (ओपनएएल बैकएंड)
  - सरल एपीआई
  - WAV फाइल लोडर/सैंपलर

* सीजीएल विजेट (वैकल्पिक)
  - आप इसे `#define CGL_EXCLUDE_WIDGETS` द्वारा अक्षम कर सकते हैं
  - एपीआई जैसा [p5.js](https://p5js.org/)
  - पाठ विजेट (किसी भी फ़ॉन्ट को लोड या बेक किए बिना उच्च गुणवत्ता वाला कुरकुरा पाठ प्रस्तुत करें)
  - बैच रेंडरर बैकएंड (बड़ी संख्या में विगेट्स के लिए भी बहुत तेज)
  - ड्रा (भरा हुआ या स्ट्रोक किया हुआ):
    - त्रिभुज [`CGL_widgets_add_triangle`]
    - सामान्य क्वाड [`CGL_widgets_add_quad`]
    - आयत [`CGL_widgets_add_rect` `CGL_widgets_add_rect2f`]
    - लाइन [`CGL_widgets_add_line`]
    - वृत्त [`CGL_widgets_add_circle` `CGL_widgets_add_circle2f`]
    - अंडाकार [`CGL_widgets_add_oval`, `CGL_widgets_add_oval2f`]
    - चाप
  - कथानक
    - स्कैटर प्लॉट
    - बार ग्राफ़ (ऊर्ध्वाधर / क्षैतिज)
    - पाई चार्ट
    - एक समारोह प्लॉट करें
  - उन्नत बेजियर कर्व (रेखाएं या बिंदीदार) विजेट
  - अलग-अलग शिखर जोड़ें
  - स्ट्रोक रंग/मोटाई समायोजित करें
  - बैच रेंडरर अधिकतम कोने क्षमता को अनुकूलित करें (कम मेमोरी सिस्टम के लिए)

* गणित पुस्तकालय 
  - उन्नत मैट्रिक्स पुस्तकालय (यह ग्राफिक्स के लिए मैट्रिक्स पुस्तकालय से अलग है)
  - vec2/vec3/vec4
  - mat3/mat4 (for graphics)
  - add/sub/mul/div/scale/length/normalize/lerp/min/max/equal for vec2/vec3/vec4
  - rotate_x/rotate_y/rotate_z for vec3
  - scale/translate/rotate_x/rotate_y/rotate_z/add/sub/mul for mat4
  - perspective for mat4
  - transpose for mat4/(mat3 TODO)
  - Rotation Matrices using Goldman's Method
  - look_at matrix 
  - Quaternion math
  - वैक्टर बदलें
  - **ध्यान दें:** अधिकांश गणित कार्य मैक्रोज़ के माध्यम से कार्यान्वित किए जाते हैं, इसलिए **पूरी तरह इच्छुक** होंगे और बिना किसी अनावश्यक फ़ंक्शन कॉल के काफी तेज़ होंगे

* के लिए उच्च स्तरीय ओपनजीएल एपीआई (वैकल्पिक)
  - आप इसे `#define CGL_EXCLUDE_GRAPHICS_API` द्वारा पूरी तरह से अक्षम कर सकते हैं
  - बनावट (2D / 2D ऐरे / क्यूब मैप)
  - फ़्रेमबफ़र्स
  - एसएसबीओ (शेडर स्टोरेज बफर ऑब्जेक्ट)
  - यूबीओ (यूनिफ़ॉर्म बफर ऑब्जेक्ट)
  - शेडर्स
    - वर्टेक्स और फ्रैगमेंट (ज्यामिति शेडर शामिल नहीं है क्योंकि इसका बहुत व्यापक रूप से उपयोग नहीं किया जाता है)
    - कंप्यूट शेडर एपीआई

* सीजीएल मेश एपीआई
  - सीजीएल के पास मेश को संभालने के लिए एक उच्च स्तरीय एपीआई है
  - 2 प्रकार की जाली होती है
    - सीपीयू मेश -> मेश ऑपरेशंस के लिए उपयोग किए जाने वाले डेटा को भी स्टोर करता है
      - त्रिकोण उत्पन्न करें
      - चतुर्भुज उत्पन्न करें
      - लोड ओबीजे (बीटा)
      - घन उत्पन्न करें
      - विमान उत्पन्न करें
      - सिलेंडर उत्पन्न करें
      - गोला उत्पन्न करें
      - किसी भी पैरामीट्रिक सतह समारोह से जाल उत्पन्न करें [यहाँ देखें] (https://stackoverflow.com/a/31326534/14911094)
      - सामान्य गणना करें
      - मेश पर ऑपरेशन करें
        - 2 जाली लगाएं
        - ऑफसेट कोने
        - वगैरह ।
    - जीपीयू जाल -> जीपीयू पक्ष पर संग्रहीत डेटा के सूचक (आंतरिक रूप से वर्टेक्स बफर, इंडेक्स बफर, वर्टेक्स ऐरे को संभालता है) और इसके लिए उपयोग किया जा सकता है
      - प्रदान करना
      - प्रस्तुत करना
      - वायरफ्रेम प्रस्तुत करें
      - रेंडर वायरफ्रेम इंस्टेंस्ड
      
* सीजीएल कैमरा
  - सीजीएल एक उचित कैमरा अमूर्तता प्रदान करता है
  - परिप्रेक्ष्य और वर्तनी
  - यह आंतरिक रूप से सभी मैट्रिक्स गणनाओं को संभालता है (बस स्थिति और रोटेशन इनपुट करें)
  - ऑटो अप, राइट, फ्रंट वैक्टर की गणना करता है
 
* टेक्स्ट रेंडरिंग (वैकल्पिक) (आवश्यक [FreeType2](http://freetype.org/))
  - आप इसे `#define CGL_EXCLUDE_TEXT_RENDER` से पूरी तरह अक्षम कर सकते हैं
  - `.ttf` फ़ाइलों से फ़ॉन्ट लोड करें
  - पात्रों के लिए बिटमैप्स बेक करें
  - स्ट्रिंग्स से टेक्सचर बेक करें

* ट्रेल रेंडरर
  - फास्ट 3डी ट्रेल रेंडरर
  - जाली को बेक करें
  - कस्टम शेडर समर्थन
  - पूरी तरह से अनुकूलन योग्य
  
 
* स्काई रेंडरर (वैकल्पिक)
  - आप इसे `#define CGL_EXCLUDE_SKY_RENDERER` से पूरी तरह अक्षम कर सकते हैं
  - स्काई बॉक्स (क्यूब मेश) और स्काई स्फेयर/डोम (स्फेयर मेश) दोनों को सपोर्ट करता है
  - क्यूब मैप टेक्सचर्ड स्काई को सपोर्ट करता है
  - वास्तविक समय प्रक्रियात्मक रूप से उत्पन्न आकाश का समर्थन करता है (+ प्रक्रियात्मक बादल)
  - कोड की केवल 3 - 5 पंक्तियों के साथ एक सुंदर आकाश प्रस्तुत करें

* फोंग रेंडरर (वैकल्पिक)
  - आप इसे `#define CGL_EXCLUDE_PHONG_RENDERER` के माध्यम से अक्षम कर सकते हैं
  - यह है:
    - फोन पाइपलाइन -> यह शेडर डेटा और ग्लोबल इंजन डेटा रखने वाली पाइपलाइन है। उपलब्ध विकल्प हैं
      - ब्लिन सुधार को सक्षम/अक्षम करें
      - सक्षम/अक्षम गहराई परीक्षण
      - गामा सुधार को सक्षम/अक्षम करें
      - सेटअप परिवेश प्रकाश व्यवस्था
      - रोशनी जोड़ें/निकालें
    - फोंग लाइट -> यह 3 प्रकार की हो सकती है:
      - दिशात्मक -> यह लेता है (दिशा, रंग, तीव्रता)
      - बिंदु -> यह लेता है (स्थिति, रंग, तीव्रता, स्थिर, रैखिक, द्विघात)
      - स्पॉट (TODO)
    - फोंग सामग्री
      - बनावट/रंग का उपयोग न करें
      - स्पेक्युलर बनावट / रंग
      - चमक
      - सामान्य नक्शे (TODO)

* तिलमैप रेंडरर (वैकल्पिक)
  - आप इसे `#define CGL_EXCLUDE_TILEMAP_RENDERER` से अक्षम कर सकते हैं
  - कोड की एक पंक्ति के साथ एक NxN टाइलमैप प्रस्तुत करता है
  - प्रत्येक टाइल में निम्नलिखित अवस्थाएँ हो सकती हैं
    - स्पष्ट (पारदर्शी या अक्षम)
    - ठोस रंग
    - बनावट -> बनावट के माध्यम से आपूर्ति की जा सकती है:
      - बनावट 2d सरणी -> आपको प्रत्येक टाइल के लिए गहराई प्रदान करने की आवश्यकता है
      - टाइलसेट या बनावट एटलस -> आपको टाइल पर उपयोग किए जाने वाले अलास के क्षेत्र की सीमाएं (सामान्यीकृत 0.0-1.0) प्रदान करनी होंगी
    - नोट: यह टाइल रेंडर केवल 4 कोने प्रस्तुत करता है और इसमें केवल 1 ड्रॉ कॉल है (इंस्टेंस्ड कॉल नहीं है इसलिए यह काफी तेज़ है
    
  
## जिन चीजों पर काम किया जा रहा है:
 
  * PBR renderer (वैकल्पिक)
  * IBL (वैकल्पिक)
 
 ## शोरील
 


https://user-images.githubusercontent.com/73700725/211901867-8d2ddf87-13fa-4115-827a-3b43ed29b92d.mp4

https://user-images.githubusercontent.com/73700725/211902216-5fee0cff-f7db-4a3e-a16b-c4962d275d90.mp4

https://user-images.githubusercontent.com/73700725/211901919-d32778b1-7967-4749-b22d-ab95bab8d88e.mp4
 
https://user-images.githubusercontent.com/73700725/205131064-2ea36253-7976-4b02-bfdf-290b5a8e2171.mp4
 
https://user-images.githubusercontent.com/73700725/205130311-87cdddbb-e96f-412a-a9b5-96b2f474f6d1.mp4

https://user-images.githubusercontent.com/73700725/205130454-017992a5-f786-4b7e-b330-9046edbec25c.mp4

https://user-images.githubusercontent.com/73700725/205130582-8f6a4ce8-d932-402e-ad88-24a2e7d090b7.mp4

https://user-images.githubusercontent.com/73700725/208747347-6f0c0d49-c11c-4bf0-8497-82806e53974f.mp4




**अधिक जानकारी के लिए [उदाहरण](./examples) और [शोरील](./showreels) देखें**

<br>
