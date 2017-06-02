.. title: Makine Öğrenimine Hazırlık 2.1: Doğrusal Cebir- 1.1: Terimler
.. slug: makine-ogrenimine-hazirlik-21-dogrusal-cebir-1
.. date: 2017-05-30 01:53:12 UTC+02:00
.. tags: mathjax, dizey, sayıl, gerey, yöney, makine öğrenimi
.. category: yapay-zeka
.. link: 
.. description: 
.. type: text

Merhaba arkadaşlar,

Bundan önceki, Derin Öğrenime Giriş `yazı dizisinde <https://d-k-e.github.io/yapayzeka-eski-metinler/posts/yapay-zeka-ve-derin-ogrenime-giris-1/>`_, çok kabaca derin öğrenimin ne olduğundan, ne tip modeller kullandığından, ilgilendiği problemlerden ve bu problemlere sunduğu çözümlerden bahsettim.
Bu yazı dizisini ise Derin Öğrenim algoritmalarını açıklarken kullanacağım matematiksel alt yapıya ayırdım.
Bu alt yapının ilk ayağı hiç kuşkusuz doğrusal cebir. Doğrusal cebiri üniversitede görmeseler de liseden hatırlayanlar olacaktır.
Koordinat sistemi x,y filan deyince aklınıza gelen şey.
Bu yazı tabi ki doğrusal cebir ilgili bilinen her şeyi anlatmaya filan çalışmayacak, derin öğrenim ve daha genel anlamda makine öğreniminde kullanıldığı kadarını sizlerle paylaşmaya çalışacağım.

Şimdi ağırlıklı olarak kullanacağımız terimler şunlar: sayıllar, dizeyler, yöneyler, gereyler.
Bu terimlerin her birini en ufak detayına kadar uzun uzun anlatacağım, zira ne ifade ettiklerini tam olarak bilmek şart.

========
Sayıllar
========

Sayıl, bir adet sayıdır. Böyle deyince garip duyuluyor, ancak bunun dışında göreceğimiz diğer terimler genellikle daha karmaşık kümelerden oluşuyorlar.
Sayıl öyle değil, bildiğimiz normal 3,4,7 filan gibi bir sayı.
Genellikle hangi sayı kümesine ait olduğu da belirtilir.
Örneğin Sayıl "a" :math:`s \in \mathbb{N}` yani s elemanıdır doğal sayılar kümesinin.
Nerede işimize yarıyacak ?
Yöneylerin arasındaki açı ilişkilerini incelerken, bir dizeyi bir başka dizeye dönüştürürken, vs.
Özellikle temel bileşen analizi gibi algoritmalarda özyöneyleri incelerken bu sayıl terimi anahtar kavramlardan biri olacak.
Daha doğrusu ben bu terimi bildiğinizi varsayarak algoritmayı açıklayacağım.

=========
Yöneyler
=========

Yöneyler, adının da belirttiği gibi, yönü ve büyüklüğü olanlar.
Bunlar genellikle *belirli bir referans noktasına göre*, ki bu genelde kolaylık olsun diye (0,0) kabul edilir, başka bir noktada olan noktalardır.
Referans noktasıyla, tayin ettikleri nokta arasındaki mesafe onların büyüklüğünü oluşturur.
Yöneyin, yönünüyse eksenlerle yaptıkları açılara göre söylenir. Örnek verecek olursak:

.. image:: /images/MÖ-Hazırlık-21/yöneyÖrneği.png


[2]_
Resimdeki "a" yöneyimizin *vardığı* dolayısıyla onu tayin eden noktayı belirtiyor.
63° olarak belirtilen yöneyin yönü.
Doğru olarak çizilen alansa yöneyin büyüklüğünü temsil ediyor.

Yöneyler açık olarak ifade edildiklerinde genelde şu şekilde yazılırlar.
Diyelim ki elimizde bir "a" yöneyi olsun :math:`a = [a_1, a_2, a_3,{\dots}, a_n ]`.
"a"'nın altına yazılanlar elemanların numarası, yani a yöneyinin birinci elemanı, ikinci elemanı, gibi.
Bazı kitaplarda A noktasından B noktasına doğru olan bir yöney için :math:`\vec{AB}` gibi ifadeler de kullanılıyor.
Bazen yöneyi dikine yazdıklarını da gördüm. Örneğin:

.. math::

   a = \left[
   \begin{array}{r}
    a_1 \\
    a_2 \\
    a_3 \\
    \vdots \\
    a_n
    \end{array}
   \right]

Yöneylerin dizinlenmesinde kullanılan bir takım uzlaşımlar var.
Örneğin, yöneyin ikinci, beşinci ve yirmi sekizinci elemanlarını ayırmak istersek, bunun için başta bu eleman numaralarının olduğu bir küme oluşturuyoruz.
Örneğin "k" kümesi, yani :math:`k = \{{2, 5, 28\}}`.
Sonrasında da bu kümenin adını tıpkı diğer elemanları ifade ederken kullandığımız gibi yöneyin adının altına koyuyoruz, yani :math:`a_k`.
Hariç olan elemanları kast ettiğimizde eksi işaretini kullanıyoruz.
Örneğin ikinci elemanlar hariç, yöneyin bütün elemanları gibi bir ifade, şöyle oluyor :math:`a_{-2}`.
"k" kümesine dahil olmayan elemanların hepsi gibi ifadeler de yine benzer bir şekilde :math:`a_{-k}` ifade ediliyor.

.. yöneylerin dizinlenmesi sayfa 32, resmi küçült renklerini değiştir

=========
Dizeyler
=========

Dizeyler bayağı meşhur, filmini bile çektiler. İsminden anlaşılacağı üzere yatay ve dikey dizilerden oluşan, dolayısıyla iki boyutlu, sayı dizinidir.
Genellikle boyutları y x d ifadesiyle verilir.
Bu ifade y, satıra, d sütun olarak okunur [1]_.
Örneğin 23 satırlı ve 4 sütunlu bir K dizeyi için kullanılan ifade şudur: :math:`K^{23x4}`

Dizeyler ve onlarla ilgili işlemler Makine Öğreniminde çok sık kullanılıyor, bundan dolayıdır ki numpy, scipy filan gibi kütüphaneler, dizey işlemlerini eniyilemek için bir hayli uğraşıyorlar.
Dizeydeki bir elemanı ifade etmek istediğimizde onun satır ve sütun numarasını veririz

- Örneğin :math:`K_{12,2}` ifadesi K dizeyinin 12. satırı üzerinde 3. sütunun altına denk gelen elemanı ifade etmektedir.

Bir **satırdaki** elemanların tamamını ifade etmek istediğimiz zaman sütun numarası yerine ":" koyulur.

- Örneğin :math:`K_{3,:}` ifadesi K dizeyinin 3. satırındaki bütün elemanları ifade eder.

Bir **sütundaki** elemanların tamamını ifade etmek istediğimiz zaman satır numarası yerine ":" koyulur.

- Örneğin :math:`K_{:,3}` ifadesi K dizeyinin 3. sütunundaki bütün elemanları ifade eder.

Bazı durumlarda dizeyde erişmek istediğimiz elemanlar bir ifadenin sonucudurlar.
İfadeden kastım, 3'ün katı olan satırların 2.sinden 3. sütuna tekabül eden eleman gibi şeyler.
Bunlar genelde :math:`f(K)_{y,d}` şeklinde temsil edilir.
Bu ifade şu şekilde okunur, K dizeyine f işlemini yap, oradaki satır ve sütunu al.
f işleminden kastım, yukarıdaki 3'ün katı filan muhabbeti gibi olan ifadeler.
Tam öyle olmak zorunda değil tabi ama ona benzer dizey değerlendirmesi yapan ifadeler.

Sıklıkla bahsedeceğimiz dizey işlemleri şunlar: dizey toplamı, sayıl çarpımı, dizey çaprazlama, dizey çarpımı.


=========
Gereyler
=========

Gereyler aslında dizeyler gibi, sadece çok boyutlular.
Nasıl K dizeyindeki bir elemanı tayin etmek için eksenler üzerindeki konumunu K'nin altına yazıyorduk, gereylerde de benzer bir sistem var.
Örneğin 7 boyutlu, yani eksenli bir G gereyindeki elemanı belirtmek için şöyle bir ifade kullanırız :math:`G_{j,o,r,m,v,r,x}`, tabi burada j, o, r, m, v, ve x'in, sayma sayıları kümesinin elemanı olduğunu kabul ediyoruz.


Bu yazıyı burada bitiriyorum.
Gördüğümüz matematiksel kavramlar bundan sonrası için temel teşkil ediyor.
Bir sonraki yazıda bunlarla yapılan işlemleri anlatmaya çalışacağım.
Anlaşılmayan bir şey varsa, ya da eklemek istediğiniz bir şey varsa lütfen yorumlarda belirtin.

Sağlıcakla,

Kaan


#############
Notlar
#############

.. [1] y, yi yatay, d'yi dikey gibi de okuyabilirsiniz, yani yataya dikey.

.. [2] Resimin temeli Jakob Scholbach'a aittir, üzerindeki değişiklikler bana ait, `orjinali <https://en.wikipedia.org/wiki/Vector_space#/media/File:Vector_components.svg>`_. 

