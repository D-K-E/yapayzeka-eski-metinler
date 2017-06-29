.. title: Makine Öğrenimine Hazırlık 2.1 Doğrusal Cebir 5
.. slug: makine-ogrenimine-hazirlik-21-dogrusal-cebir-5
.. date: 2017-06-20 03:33:17 UTC+02:00
.. tags: mathjax, doğrusal cebir, yapay-zeka, makine öğrenimi
.. category: 
.. link: 
.. description: 
.. type: text

Merhaba Arkadaşlar,

Makine Öğrenimine Hazırlık yazı dizisinin doğrusal bağımlılık ile ilgili son yazısıyla karşınızdayım
Bildiğiniz gibi bu yazı dizisini aslında makine öğreniminde ve daha sonrasında derin öğrenimde karşımıza çıkacak algoritmaların matematiksel temellerini anlayabilmemiz için yazıyorum.
Bir `önceki yazımda <https://d-k-e.github.io/yapayzeka-eski-metinler/posts/makine-ogrenimine-hazirlik-21-dogrusal-cebir-4/>`_ doğrusal bağımlılık konusunun anlaşılabilmesi için gerekli olan doğru denklemi ve doğru sistemi konularını ele almıştım.
Eğer makine öğrenimine yeni başlıyorsanız, bu yazı dizisinin `ilk bölümünden <https://d-k-e.github.io/yapayzeka-eski-metinler/posts/makine-ogrenimine-hazirlik-21-dogrusal-cebir-1/>`_ başlamanızı tavsiye ederim.
Eğer çok çok yeniyseniz ve "Makine Öğrenimi Nedir, Derin Öğrenim Nedir ?", gibi sorulara cevap bulmaya geldiyseniz, bunun için üç bölümlük bu konulara değinen `ilk yazı dizisini <https://d-k-e.github.io/yapayzeka-eski-metinler/posts/yapay-zeka-ve-derin-ogrenime-giris-1/>`_ tavsiye ederim.

Bu yazı, doğrusal bağımlılık konusunun ikinci ve son bölümünü oluşturuyor.
Temel sorumuz şuydu, :math:`Ak=u` denklem sistemi hangi durumlarda :math:`A^{-1}` ile çözülebilir ?
Ele alacağımız kavramlar şunlar:

- Doğrusal bileşim,
- Katsayı dizeyi

Ve en nihayetinde

- Doğrusal Bağımlılık
- Doğrusal Bağımsızlık



###########################
`Doğrusal Bağımlılık - 2`_
###########################


`Doğrusal Bileşim`_
-------------------

Bir doğru sistemini ifade eden denklemi düşünelim, :math:`Ak=u`.
Denklemde :math:`A{\in}{\mathbb{R}}^{mxp}`, A bir `dizey <https://d-k-e.github.io/yapayzeka-eski-metinler/posts/makine-ogrenimine-hazirlik-21-dogrusal-cebir-1/#dizeyler>`_; :math:`k{\in}{\mathbb{R}^m}`, k *bilinmeyen* bir `yöney <https://d-k-e.github.io/yapayzeka-eski-metinler/posts/makine-ogrenimine-hazirlik-21-dogrusal-cebir-1/#yoneyler>`_; :math:`u{\in}{\mathbb{R}^p}`, u *bilinen* bir yöneydir.

Doğrusal bileşim dediğimiz işlem aslında bir yöneyin bir dizey ile çarpılması eyleminin adıdır.
Matematiksel ifadesi şu şekilde:

.. math::

   A_{:,1}k_1 + {\dots} + A_{:,n}k_n 

Okunuşu kısaca A dizeyinin **sütunlarıyla** "k" yöneyinin elemanlarını çarpıyoruz.
Dolayısıyla aslında bütün ifade A dizeyinin sütunlarını oluşturan yöneylerin, k yöneyinin elemanlarını oluşturan sayıllarla çarpıldıktan sonra toplanmasını ifade ediyor.

Burada k yöneyinin elemanlarına *katsayılar* deniyor.

`Katsayı dizeyi`_
-------------------

Şu ikisini karıştırmamak lazım.
Doğrusal bileşim bağlamında "k" yöneyinin elemanlarına katsayılar deniyor, ancak `doğrusal denklem sistemi <https://d-k-e.github.io/yapayzeka-eski-metinler/posts/makine-ogrenimine-hazirlik-21-dogrusal-cebir-4/#dogru-denklem-sistemi>`_ bağlamında katsayı dizeyi, "A"'ya tekabül ediyor.
Somut olması için açık bir örnek vereyim:

.. math::
   
   4x + 5y - z = 0

   2x + y - z = 0

Bir önceki yazıdaki denklem sistemini ele alalım.
Bu sistem bağlamında, katsayı dizeyi G diyelim.
G dizeyini açık yazalım:

.. math::

   G = \left[
   \begin{array}{r,r,r}
   4, 5, -1 \\
   2, 1, -1 \\
   \end{array}
   \right]


Doğrusal bileşim bağlamında katsayıları oluşturan yöneye f diyelim.
f'yi açık yazalım:

.. math::

   f = \left(
   \begin{array}{r}
   x \\
   y \\
   z \\
   \end{array}
   \right)

Şimdi doğrusal bileşim bağlamında katsayıların neler olduğunu açıkça gördüğümüze göre, doğrusal bağımlılık ve bağımsızlıktan bahsetmeye başlayabiliriz.
Eğer doğrusal denklem sistemindeki katsayı dizeyini oluşturan sütunlarla çarpılacak yöney elemanlarından herhangi biri 0'dan başka bir sayıysa, katsayı dizeyinin sütunları **doğrusal bağımlılık** gösterirler.
Eğer çarpılacak yöney elemanlarının hepsi 0'a eşitse, katsayı dizeyinin sütunları **doğrusal bağımsızlık** gösterirler.

Doğrusal bağımsızlığın matematiksel ifadesi kolay anlaşılır.
Bu yüzden onu :math:`Ak=u` denklemi çerçevesinde veriyorum:

.. math::

   A_{:,1}k_1 + {\dots} + A_{:,n}k_n = 0

   k_i = 0

   {\forall}i = 1, {\dots}, n

Kısaca :math:`Ak=u` denklem sisteminde eğer "k"nın bütün elemanları 0'a eşitse, A dizeyinin sütunları birbirinden doğrusal olarak bağımsızdır.
Eğer "k"'nın bir tane elemanı bile 0'a eşit değilse, A dizeyinin sütunları birbirine doğrusal olarak bağımlıdır.

Neden ? Çünkü eğer "k" yöneyinin elemanlarından bir tanesi bile 0'a eşit değilse, A dizeyinin sütunlarından en azından biri, diğerinin doğrusal bileşimi demektir.
Neden ? Çünkü "k"'nın 0'a eşit olan elemanının çarpıldığı sütun ile, "k"'nın 0'a eşit olmayan elemanın çarpıldığı sütun arasında bir sayıl ile ifade edilebilecek bir ilişki var demektir.
Yukarıda tarifini verdiğimiz gibi yöney elemanlarını oluşturan sayılların sütun yöneyleriyle çarpımına doğrusal bileşim dendiği düşünülürse, "k"'nın ilgili elemanlarıyla çarpılan sütun yöneyleri doğrusal bileşim olarak yazılabilir.

Biraz soyut kaldığını tahmin ediyorum ama örnekle daha iyi anlaşılacak.

Yukarıdaki denklem sistemimizi ve ilgili çözümlerini alalım tekrar.
Ele aldığımız denklem sistemi doğrusal bağımlılığa bir örnek:

.. math::

   4x + 5y - z = 0

   2x + y - z = 0

   s^T = \left(
   \begin{array}{c}
   x \\
   y \\
   z \\
   \end{array}
   \right)
   
   s^T = \left(
   \begin{array}{c}
   -2 \\
   1 \\
   -3 \\
   \end{array}
   \right)


   G = \left[
   \begin{array}{c,c,c}
   4, 5, -1 \\
   2, 1, -1 \\
   \end{array}
   \right]

   G {\cdot} s = 0

   \left(
   \begin{array}{c}
   4 \\
   2 \\
   \end{array}
   \right){\times}-2 + 
   \left(
   \begin{array}{c}
   5 \\
   1 \\
   \end{array}
   \right){\times}1 +
   \left(
   \begin{array}{c}
   -1 \\
   -1 \\
   \end{array}
   \right){\times}-3 = 0

Durum buyken, doğrusal bağımlılık için şu soruyu soruyoruz "Acaba bir yöneyi diğerinin katı olarak yazabilir miyim ?" Yani hangi koşullarda:

.. math::

   G_{:,1}s_1 = G_{:,2}s_2

Geçerli bir ifadedir ? Buna verilen cevap, :math:`\{ s_1, s_2 \} \not = \{ 0,0 \}` gerek şartı sağlanıyorsa, ifade geçerli olabilir.
Neden ? Çünkü sütun yöneylerinin değerleri elveriyorsa bu ifade geçerli olacaktır.
Yukarıda verdiğim denklem sistemi, gerek şartı sağlıyor, olmasına rağmen bağımlılık şartını sağlamıyor. Görelim:

.. math::

   s_2 \not = 0 \Rightarrow G_{:,1} = G_{:,2}{\frac{s_1}{s_2}}

   s_1 \not = 0 \Rightarrow G_{:,1} = G_{:,2}{\frac{s_2}{s_1}}


Uygulanabiliyor mu görelim:

.. math::

   \left(
   \begin{array}{c}
   4 \\
   2 \\
   \end{array}
   \right){\times}-2 = ?
   \left(
   \begin{array}{c}
   5 \\
   1 \\
   \end{array}
   \right){\times}1

   \left(
   \begin{array}{c}
   4 \\
   2 \\
   \end{array}
   \right) \not = - \frac{1}{2} \left(
   \begin{array}{c}
   5 \\
   1 \\
   \end{array}
   \right)

Açıkça uygulanamıyor, o halde bir de uygulanabilen bir denklem sistemi görelim:

.. math::

   2x + 1y  = 0

   4x + 2y  = 0

   s^T = \left( x,y \right)

   s^T = \left( -1,2 \right)

   G = \left[
   \begin{array}{c,c,c}
   2, 1 \\
   4, 2 \\
   \end{array}
   \right]

   G {\cdot} s = 0

   \left(
   \begin{array}{c}
   2 \\
   4 \\
   \end{array}
   \right){\times} -1 + 
   \left(
   \begin{array}{c}
   1 \\
   2 \\
   \end{array}
   \right){\times}2 = 0

   G_{:,1}s_1 =? G_{:,2}s_2
  
   \left(
   \begin{array}{c}
   4 \\
   2 \\
   \end{array}
   \right){\times}1
   =? \left(
   \begin{array}{c}
   1 \\
   2 \\
   \end{array}
   \right){\times}2

   \left(
   \begin{array}{c}
   4 {\times}1 \\
   2 {\times}1  \\
   \end{array}
   \right)
   =? \left(
   \begin{array}{c}
   1 {\times}2  \\
   2 {\times}2  \\
   \end{array}
   \right)

   \left(
   \begin{array}{c}
   4 \\
   2 \\
   \end{array}
   \right) = \left(
   \begin{array}{c}
   4 \\
   2 \\
   \end{array}
   \right)

Görüldüğü üzere geçerlilik doğrulanıyor. O halde buradaki iki sütun yöneyi arasında doğrusal bir bağımlılıktan söz edebiliriz.
Burada konuyu dizeyler üzerinden anlatıyor olmamın sebebi makine öğreniminde genellikle dizeyler bağlamında kullanılıyor olmasında.
Özellikle ağırlık dizeyi denilen dizey üzerinde yapılan işlemlerde kilit bir kavram olacak.

Bu iki denklem sistemi arasındaki farkın gözle görülür olması için ikisinin de koordinat düzleminde nasıl gözüktüğünü görelim.

Doğrusal Bağımsız:

.. image:: /images/MÖ-Hazırlık-21/dogrusalBagimsiz.png


Doğrusal Bağımlı:

.. image:: /images/MÖ-Hazırlık-21/dogrusalBagimli.png


Verdiğim örneklerden de görüleceği üzere aslında doğrusal bağımlılık gösteren denklemleri niteleyen yöneyler, aynı doğrunun birer parçası, doğrusal bağımlılık *göstermeyen* denklemleri niteleyen yöneyler, kesişen ama aynı yönde olmayan doğrulara ait.

`Doğrusal Aralık`_
--------------------

Bu aslında ayrı bir başlık gerektirmeyen bir kavram.
Bir denklem sisteminin katsayı dizeyinin sütunlarını oluşturan yöneylerle yapılan doğrusal bileşimlerin tümüne **sütun alanı** denir.
Yer yer *doğrusal aralık*, ya da kısaca *aralık* olarak da ifade edilir.
Doğrusal aralık ifadesi genel olarak bir yöneyler kümesinin olası bütün doğrusal bileşimleri sonucuna denir.
Bizim ele aldığımız konu yalnızca katsayı dizeyinin sütunları bağlamında olduğunda *sütun alanı* ifadesi bana daha uygun görünüyor.
Aralık sözcüğü aslında durumu çok iyi karşılamıyor, yayılım, veya içerim daha iyi karşılıyor.
Bunu örneği verdikten sonra daha iyi göreceksiniz diye umuyorum.

Doğrusal Aralık için hızlıca bir örnek vereyim [1]_:

Diyelim ki Y bir yöney uzayı, A'da bu uzayın bir alt kümesi.
Eğer Y yöney uzayının her yöneyi, A'daki yöneylerin doğrusal bileşimi olarak yazılabiliyorsa, Y, A'nın doğrusal aralığındadır.
Matematiksel olarak ifade edecek olursak:

.. math::

   A \subset Y

   A = \{v_1, v_2, {\dots}, v_n \}

Eğer :math:`Y = c_1v_1 + c_2v_2 + {\dots} + c_nv_n` ise DAralık(A) = Y.

Örneğin :math:`v_1 = \{1, 0, 0 \}` ve :math:`v_2 = \{ 0, 1, 1 \}` yöneylerinin doğrusal aralığını görelim.

.. math::

   c_1v^{T}_1 + c_2v^{T}_2 = c_1 \left(
   \begin{array}{c}
   1 \\
   0 \\
   0 \\
   \end{array}
   \right) + \left(
   \begin{array}{c}
   0 \\
   1 \\
   1 \\
   \end{array}
   \right) = \left(
   \begin{array}{c}
   c_1 \\
   c_2 \\
   c_2 \\
   \end{array}
   \right)

Görüldüğü üzere :math:`v_1` ve :math:`v_2` yöneylerinin doğrusal aralığı :math:`{\mathbb{R}}^3` kümesindeki ikinci ve üçüncü elemanı aynı olan yöneylerin tamamını kapsar.
Neden ? Çünkü bu şartı sağlayan bütün yöneyleri :math:`v_1` ve :math:`v_2` doğrusal bileşimi ile ifade edebilirsiniz.
Örneğin :math:`v_5 = \{ 8, 10, 10 \}` yöneyini ele alalım.
Görüldüğü üzere yukarıdaki şartı sağlayan bir yöney.
Bu yöneyin nasıl :math:`v_1` ve :math:`v_2` doğrusal bileşimi ile ifade edildiğini görelim:

.. math::

   v_5^{T} = \left(
   \begin{array}{c}
   8 \\
   10 \\
   10 \\
   \end{array}
   \right) =  \left(
   \begin{array}{c}
   1 \\
   0 \\
   0 \\
   \end{array}
   \right) {\times} 8 + \left(
   \begin{array}{c}
   0 \\
   1 \\
   1 \\
   \end{array}
   \right) {\times} 10

Bu haliyle bakıldığında :math:`v_5` yöneyinin örnekteki doğrusal bileşimin şekliyle örtüştüğü görülüyor.


Bonus
#########

Ufak bir bonus olarak, grafikleri çizerken kullandığım kodu da burada paylaşıyorum:


.. code-block:: python

    import numpy as np  
    import matplotlib.pyplot as plt  
    def graph(formula, x_range):  
        x = np.array(x_range)  
        y = eval(formula)
        return x,y
    #
    # Doğrusal Bağımlı
    #
    graphX, graphY = graph('-2*x', range(4))
    plt.plot(graphX, graphY, label="Doğrusal bağımlı")
    plt.legend()
    plt.show()

    # Doğrusal Bağımsız
    #
    graphX1, graphY1 =graph('(-2*2*x +3)/-1', range(3))
    graphX, graphY = graph('(-2*4*x +3)/-5', range(3))
    plt.plot(graphX, graphY, label="Doğrusal Bağımsız 1")
    plt.plot(graphX1, graphY1, label="Doğrusal Bağımsız 2")
    plt.legend()
    plt.show()


Bu yazıyı burada bitiriyorum.
Bundan sonraki yazı şu zamana kadar anlata geldiğim kavramların tamamını barındırarak, yazının başında temel soru olarak addettiğim ve :math:`Ak=u` denklem sistemi hangi durumlarda :math:`A^{-1}` ile çözülebilir sorusuna bir yanıt vereceğim.
Sizin konuya eklemek istediğiniz bir şey varsa yorumlarda belirtin lütfen.

Sağlıcakla,

Kaan
           
Notlar
###############

.. [1] Örneği aldığım `site <http://math.bard.edu/belk/math213s14/LinearCombinationsAndSpanRevised.pdf>`_
