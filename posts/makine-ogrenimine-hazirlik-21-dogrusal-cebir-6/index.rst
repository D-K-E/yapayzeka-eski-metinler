.. title: Makine Öğrenimine Hazırlık 2.1 Doğrusal Cebir 6
.. slug: makine-ogrenimine-hazirlik-21-dogrusal-cebir-6
.. date: 2017-07-04 02:25:17 UTC+02:00
.. tags: mathjax, doğrusal cebir, yapay-zeka, makine öğrenimi
.. category: 
.. link: 
.. description: 
.. type: text

Merhaba Arkadaşlar,

.. contents::


Bu yazıda :math:`Ak=u` denklem sistemi hangi durumlarda :math:`A^{-1}` ile çözülebilir sorusuna bir yanıt vereceğim.
Bundan önceki yazılar boyunca, özellikle Doğrusal Cebir 3-5 arasında bu sorunun çözümünde kullanılacak kavramsal alt yapıyı vermeye çalıştım.
Bildiğiniz gibi bu yazı dizisini aslında makine öğreniminde ve daha sonrasında derin öğrenimde karşımıza çıkacak algoritmaların matematiksel temellerini anlayabilmemiz için yazıyorum.
Eğer makine öğrenimine yeni başlıyorsanız, bu yazı dizisinin `ilk bölümünden <https://d-k-e.github.io/yapayzeka-eski-metinler/posts/makine-ogrenimine-hazirlik-21-dogrusal-cebir-1/>`_ başlamanızı tavsiye ederim.
Eğer çok çok yeniyseniz ve "Makine Öğrenimi Nedir, Derin Öğrenim Nedir ?", gibi sorulara cevap bulmaya geldiyseniz, bunun için üç bölümlük bu konulara değinen `ilk yazı dizisini <https://d-k-e.github.io/yapayzeka-eski-metinler/posts/yapay-zeka-ve-derin-ogrenime-giris-1/>`_ tavsiye ederim.

Denklemimizdeki elemanları hatırlayalım: :math:`A{\in}{\mathbb{R}}^{mxp}`, A bir `dizey <https://d-k-e.github.io/yapayzeka-eski-metinler/posts/makine-ogrenimine-hazirlik-21-dogrusal-cebir-1/#dizeyler>`_; :math:`k{\in}{\mathbb{R}^p}`, k *bilinmeyen* bir `yöney <https://d-k-e.github.io/yapayzeka-eski-metinler/posts/makine-ogrenimine-hazirlik-21-dogrusal-cebir-1/#yoneyler>`_; :math:`u{\in}{\mathbb{R}^p}`, u *bilinen* bir yöneydir.
Kısaca "k"'nın değerini bulmaya çalışıyoruz.
Bunun için :math:`A^{-1}` ters dizeyini kullanarak şu çözüme gitmiştik:

.. math::

   Ak=u
   
   A^{-1}Ak = uA^{-1}

   I_nk=uA^{-1}

   k=uA^{-1}

Bu hatırlatmayı burada bırakalım.
Daha detaylı bir açıklama için, `buraya <https://d-k-e.github.io/yapayzeka-eski-metinler/posts/makine-ogrenimine-hazirlik-21-dogrusal-cebir-3/#ters-dizey>`_ bakabilirsiniz.

Burada "k"'nın bir çözümünün olması, "u"'nun, "k" ve "A"'nın çarpımından oluştuğu düşünülürse, A'nın `sütun alanında <https://d-k-e.github.io/yapayzeka-eski-metinler/posts/makine-ogrenimine-hazirlik-21-dogrusal-cebir-5/#dogrusal-aralik>`_  olmasına bağlıdır.
Bu durumda, yine aynı işlemde gerçekleştirilen `nokta çarpımı <https://d-k-e.github.io/yapayzeka-eski-metinler/posts/makine-ogrenimine-hazirlik-21-dogrusal-cebir-2/#yoney-carpimi>`_ dolayısıyla :math:`u{\in}{\mathbb{R}^m}` halini varsayar.
Kısaca "u" yöneyinin elemanları "A" dizeyinin katsayı yöneyi ile çarpılıp toplanmasından oluştuğundan ve katsayı yöneyi bilinmeyen olduğundan, "u"nun elemanlarının A yöneyinin satırlarının elemanlarının ait olduğu kümeye ait olması beklenir.
Katsayı yöneyinin bilinmeyen olması durumu, denklemin çözülebilmesi için "A"'nın sütun alanının :math:`{\mathbb{R}^m}` kümesini kapsamasını gerektirir, zira eğer herhangi bir nokta sütun alanından eksik ise "u" nun o nokta için alabileceği değerin çözümü yoktur.
Daha önceki yazılarımda dizey çarpımı işleminin nasıl yapıldığına değinmiştim, ama burada gözünüzde canlandıramadıysanız bir kere daha belirteyim.
A dizeyi ile "k" yöneyini çarpmak demek, A dizeyinin satırlarının her birinde bulunan elemanları "k" yöneyinin satıra denk gelen elemanıyla çarparak, dizey satırını kendi içinde toplamak demek olduğundan, bu işlem sonucu oluşacak "u" yöneyinin ilgili elemanının da A dizeyinin satırlarını kapsayan kümeye dahil olması beklenir, çünkü en nihayetinde yapılan şey A dizeyinin bir satırını katsayı yöneyinin sayıllarıyla çarpıp toplamak.

Şimdi, "m" A'nın satır sayısını temsil ettiğine göre, ve yukarıda belirttiğim :math:`u{\in}{\mathbb{R}^m}` durumu da geçerli olduğuna göre, şu göstergeyi de kabul etmek durumundayız, :math:`p {\ge} m`.
Neden ? Çünkü A dizeyinin k yöneyi ile çarpımı sonucu oluşacak olanın p sütun sayısına sahip olacağını dizey çarpımı işleminin yapısı gereği olduğunu biliyoruz.
Yine aynı şekilde eğer "u" yöneyinin elemanlarının :math:`{\mathbb{R}^m}` kümesine dahil olduklarını da biliyoruz.
O halde "p" "m"'den küçük olamaz, çünkü eğer olursa "u" yöneyinin elemanlarından biri A dizeyinin sütun alanın dışında kalır.
Bunun getireceği sonuç "u"'yöneyinin denklem sisteminin her bileşimi için sonucunun garanti olmaması olacaktır.

Ancak şunu biliyoruz, doğrusal bağımlılık gösteren yöneyler, aslında tek bir yöney ile temsil edilebiliyorlar.
Dolayısıyla sütun alanına yaptıkları bir etki yok. Bu şu demek, :math:`p {\ge} m` şartına bir de, bir veya daha fazla m boyutlu doğrusal bağımsızlık gösteren denklemler kümesi barındırmak eklendi.
Sorulabilecek makul soru şu, neden "p" "m"'den büyük olabiliyorken, barındırılabilecek bağımsız denklemler kümesi "m" üzerinden birimleniyor ?
Bunun sebebi şu, yukarıda belirttiğim gibi esasında :math:`p {\ge} m` bir gösterge, yani ilk elde baktığınızda size bir fikir verecek, kabaca eleme yapabilmenizi sağlayacak bir belirti.
Doğrusal bağımlılık söz konusu olduğunda bu göstergenin işlememesi riski var, çünkü elinizdeki denklem sisteminde her ne kadar :math:`p {\ge} m` tutuyor olsa da bağımlı denklemler tek bir denklem olarak temsil edilebildiği için :math:`p {\le} m` riski var.
Bu riskin oluşmaması için kontrol etmemiz gereken, A dizeyinin sütun alanının "m" boyutunda bir bağımsız denklemler kümesini barındırıp barındırmadığı.
"m" boytundaki bir denklemler kümesinin "m" taneden daha fazla bağımsız denkleme sahip olamayacağı düşünülürse, zira hiçbir denklem bir diğeri cinsinden yazılamayacaktır, A dizeyinin u yöneyi bağlamında yukarıdaki şartları sağlayabilmesi için, m üzerinden birimlenen bir bağımsız denklemler kümesini barındırması gerektiği aşikardır.
Kaç tane "m" kadar barındıracağı sorun değil, ancak bir veya daha fazla "m" boyutlu küme barındırması şart.

Sorumuzun diğer ayağına gelelim, :math:`Ak=u` denklem sistemini :math:`A^{-1}` ile çözmeye çalıştığımı yazmıştım.
Ters dizeyi bir önceki yazılardan hatırlayanlar, onun düzüyle çarpıldığında birim dizeyi verdiğini hatırlayacaklardır.
Birim dizeyin temel şartı olan kendisiyle çarpılanı değiştirmeme özelliğinin temel dayanağı olan kare şeklinde olmayı, yani satır sayısının sütun sayısına eşit olmasını da hatırlayalım.
Bu bağlamda belki de en başta söylememiz gereken en bariz olgu şuydu, A dizeyi eğer ters dizey ile çözülebiliyorsa, kare şeklindedir, yani :math:`p {\ge} m` filan demeye gerek kalmadan, baştan :math:`p = m` olmak durumundadır arkadaşlar da diyebilirdim.
Takip ettiğim kaynak [1]_ bunu bu şekilde sunmuyor, yani bunu başta sunmuyor ki iyi de yapıyor aslında, çünkü mantıken denklemin kendisinin çözülebilme şartlarının denklemin bir yöntemle çözülebilme şartına öncelenmesi gerekir.

O halde soruya tam yanıt verelim.

Soru şuydu:

- :math:`Ak=u` denklem sistemi hangi durumlarda :math:`A^{-1}` ile çözülebilir ?

Cevabıysa şu:

- Eğer A'nın satır ve sütun sayısı birbirine eşitse ve sütunlarını oluşturan yöneyler doğrusal bağımsızlık şartını sağlıyorsa, :math:`Ak=u` denklem sistemi :math:`A^{-1}` ile çözülebilir.


Bu yazıyı burada bitiriyorum.
Doğrusal Cebir üzerine olan yazı dizisinin bir sonraki yazısı, yöney normları, üzerine olacak.
Eklemek istediğiniz bir şey varsa, ya da daha iyi açıklanmasını talep ettiğiniz bir şey lütfen yorumlarda belirtin.

Sağlıcakla,

Kaan

.. deep learning p., 38


.. [1] Kaynağı önceki yazılarımda sıkça belirttim. Goodfellow I.,Y. Bengio, Deep Learning, Cambridge, 2016.
