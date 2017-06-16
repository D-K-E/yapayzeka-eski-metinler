.. title: Makine Öğrenimine Hazırlık 2.1 Doğrusal Cebir 4
.. slug: makine-ogrenimine-hazirlik-21-dogrusal-cebir-4
.. date: 2017-06-12 23:07:43 UTC+02:00
.. tags: mathjax, yapay-zeka, doğrusal cebir
.. category: 
.. link: 
.. description: 
.. type: text

Merhaba Arkadaşlar

Makine Öğrenimine Hazırlık yazı dizisinin bir başka yazısı.
Bu yazı dizisini makine öğreniminde ve daha sonrasında derin öğrenimde karşımıza çıkacak algoritmaların matematiksel temellerini anlayabilmemiz için yazıyorum.
Bir `önceki yazımda <https://d-k-e.github.io/yapayzeka-eski-metinler/posts/makine-ogrenimine-hazirlik-21-dogrusal-cebir-3/>`_ özellikle doğrusal sınıflayıcıların temeli niteliğindeki :math:`Ak=u` denklemini çözmeye yarayan matematiksel kavramlar olan ters dizey ve birim dizeyini açıklamıştım.
Eğer makine öğrenimine yeni başlıyorsanız, bu yazı dizisinin `ilk bölümünden <https://d-k-e.github.io/yapayzeka-eski-metinler/posts/makine-ogrenimine-hazirlik-21-dogrusal-cebir-1/>`_ başlamanızı tavsiye ederim.
Eğer çok çok yeniyseniz ve "Makine Öğrenimi Nedir, Derin Öğrenim Nedir ?", gibi sorulara cevap bulmaya geldiyseniz, bunun için üç bölümlük bu konulara değinen `ilk yazı dizisini <https://d-k-e.github.io/yapayzeka-eski-metinler/posts/yapay-zeka-ve-derin-ogrenime-giris-1/>`_ tavsiye ederim.

Bu yazı boyunca temelde Doğrusal Bağımlılık konusuna değinmek için gereken bir kaç kavrama değineceğim.

- Doğrusal Bağımlılık
  - Doğru denklemi
  - Doğru denklem sistemi

Bunlar ana hattı belirliyor olmakla beraber aralarda yeni terimlere ve konulara baş vuracağız.
Neden bu konulardan bahsedeceğiz ?
Çünkü bir önceki yazıda ters dizey ve birim dizeyi aracılığıyla çözdüğümüz, yukarıda da belirttiğimiz denklemi.

---------------------------
`Doğrusal Bağımlılık - 1`_
---------------------------

Bir `önceki yazıda <https://d-k-e.github.io/yapayzeka-eski-metinler/posts/makine-ogrenimine-hazirlik-21-dogrusal-cebir-3/>`_ :math:`A^{-1}` için sorduğum soru kenarda dursun.
Bu bölümde bu soruya yaklaşımımızı etkileyecek önemli bir dizi kavramı açıklamaya çalışacağım.
Doğrusal bağımlılığın ne olduğunu anlayabilmemiz bilmemiz gereken ilk şey, bir doğru denkleminin ne olduğu.

Doğru denklemi, koordinat düzlemi üzerindeki bir doğruyu ifade eden denklemdir. Genel formülü şudur:

.. math::

   A_{i,:}k=u_i

Tanıdık değil mi. Yukarıdaki denkleme çok benziyor. Bir örnek verecek olursak.
Diyelim ki A, 2x2 bir dizey, "k" 2 satırlı bir yöney, "u" da 2 satırlı bir yöney:

.. math::

   A = \left[
   \begin{array}{r,r}
   3 & 4 \\
   2 & 3 \\
   \end{array}
   \right]

   k = \left(
   \begin{array}{r}
   x \\
   y \\
   \end{array}
   \right)

   u = \left(
   \begin{array}{r}
   2 \\
   1 \\
   \end{array}
   \right)

Verdiğimiz örnekler ışığında, bir doğrunun denklemi şu olacaktır:

.. math::

   3x + 4y = 2

Doğru denklem sistemi ise birden fazla doğrudan oluşan ve aynı değişken yöneyini kullanandır.
Değişken yöneyinden kastım, yukarıdaki örnekteki "k" gibi, doğru denklemine değişkenlerini veren yöney.
Bu sistemler genelde :math:`Ak=u` şeklinde ifade edilirler.
Dikkat edilmesi gereken noktaysa, eğer :math:`A^{mxp}` ve :math:`k^{1xp}` ise :math:`u^{1xm}` olacaktır.
Bu genellemeyi açık yazacak olursak:

.. math::

   A_{1,1}k_1 + \dots + A_{1,p}k_p = u_1
   
   A_{2,1}k_1 + \dots + A_{2,p}k_p = u_2

   \vdots

   A_{m,1}k_1 + \dots + A_{m,p}k_p = u_m
   
Bir doğru denklem sisteminin **türdeş** olması demek, "u" yöneyinin bütün elemanlarının 0 olması demektir.
Türdeş doğru sistemlerinin hep *en az bir* çözümü vardır.
En az bir çözüm şartını sağlayan denklemlerin başında k yöneyinin sadece 0'lardan oluşması hali gelir.
Bu çözüme **apaçık çözüm** denir.
Sistemdeki denklemlerden birinin çözümünü sağlayan ve sadece 0'lardan oluşmayan "k" yöneyinin sağladığı çözüme ise **apaçık olmayan** çözüm denir.
Örneğin elinizde şöyle bir sistem olsun:

.. math::
   
   4x + 5y - z = 0

   2x + y - z = 0

Bu denklemi çözmek için yapmamız gereken şey basit.
İkinci denklemi - 2 ile çarpıp birinci denkleme eklemek.
Bunun sonucunda elde edeceğimiz denklemse şu olacaktır:

.. math::

   3y + z = 0

İşin anlaşılması biraz güç, daha doğrusu niye yapıldığını anlamak biraz güç olan noktası burada.
Bu denklemdeki değişkenlerden birine 0'dan büyük bir değer veriyoruz. Neden ? Daha doğrusu neden 0'dan büyük keyfi bir değer vermemiz
herhangi bir problem yaratmıyor ?
Sebebi şu: Bir doğru denklem sistemi, kendisini dönüştüren eşitleme işlemlerinde sonuç kümesini muhafaza eder.

Bunun ispatı biraz uzun ve doğrusal cebir işlemlerinden ziyade kümelerin özellikleriyle alakalı, ama karmaşık değil.
Ben burada işi tam yapmış olmak adına ispatı vereceğim [1]_ .

1. Doğru denklem sistemleri aslında birer denklem kümesi olduğundan, bu kümeye ait olan denklemlerin sırası, denklemleri çözen sonuçlar kümesini değiştirmiyor.

2. :math:`{\alpha} \not = 0` diyelim.

   1. Elimizdeki :math:`Ak=u` sistemindeki, "i" denklemini :math:`{\alpha}` ile çarpalım.

      - Anlaşılır olması için sistemi açık yazıyorum.

        .. math::

           A_{1,1}k_1 + \dots + A_{1,p}k_p = u_1
           
           A_{2,1}k_1 + \dots + A_{2,p}k_p = u_2

           \vdots

           {\alpha}A_{i,1}k_1 + \dots {\alpha}A_{i,p}k_p = {\alpha}u_i

           A_{m,1}k_1 + \dots + A_{m,p}k_p = u_m

   2. S bu doğru sisteminin çözüm kümesi olsun, T de :math:`\alpha` ile çarpım sonucu dönüşmüş sistemin sonuç kümesi olsun.

      1. :math:`(k_1, k_2, k_3, \dots, k_p) = (f_1, f_2, f_3, \dots, f_p) \in S`. Yani "k" ve "f" eşit yöneyler.
      2. Dolayısıyla :math:`{\alpha}A_{i,1}f_1 + \dots {\alpha}A_{i,p}f_p = {\alpha}u_i` geçerlidir.
      3. Dolayısıyla :math:`(f_1, f_2, f_3, \dots, f_p) \in T`
      4. O halde :math:`S \subset T`.

   3. S bu doğru sisteminin çözüm kümesi olsun, T de :math:`\alpha` ile çarpım sonucu dönüşmüş sistemin sonuç kümesi olsun.

      1. :math:`(k_1, k_2, k_3, \dots, k_p) = (f_1, f_2, f_3, \dots, f_p) \in T`. Yani "k" ve "f" eşit yöneyler.
      2. Dolayısıyla :math:`T_i = \{ {\alpha}A_{i,1}f_1 + \dots {\alpha}A_{i,p}f_p = {\alpha}u_i \}` geçerlidir.
      3. :math:`\alpha \not = 0` olduğundan dolayı, :math:`\frac{1}{\alpha}T_i`, geçerli bir sonuç verecektir.

         - Açık yazacak olursam:

         .. math::

            {\frac{1}{\alpha}}{\alpha}A_{i,1}k_1 + \dots {\frac{1}{\alpha}}{\alpha}A_{i,p}k_p = {\frac{1}{\alpha}}{\alpha}u_i

         - Bu işlem geçerlidir.

      4. O halde :math:`T \subset S`.
      5. İki kümenin birbirine eşit olmasının şartı böylelikle sağlanmış oluyor.

İspatın birinci ayağını bitirmiş olduk.
İlk dikkatimizi çekmesi gereken şey, eğer :math:`\alpha = 0` olsaydı, 1. ayağın 3. maddesini iddia edemezdik, zira :math:`\frac{1}{0}` ile karşılaşma imkanımız olurdu.


3. :math:`\alpha` herhangi bir karmaşık sayı olsun.

   1. Elimizdeki :math:`Ak=u` sistemindeki, "i" denklemini :math:`{\alpha}` ile çarpıp, "j" denklemine ekleyelim.

      - Açık yazacak olursam:

      .. math::

         A_{1,1}k_1 + \dots + A_{1,p}k_p = u_1

         A_{2,1}k_1 + \dots + A_{2,p}k_p = u_2

         \vdots

         ({\alpha}A_{i,1} + A_{j,1})k_1 + \dots ({\alpha}A_{i,p} + A_{j,p})k_p = {\alpha}u_i + u_j

         A_{m,1}k_1 + \dots + A_{m,p}k_p = u_m

   2. S bu doğru sisteminin çözüm kümesi olsun, T dönüşmüş sistemin sonuç kümesi olsun.

      1. :math:`(k_1, k_2, k_3, \dots, k_p) = (f_1, f_2, f_3, \dots, f_p) \in S`. Yani "k" ve "f" eşit yöneyler.
      2. :math:`T_j` açık yazılınca şu görülecektir:

         .. math::

            ({\alpha}A_{i,1} + A_{j,1})f_1 + \dots + ({\alpha}A_{i,p} + A_{j,p})f_p = {\alpha}u_i + u_j
            
            ({\alpha}A_{i,1}f_1 + \dots + {\alpha}A_{i,p}f_p) + (A_{j,1}f_1 + \dots + A_{j,p}f_p) = {\alpha}u_i + u_j

            {\alpha}(A_{i,1}f_1 + \dots + A_{i,p}f_p) + (A_{j,1}f_1 + \dots + A_{j,p}f_p) = {\alpha}u_i + u_j

            {\alpha}u_i + u_j = {\alpha}u_i + u_j

      3. Dolayısıyla :math:`(f_1, f_2, f_3, \dots, f_p) \in T`
      4. O halde :math:`S \subset T`.

   3. S bu doğru sisteminin çözüm kümesi olsun, T de :math:`\alpha` dönüşmüş sistemin sonuç kümesi olsun.

      1. :math:`(k_1, k_2, k_3, \dots, k_p) = (f_1, f_2, f_3, \dots, f_p) \in T`. Yani "k" ve "f" eşit yöneyler.
      2. :math:`T_j` açık yazılınca şu görülecektir:

         .. math::

            A_{j,1}f_1 + \dots + A_{j,p}f_p = A_{j,1}f_1 + \dots + A_{j,p}f_p + {\alpha}u_i - {\alpha}u_i

            A_{j,1}f_1 + \dots + A_{j,p}f_p = A_{j,1}f_1 + \dots + A_{j,p}f_p + {\alpha}(A_{i,1}f_1 + \dots + A_{i,p}f_p) - {\alpha}u_i

            A_{j,1}f_1 + \dots + A_{j,p}f_p = A_{j,1}f_1 + {\alpha}A_{i,1}f_1 + \dots + A_{j,p}f_p + {\alpha}A_{i,p}f_p - {\alpha}u_i

            A_{j,1}f_1 + \dots + A_{j,p}f_p = f_1(A_{j,1} + {\alpha}A_{i,1} ) + \dots + f_p(A_{i,p} + {\alpha}A_{i,p}) - {\alpha}u_i

            A_{j,1}f_1 + \dots + A_{j,p}f_p = {\alpha}u_i + u_j - {\alpha}u_i

            A_{j,1}f_1 + \dots + A_{j,p}f_p =  u_j 

      3. Dolayısıyla :math:`(f_1, f_2, f_3, \dots, f_p) \in S`
      4. O halde :math:`T \subset S`.
      5. İki kümenin birbirine eşit olmasının şartı böylelikle sağlanmış oluyor.

Neden ispatın ikinci ayağında :math:`\alpha \not = 0` şartını aramadık ?
Bu sorunun cevabı aslında 3.3.2 bölümündeki işlem dizisinden anlaşılıyor.
:math:`\alpha` değeri bu işlem dizisi boyunca bir önem teşkil etmiyor, zira kendisiyle herhangi bir işlem yapılmıyor.
Çarpma işleminin özellikleri çerçevesinde ifadenin tekrar yazılması sonucu, :math:`\alpha` konum değiştiriyor o kadar.

Bu ispat ışığında yukarıda verdiğim denklem sisteminin çözümü sırasında kullandığım metodun meşruluğu görülüyor.
Denklemlerin birbirine eklenmesi ve onların 0'dan büyük sayılarla çarpılması çözüm kümesini yani "k" yöneyinin elemanlarını
değiştirmediğine göre, ve aradığım çözüm kümesinin tek şartı **apaçık olmamak** olduğuna göre, denklemi çözmemizi sağlayacak ilk değerin sadece bu şartları sağlaması, denklem sisteminin çözülmesi için yeter neden teşkil eder.
Örneği çözerek bunu göstereyim:

.. math::
   
   4x + 5y - z = 0

   2x + y - z = 0

   -2(2x + y - z) = 0

   4x -4x + 5y - 2y + (-z + 2z) = 0

   3y + z = 0

Diyelim ki :math:`z=-3`:

.. math::

   3y - 3 = 0

   y = 1

O halde:

.. math::

   2x + 1 - (-3) = 0

   2x + 4 = 0

   x = -2

Peki bu değerler, ilk denklemi sağlıyorlar mı ? Görelim:

.. math::

   4(-2) + 5(1) - (-3) = 0

   -8 + 5 + 3 = 0

   8 - 8 = 0

   0 = 0

Bu ispat ve onun uygulamasıyla bu yazıyı bitiriyorum.
Doğrusal Bağımlılık konusunun ikinci bölümünde, doğrusal bileşim, katsayı dizeyi, ve en nihayetinde doğrusal bağımlılık ve doğrusal bağımsızlık
konularını ele alarak, iki yazı boyunca süre gelmiş olan, :math:`A^{-1}` hesaplanabilir bir dizey mi, ya da hangi bağlamlarda açığa çıktığını varsaymak yanlış olmaz sorusuna bir cevap vermeye çalışacağım.

Sağlıcakla,

Kaan

Notlar
#######

.. [1] İspatı aldığım `kaynak <http://linear.ups.edu/html/section-SSLE.html>`_ .
