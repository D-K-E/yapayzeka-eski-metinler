.. title: Makine Öğrenimine Hazırlık 2.1 Doğrusal Cebir 2: Sık Kullanılan İşlemler
.. slug: makine-ogrenimine-hazirlik-21-dogrusal-cebir-2
.. date: 2017-06-03 02:06:51 UTC+02:00
.. tags: mathjax, dizey, sayıl, gerey, yöney, makine öğrenimi
.. category: 
.. link: 
.. description: 
.. type: text


Merhaba Arkadaşlar,

Bir `önceki yazımda <https://d-k-e.github.io/yapayzeka-eski-metinler/posts/makine-ogrenimine-hazirlik-21-dogrusal-cebir-1/>`_, makine öğrenimi ve derin öğrenimde sık kullanılan algoritmalarda geçen matematiksel kavramların kısa bir özetini vermiştim.
Yine o yazıda belirttiğim gibi, bu yazıyı o kavramlarla yapılan işlemlere ayıracağım. Örnekleri bol tutmaya özen göstereceğim.


`Yöney İşlemleri`_
###################

`Yöney Çaprazlama`_
---------------------

Çaprazlama işlemi, dizeyler için daha kullanışlı bir yapı olsa da yöneyleri temsil ederken de yer yer kullanılır.
Yöneyler tek sütunlu dizeyler olarak görülebildiklerinden, bir yöneyin çaprazlanmış hali de tek sütunlu bir dizeydir.
Bu bağlamda şu ifadeyle yer yer karşılaşırız :math:`x = [x_1, x_2, x_3]^T`.
Dizeyler için geçerli olan işlemlerin hemen hepsi yöneyler içinde yapılabilir.

`Yöney Çarpımı`_
------------------
Bu işlemin iki türü var:

1. Nokta çarpımı
2. Çapraz çarpım.

Derin Öğrenim ve makine öğrenimi bağlamında gereken doğrusal cebir için bunlardan bilmemiz gereken **nokta çarpımı**
Onunda formülü basit, x ve p iki yöney olsun:

.. math::

   p {\cdot} x = {\sum_{j=1}^{n} p_j {\times} x_j = p_1 {\times} x_1 + p_2 {\times} x_2 + {\dots} + p_n {\times} x_n}

Yani işlemin sonucu bir `sayıl <https://d-k-e.github.io/yapayzeka-eski-metinler/posts/makine-ogrenimine-hazirlik-21-dogrusal-cebir-1/#sayillar>`_.
Bir örnek verecek olursak:

.. math::

   p = [1,3]

   x = [3,4]

   p {\cdot} x = 1 {\times} 3 + 3 {\times} 4 = 15

Bu değer ne ifade ediyor. Elde edilen sayılın ifade ettiği şey, yöneylerin arasındaki açı ilişkisi.
Bunu biraz açmadan önce nokta çarpımının ne yaptığını anlamaya çalışalım, yani bizden iki yöney arasında ne ilişkisi kurmamızı istediğini anlamaya çalılaşım.

Öncelikle neden bu işlem bize bir yöney değilde bir sayıl veriyor ? Bunun sebebi yöneylerin dizeyler düzeyinde bir soyutlaması yapıldığında yani yöneyler dizeyler cinsinden ifade edildiğinde, yapılan dizey çarpımının sonucunun 1 satırlı ve 1 sütunlu olmak durumunda kalmasından ileri geliyor.
Dizey çarpımlarının matematiksel ifadesini birazdan daha dikkatle detaylı inceleyeceğim ama kısadan şunu koyayım: :math:`\vec{p}^T = p^{1x0}` ve :math:`\vec{x} = x^{0x1}` dizey çarpımlarında :math:`H^{mxq} = K^{mxn} {\times} R^{jxq}` olduğundan dolayı yani çarpım sonucu oluşan dizey çarpılandan satır sayısı, çarpandan da sütun sayısı aldığından dolayı :math:`z^{1x1} = p^{1x0} {\times} x^{0x1}` olur, yani iki yöneyden devşirme dizey arasındaki çarpımın ancak ve ancak 1 satırı ve 1 sütunu olabilir. Bir satırı ve bir sütunu olan dizeyde zaten bir sayıldır.

Bu sayıl yöneylere dair ne söylüyor ?    
Bu sayılın değerlerine göre yöneylerin arasındaki açıya dair şunlar söylenebilir:

- Eğer sayılın değeri > 0 ise iki yöney arasındaki açı 90 dereceden küçüktür.
- Eğer sayılın değeri = 0 ise iki yöney arasındaki açı 90 derecedir.
- Eğer sayılın değeri < 0 ise iki yöney arasındaki açı 90 dereceden büyüktür.
    
Akla gelen en makul soru şu tabi, neden ?
Bunu hissettirmeye çalışacağım, zira matematiksel ispatını tek başına vermemin çok bir anlamı yok.
İlgili formül şu :math:`\vec{p} {\cdot} \vec{x} = |{\vec{p}}| {\times} |{\vec{x}}| {\times}{\cos}{\theta}`.
Yani Öklid düzlemindeki iki yöneyin nokta çarpımı, onların büyüklüklerinin ve aralarındaki açının kosünüsünün çarpımına eşittir.
`Wikipedia'nın ilgili sayfasına <https://en.wikipedia.org/wiki/Dot_product>`_ baktığınızda verdiğim iki formülün birbirine denk olduğunu göreceksiniz.
Oradaki ispat anlaşılır olmakla beraber konuya yabancı olanların terimlerde zorlanma ihtimali muhtemel.

Şunu hissederseniz nokta çarpımının neyi ifade ettiğini anlarsınız.
Normal çarpım, sizi aynı sayı doğrusu üzerinde ilerletiyor, yani örneğin sadece koordinat düzleminin "x" ya da "y" ekseni üzerinde oynuyorsunuz.
Nokta çarpımında ise her iki eksen üzerinde de kendisini gösteren varlıkların birbirine teması söz konusu.
Somut bir örnek verecek olursak.
Sahilde havlunuzun üstünde oturuyorsunuz, arkanızda da plajın şemsiyesi duruyor. Güneşte tam tepeden vuruyor.
Şemsiyenin üstünüze vuran gölgesinin başlayıp bittiği bir yer var.
Örneğin şemsiyenin gölgesi, başınızda başlıyor, göbeğinizde bitiyor.
Bu gölge, şemsiyenin sizle yaptığı açı değiştikçe değişecektir.
Nokta çarpımının bize sonuç olarak sunduğu sayıl, işte bu gölgenin bedeniniz üzerinde nerede bittiği.
Bu yüzdendir ki nokta çarpımı aynı zamanda bir yöneyin diğer yöneye öklid düzleminde geometrik izdüşümünü verir.

Peki çarpım diye ifade edilen bir işlem niye tutup bize geometrik izdüşümünü veriyor, iki yöney arasındaki ?
Niye bu işlem toplamanın tekrar edilmesi cinsinden tanımlanan çarpım işleminin adını taşıyor, onunla hiçbir alakası yok gibi gözükürken ?
Bunlar makul sorular.
Nokta çarpımında bir eklemenin potansiyeli var, yani bu çarpım sonucu şunu diyoruz, bir yöney eğer diğer yöney üzerinde olsaydı ona şu kadar eklerdi.
Diğer yöneye eklenecek yöneyin ne kadar diğer yöneyle farazi bir çakışmaya elverişli olduğunu da aralarındaki açı belirliyor.
Tıpkı şemsiye örneğinde olduğu gibi. Genel olarak sezdirme yönü kuvvetli bir açıklamaya `şuradan <https://betterexplained.com/articles/vector-calculus-understanding-the-dot-product/>`_ erişebilirsiniz. Daha anlaşılmayan noktalar varsa yorumlara yazın ben açıklamaya çalışırım.




`Dizey İşlemleri`_
###################

`Dizey Toplamı`_
-----------------

Dizey toplamı, iki aynı sayıda satıra ve sütuna sahip olan dizeyler arasında gerçekleşir.
İki dizeyinde aynı şekilde olması önemli, zira toplama işlemi eleman başına yapılır, yani
D ve M iki dizey olsun :math:`D^{2x3} + M^{2x3} = H^{2x3}` aslında şunu ifade eder.

.. math::

   D + M = \left[
   \begin{array}{r,r,r}
   D_{1,1} + M_{1,1}, & D_{1,2} + M_{1,2}, & D_{1,3} + M_{1,3} \\
   D_{2,1} + M_{2,1}, & D_{2,2} + M_{2,2}, & D_{2,3} + M_{2,3} \\
   \end{array}
   \right] = H

Görüldüğü üzere iki dizeyde aynı yerde bulunan elemanlar birbirleriyle toplanırlar.
Oldukça basit bir işlem kısaca.

Eğer toplananlar bir dizey ve bir yöney olsaydı. Örneğin D dizeyi ile p yöneyini toplasaydık, yani durum :math:`R = D + p` olsaydı.
Ortaya "p"nin *yayımlanması* denilen olay ortaya çıkardı. Bu da şu demek:
:math:`R = D + p` aslında :math:`R_{i,j} = D_{i,j} + p_j` demek olduğundan, yani diyelim ki :math:`p = [1, 4]^T` ve D'de yukarıdaki gibi :math:`D^{2x3}`, dolayısıyla toplama işleminin ifade ettiği şey şu:

.. math::
   D = \left[
   \begin{array}{r,r,r}
   D_{1,1} + 1,  & D_{1,2} + 1, & D_{1,3} + 1 \\
   D_{2,1} + 4, & D_{2,2} + 4, & D_{2,3} + 4 \\
   \end{array}
   \right]

Yani yöneyin elemanları dizeyin denk gelen satırlarına ekleniyor.
Buna derin öğrenim jargonunda *yayımlama* deniyor.
Kanımca, Türkçe'de gerçekleşen durumu çok iyi tarif etmeyen bir sözcük.
Durumu daha iyi ifade eden sözcük bence *sirayet etmek*, zira gerçekleşen işlemde yöneyin elemanları dizeyin satırlarına sirayet ediyor.

`Dizey Çaprazlama`_
--------------------

Bir dizeyin ana çaprazından geçtiği var sayılan çizgi üzerinden elemanların yerini bu çizgiye olan mesafeyi koruyacak şekilde çizginin öteki tarafındaki noktaya geçmesi, yani simetrik görüntüsünün alınmasıyla yeni bir dizey oluşturur.
Matematiksel ifadesi şudur :math:`(A^T)_{i,j} = A_{i,j}` T işareti ilgili dizeyin çaprazlanma sonucu ortaya çıktığını gösteriyor.
Akılda kalıcı olması açısından T'nin İngilizce, 'transpose' teriminin yerini tuttuğunu düşünebiliriz.

:math:`A^{2x3}` dizeyi için açık bir örnek verecek olursak,

.. math::

   A = \left[
   \begin{array}{r,r,r}
   A_{1,1},  & A_{1,2}, & A_{1,3} \\
   A_{2,1}, & A_{2,2}, & A_{2,3} \\
   \end{array}
   \right]
   
   A^T = \left[
   \begin{array}{r,r}
   A_{1,1}, & A_{1,2} \\
   A_{2,1}, & A_{2,2} \\
   A_{3,1}, & A_{3,2} \\
   \end{array}
   \right]

Yine aynı ışıkla baktığımızda :math:`(A^T)^T = A` oldğunu da görebiliriz.

`Dizey Çarpımı`_
------------------

Bu temelde yöneylerde yaptığımız nokta çarpımı işlemi gibi işliyor. İki dizey çarpıldığında ortaya bir yeni bir dizey çıkıyor. Bu yeni dizey, çarpılandan satır, çarpandan sütun alıyor.
Örneğin :math:`A^{2x3}`, :math:`E^{3x4}` dizeyleri çarpıldığında, ortaya çıkan sonuç  :math:`AE = Y^{2x4}` şekline sahip oluyor.
Dikkat edilmesi gereken bir başka nokta da A dizeyinin **sütun** sayısının E dizeyinin **satır** sayısına eşit olduğu.
Bu dizeyler arası çarpım işlemi yapılabilmesi için temel şart. Çarpma işleminin tam formülü ise şu:

.. math::

   Y_{i,j} = {\sum_{k} A_{i,k}E_{k,j}}

Örnek bir çarpma işlemi yapalım:

.. math::
   A^{2x3} = \left[
   \begin{array}{r,r,r}
   2, & 3, & 1 \\
   1, & 0, & 4 \\
   \end{array}
   \right]

   E^{3x4} = \left[
   \begin{array}{r,r,r,r}
   3, & 1, & 0, & 2 \\
   1, & 0, & 4, & 1 \\
   2, & 3, & 1, & 0 \\
   \end{array}
   \right]

   AE = Y^{2x4} = \left[
   \begin{array}{r,r,r,r}
   11 = 3{\times}2 + 1{\times}3 + 2{\times}1, & 5 = 2{\times}1 + 0{\times}3 + 3{\times}1, & 13 = 0{\times}2 + 4{\times}3 + 1{\times}1, & 7=2{\times}2 + 1{\times}3 + 0{\times}1 \\
   11, & 13, & 4, & 2 \\
   \end{array}
   \right]

Dizeyler sayıllarla da çarpılabilirler. Böyle bir durumda dizeyin her elemanı sayılla çarpılır. Örneğin

.. math::

   A^{2x3} = \left[
   \begin{array}{r,r,r}
   2, & 3, & 1 \\
   1, & 0, & 4 \\
   \end{array}
   \right]

   A {\times} 2 = \left[
   \begin{array}{r,r,r}
   2{\times} 2, & 3{\times} 2, & 1{\times} 2 \\
   1{\times} 2, & 0{\times} 2, & 4{\times} 2 \\
   \end{array}
   \right]

Dizey çarpımlarında şu özellikler bulunur:

Dağılma Özelliği
    :math:`R (A + C) = RA + RC`

Birleşme Özelliği
    :math:`R(AC) = (RA)C`

Normal çarpmanın aksine dizey çarpımında değişme özelliği yoktur, yani :math:`RA{\not =}AR`
Dizey çarpımının çaprazlanması ise şunu verir :math:`(AR)^T=A^TR^T` 

Şimdilik bu kadar yeter.
Bundan sonraki yazımda, şu denklemin çözülmesi için gereken işlemleri inceleyeceğim :math:`Ak=u`.
Denklemde :math:`A{\in}{\mathbb{R}}^{mxp}`, A bir dizey; :math:`k{\in}{\mathbb{R}^m}`, k *bilinmeyen* bir yöney; :math:`u{\in}{\mathbb{R}^p}`, u *bilinen* bir yöneydir.
Neden bu denklemle uğraşacağız sorusunun cevabı ise basit.
Bu denklem aslında doğrusal sınıflandırıcının kullandığı ana şemayı oluşturur.
Doğrusal sınıflandırıcı da makine öğreniminde, ve özellikle derin öğrenimde bir hayli kullanılan bir algoritma.
Anlaşılmayan bir şey varsa veya belirtmek istediğiniz bir şey varsa, yorumlarda belirtin lütfen.

Sağlıcakla,

Kaan
