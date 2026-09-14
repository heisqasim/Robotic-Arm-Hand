# خريطة الطريق المشتركة - نسخة مبسطة للجانب الطبي / البايوميديكال

هدف المشروع هو الوصول إلى **V1 قابلة للاستخدام فعلياً** لشخص فاقد اليد عند مستوى قريب من الرسغ، مع بقاء معظم الساعد. التسمية الطبية الدقيقة لمستوى البتر يجب أن تتأكد سريرياً، لكن هندسياً هذه الحالة تعطي مساحة عضلية جيدة للـ EMG وتفرض علينا بالمقابل أن تكون الوصلة والـ socket قصيرة جداً حتى لا تصبح اليد الصناعية أطول من الطبيعي.

## الفكرة الأساسية

اليد المقترحة تحتوي على 3 مجموعات actuation:

- محرك مستقل للـ index
- محرك يحرك middle + ring + little عن طريق adaptive differential
- محرك مستقل للـ thumb

الأصابع tendon-driven، والرجوع يكون بواسطة springs / elastic elements. الهدف هو Power / Pinch / Tripod / Hook بموثوقية أعلى وتعقيد أقل من يد فيها محرك لكل إصبع.

## التحكم

نبدأ بـ 2-channel surface EMG:

- flexor -> close
- extensor -> open
- grip selector واضح لتغيير نمط القبض

Machine learning مو شرط حتى V1 تشتغل. LibEMG والـ pattern recognition يجيان بعد ما direct control يصير ثابت.

## دور الجانب الطبي / البايوميديكال

المهام الأساسية:

- تحديد anatomy ومستوى البتر
- خرائط الجلد والندبات والمناطق الحساسة
- اختيار مواقع EMG مع مختص مناسب
- متطلبات الـ socket والراحة والضغط
- تقييم fit و don/doff
- ملاحظة أي skin response أو discomfort
- تقييم الوظائف اليومية المفيدة للشخص

## التسلسل العام

1. نثبت القياسات والـ scan والمهام اليومية المطلوبة.
2. نبني finger واحد ونجرب tendon + motor + joints.
3. نضيف differential والـ thumb ونثبت palm architecture.
4. نبني bench hand كاملة قبل ربطها بالشخص.
5. نضيف electronics + safety limits.
6. نضيف 2-channel EMG direct control.
7. نصمم socket/adapter على أساس scan + قياسات + ملاحظات طبية.
8. ندمج wearable V1 ونختبرها تدريجياً وتحت إشراف مناسب.
9. بعد reliability نضيف sweat/heat/water hardening.
10. لاحقاً Jarvis يصير engineering workspace للـ 3D scans و CAD revisions و digital twin.

## تعريف النجاح

V1 ناجحة عندما الشخص يقدر، باختبار supervised، يفتح ويغلق اليد بقصد واضح، يمسك أغراض يومية، يستخدم Power/Pinch/Tripod/Hook، يحرر الجسم بسرعة، يلبس الـ socket بدون أذى جلدي غير مقبول، وما تكون هناك حرارة أو نقاط pinch أو أخطار كهربائية واضحة.

## ملاحظة مهمة

الـ 3D scan يعطينا geometry فقط. ما يحدد وحده مناطق الضغط الآمنة، لذلك fitting النهائي يحتاج تقييم طبي/أطراف صناعية مناسب.

ولا تُرفع صور الشخص أو الـ scans أو معلوماته الطبية إلى هذا الـ public repository.