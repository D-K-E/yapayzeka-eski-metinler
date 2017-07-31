.. title: Makine Öğrenimine Hazırlık 2.1 Doğrusal Cebir 3: Birim Dizeyi Ters Dizey
.. slug: makine-ogrenimine-hazirlik-21-dogrusal-cebir-3
.. date: 2017-06-09 03:39:11 UTC+02:00
.. tags: dizey, makine öğrenimi, mathjax
.. category: yapay-zeka
.. link: 
.. description: 
.. type: text

Merhaba Arkadaşlar,

.. contents::


Makine Öğrenimine Hazırlık yazı dizisinin bir başka yazısıyla karşınızdayım.
Bu yazı dizisini makine öğreniminde ve daha sonrasında derin öğrenimde karşımıza çıkacak algoritmaların matematiksel temellerini anlayabilmemiz için yazıyorum.
Bir `önceki yazımda <https://d-k-e.github.io/yapayzeka-eski-metinler/posts/makine-ogrenimine-hazirlik-21-dogrusal-cebir-2/>`_ makine öğrenimi algoritmalarının sıklıkla kullandığı işlemleri dile getirmiştim.
Eğer makine öğrenimine yeni başlıyorsanız, bu yazı dizisinin `ilk bölümünden <https://d-k-e.github.io/yapayzeka-eski-metinler/posts/makine-ogrenimine-hazirlik-21-dogrusal-cebir-1/>`_ başlamanızı tavsiye ederim.
Eğer çok çok yeniyseniz ve "Makine Öğrenimi Nedir, Derin Öğrenim Nedir ?", gibi sorulara cevap bulmaya geldiyseniz, bunun için üç bölümlük bu konulara değinen `ilk yazı dizisini <https://d-k-e.github.io/yapayzeka-eski-metinler/posts/yapay-zeka-ve-derin-ogrenime-giris-1/>`_ tavsiye ederim.

Bu yazımda aslında bir önceki yazıda vermiş olduğum :math:`Ak=u` denklemine değineceğim.
Denklemde :math:`A{\in}{\mathbb{R}}^{mxp}`, A bir `dizey <https://d-k-e.github.io/yapayzeka-eski-metinler/posts/makine-ogrenimine-hazirlik-21-dogrusal-cebir-1/#dizeyler>`_; :math:`k{\in}{\mathbb{R}^p}`, k *bilinmeyen* bir `yöney <https://d-k-e.github.io/yapayzeka-eski-metinler/posts/makine-ogrenimine-hazirlik-21-dogrusal-cebir-1/#yoneyler>`_; :math:`u{\in}{\mathbb{R}^p}`, u *bilinen* bir yöneydir.

Bu denklemin çözümü için inceleyeceğimiz konu başlıkları şunlar:

- Birim Dizeyi
- Ters Dizey

----------------
`Birim Dizeyi`_
----------------

Kabaca Birim Dizeyi bir yöneyle çarpıldığında o yöneyde bir değişiklik yaratmayan dizeydir. Bunu daha matematiksel bir biçimde ifade etmek istersek:

.. math::
   \forall x \in \mathbb{R}^n, I_n x = x

Yani her gerçek sayılar kümesi elemanı olan x değeri, n boyutlu birim dizeyi ile çarpıldığında sonuç olarak kendisini verir.
Neye benziyor ? Örneğin, :math:`I_4`, yani normal dizey gibi yazarsak :math:`I_{4x4}` birim dizeyi şuna benziyor:

.. math::
   \left[
   \begin{array}{r,r,r,r}
   1 & 0 & 0 & 0 \\
   0 & 1 & 0 & 0 \\
   0 & 0 & 1 & 0 \\
   0 & 0 & 0 & 1 \\
   \end{array}
   \right]

Dikkat edilmesi gereken noktalar şunlar:

- Yalnızca ana çapraz üzerinde 1 değeri var gerisi 0.
- Şekil olarak bir kare, yani **satır sayısı sütun sayısına eşit**.

---------------
`Ters Dizey`_
---------------

Birim dizeyini gördükten sonra ters dizeyi anlamak çok kolay.
Herhangi bir Y dizeyinin ters dizeyi, kendisiyle çarpıldığında [1]_ birim dizeyi verendir.
Matematiksel ifadesi şu:

.. math::

   Y^{-1} {\times} Y = I_n

Burada gördüğümüz :math:`Y^{-1}` ifadesi ters dizeyi gösteriyor, yani Y dizeyinin ters dizeyini gösteriyor.
Örnek verecek olursak [2]_:

.. math::

   A = \left[
   \begin{array}{r,r}
   4 & 3 \\
   3 & 2 \\
   \end{array}
   \right]
   
   A^{-1} = \left[
   \begin{array}{r,r}
   -2 & 3 \\
   3 & -4 \\
   \end{array}
   \right]

   AA^{-1} = \left[
   \begin{array}{r,r}
   4 & 3 \\
   3 & 2 \\
   \end{array}
   \right]
   \left[
   \begin{array}{r,r}
   -2 & 3 \\
   3 & -4 \\
   \end{array}
   \right] = \left[
   \begin{array}{r,r}
   1 & 0 \\
   0 & 1 \\
   \end{array}
   \right]

Dikkat edilmesi gereken noktalar şunlar:

- Sonucunda birim dizey elde ettiğimize göre hem Y hem de :math:`Y^{-1}` kare şeklinde, yani satır sayıları sütun sayılarına eşit.

Şu an ki bilgilerimizle yazının başındaki denklemi çözmeye muktediriz.

.. math::

   Ak=u
   
   A^{-1}Ak = uA^{-1}

   I_nk=uA^{-1}

   k=uA^{-1}

Adım adım açıklayacak olursak:

1. Denklemin kendisi.
2. Denklemin iki tarafını da A dizeyinin tersiyle çarptık.
3. A dizeyini tersiyle çarpınca sol tarafta birim dizeyi elde ettik.
4. Birim dizeyin yöneyle çarpımı yöneyin kendisini verdi, yani bilinmeyen k yöneyinin, bilinen u yöneyinin A'nın ters dizeyi ile çarpımına eşit olduğunu gördük.

Burada şu soru açığa çıktı ? :math:`A^{-1}` hesaplanabilir bir dizey mi ?
İzlediğim kitap [3]_ burada :math:`A^{-1}` aslen teorik işlevi olduğunu ve pratik hesaplamalar için "u" üzerinden işleyen algoritmaların daha isabetli sonuçlar aldığını belirtiyor.
Bunun sebebiyse bilgisayarların dizeyleri temsil etme konusunda bazen yeterince isabetli temsiller üretemediklerini vurguluyor.

Bu yazıyı burada bitiriyorum. Farkındayım biraz kısa oldu, ancak bundan sonra değineceğim doğrusal bağımlılık konusu biraz meşakatli.
Kendi başına bir yazı olmayı hayli hayli hak ediyor.
Eklemek istediğiniz bir şey varsa, ya da anlamadığınız bir şey varsa, yorumlarda belirtmekten çekinmeyin lütfen.

Sağlıcakla,

Kaan


Notlar
*******

.. [1] Dizey çarpımının nasıl yapıldığını görmek için, bir önceki yazıdaki `ilgili bölüme <https://d-k-e.github.io/yapayzeka-eski-metinler/posts/makine-ogrenimine-hazirlik-21-dogrusal-cebir-2/#dizey-carpimi>`_ bakınız.

.. [2] İlgili örnek, `şuradan <http://www.mathwords.com/i/inverse_of_a_matrix.htm>`_ alınmıştır.

.. [3] Bu kitabın referansını ilk yazı dizisinin ilk yazısında vermiştim, bir daha vereyim. Goodfellow I.,Y. Bengio, Deep Learning, Cambridge, 2016. Kitap internette var.


