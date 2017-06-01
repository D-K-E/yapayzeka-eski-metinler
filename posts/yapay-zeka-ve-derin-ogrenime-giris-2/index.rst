.. title: Yapay Zeka ve Derin Öğrenime Giriş 1.2
.. slug: yapay-zeka-ve-derin-ogrenime-giris-2
.. date: 2017-05-26 04:49:35 UTC+02:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text
   
Yapay Zeka ve Derin Öğrenime Giriş - 1.2
########################################

Merhaba Arkadaşlar,

Daha `önceki yazımda <https://d-k-e.github.io/yapayzeka-eski-metinler/posts/yapay-zeka-ve-derin-ogrenime-giris-1/>`_, yapay zeka çalışmalarında Derin Öğrenime gelene kadar kullanılagelmiş yöntem ve yaklaşımların kısa bir özetini yapmıştım. En son gelinen noktada, makine öğrenimi için gereken temsilde nitelik oluşturma zorunluluğuna kırmızı ışıkta geçen arabaların plakasını yakalamak problemi üzerinden değinmiştim.


Aynı örnek üzerinden devam edecek olursak, nitelikleri üretmenin/ayrıştırmanın *en doğru* veya *en geçerli* yolu yok. Ne özelliği yakalamanızı sağlıyorsa o geçerli, doğru yol, ancak şu var, el ile bu nitelikleri yaratmak çok vakit isteyen bir şey.
Elimizdeki örnek için elle ilgili niteliği kurgulamaya çalışsak, plakayı oluşturması muhtemel imgecik serilerini, kameranın aracı resmin kaçta kaçına taşıdığına göre, plakanın büyüklüğünün sabit olduğu düşünülürse, plakanın resimde olabileceği alanlarda, eşleştirmeye çalışırdık.
Böyle deyince çok zor duyulmuyor olabilir, özellikle bilgisayarla görüş alanındaki kütüphanelerin çokluğu düşünülürse, ancak şunu belirtmek zorundayım 'plakayı oluşturması muhtemel imgecik serileri' ifadesini el ile oluşturmak mümkün değil, zira temsilinizi değiştiren çok fazla özellik dışı etmen var.
Örneğin, yazın güneş tam kameranın arkasından vurdu, plakanın beyazı parladı bazı harfler silüet gibi görünüyor, veya kırsal alan, araba çamura girmiş plakanın bir kısmına çamur bulaşmış, veya kamyonun kasası plakaya gölge ediyor, bu yüzden plaka tam beyaz gibi gözükmüyor, vs gibi özelliğe dair olmayan bir sürü etmen özelliği değiştiriyor. Dolayısıyla, özelliğin temsili de beklenen değerlerde olmuyor.

*Temsil Öğrenimi* [1]_ ya da diğer adıyla *Nitelik Öğrenimi* denen yaklaşım, bu soruna çare bulmaya çalışıyor.
Bu yaklaşımı temsilin temsillerini üretmek gibi de düşünebilirsiniz.
Örneğin, elimizdeki ışıkta geçen araba resmine bakalım. Resim, bir imgecikler bütün dedik.
Bu imgecikler bütününü örneğin aynı değere sahip olanların koordinat düzlemindeki pozisyonları kümesi olarak da temsil edebiliriz.
Bu bir çeşit veri çerçevesi olacaktır. Çerçevenin sütunları imgecik değerleri, satırları da bir koordinat noktaları olacaktır.
Kullanılan imgecik değerlerinin yayılma aralığını verir.
Tek başına bu bile resmin içinde bulunduğu şartlara dair önemli tiyolar barındıracaktır.
Resim daha sonrasında koordinatlar sütun, imgecik değerleri satır olarak temsil edilebilir.
Bu sütunlar plakanın standard büyüklüğüne göre gruplanıp, benzer değerlerde seyreden satırların uzunluğuna bakılarak, plakanın bulunduğu koordinatlar saptanabilir, zira plakanın beyaz başladığı düşünülürse, koordinatlar değişse bile imgeciklerin değerleri belirli bir aralıkta seyredecektir. Yani bu olması beklenen şey.
Yukarıda belirttiğim gibi özellik dışı etmenler, işlerin bu kadar düzgün yürümemesi sağlayacaktır, ancak şu önemli, buraya kadar tarif ettiğim her şey bir makine tarafından yapılabilir.
Yapması gereken tek şey, ham maddeyi çeşitli temsillere dönüştürmek ve bu temsillerde tekrar eden kalıpları yakalamak. Bu çok katmanlı bir temsil grubu olarak kurgulanabilir.

Bu çok katmanlı temsil grubunu oluşturmakta kullanılan tipik algoritma, otomatik kodlayıcılardır [2]_.
Yukarıda tarif ettiğim şablonda otomatik kodlayıcılar temsiller arası geçişleri sağlayanlardır.
Genellikle çift yönlüdürler. Kabaca bir kodlayıcı ve bir de çözücü içerirler.
Kodlayıcı gelen girdiyi bir başka temsile dönüştürür, çözücü de yeni oluşan temsili kodlayıcıya geldiği haline dönüştürür.
Genelde kodlayıcılar belirli niteliklileri oluşturacak şekilde alıştırılırlar.
Burada temel amaç tabi değişiklik unsurlarını [3]_ yakalamak.
Bu unsurlar, temsilde gözlemlenen olgunun ayrıştırıcı özelliklerine tekabül ederler.
Ayrıştırıcı özellikler, temelde bir varlığı diğer varlıktan ayırmamızı veya onunla gruplamamızı sağlayanlar.
Bundan çok acayip şeyler anlamaya gerek yok, örneğin masanın ayrıştırıcı özelliği nedir, ya da onu üzerindeki lambadan nasıl ayırıyoruz ?
Masanın dört ayağı var, düz bir yüzeyi var, vs, lambanın yuvarlak bir tabanı ve bir kablosu var, vs.
Bu ve bunlar gibi özellikler masayı lambadan ayırmamızı sağlayan unsurlar.
Temsil üzerinde bu unsurları yakalamak, yapay zekanın gerçek dünya da iş yapabilmesinin temel gerekliliklerinden biri.

Sorun şu, gerçek dünyadaki gözlemlenenlerin çok fazla ayrıştırıcı özelliği var, dahası bir sürü gözlemlenenin ayrıştırıcı özelliği başka gözlemlenenlerin ayışrtırıcı özellikleriyle etkileşime giriyor.
Bu karşılıklı etkileşim hali, bize değişiklik unsurlarının birbirinden ayrılmasını zorunlu kılıyor.
İnsan bu ayrımı otomatik olarak yapıyor, örneğin ışığın üzerine vurduğu açı değiştiği zaman, insan masanın masa olarak kalmaya devam ettiğinin ayırdına varabiliyor, ancak baktığın şeyin ne olduğundan habersiz makineler için bu durumun bir garantisi yok.
Dolayısıyla bilgisayarlar için masanın masa olarak temsilde belirmesini sağlayan değişiklik unsurlarının, masaya vuran ışığın değişiklik unsurlarından ayrılabilmesi gerekli.
Bu temsil öğreniminin derin öğrenim yöntemleri olmaksızın tıkandığı noktalardan biri, zira bu iki değişiklik unsurunu birbirinden ayıracak olanın saptanması temsile dair neredeyse insan düzeyinde bir anlamayı varsayıyor.
Masanın üstüne vuran ışık örneğinden gidecek olursak, mevcut durumda masanın üstüne vuran ışıktan ayrıştırılabilmesi için, masayı oluşturan imgeciklerin ışık değiştikçe nasıl değer değiştirdiklerini biliyor olmamız lazım.
Örnek izole edildiğinde yapılabilir gözükse de, gerçek dünyadaki, masanın üstünde duran başka şeyler olabileceği, ışığın örneğin doğrudan değilde başka bir objeye vurarak masaya yansıdığı vs gibi durumlar düşünüldüğünde nitelik öğreniminin unsurlar arasında bir hiyerarşi kurmaksızın, bahsettiğim soruna çözüm getirebilmesi mümkün gözükmüyor.


Bu yazıyı burada noktalıyorum. Bir `sonraki yazı <https://d-k-e.github.io/yapayzeka-eski-metinler/posts/yapay-zeka-ve-derin-ogrenime-giris-13/>`_ giriş bölümünün son yazısı olacak. O yazıda *Derin Öğrenimin* bahsettiğim kavramlarla olan ilişkisine, ve *derinliğin* nereden geldiğine değineceğim. Son olarak da model derinliğinin ölçülmesinde kullanılan yöntemlerden kısaca bahsedeceğim.

Sağlıcakla,

Kaan

.. Sayfa 5 deep learning bölümünde kaldın devam et oradan


===========
Terimler
===========


.. [1] Temsil Öğrenimi: Ham verinin temsilinde özelliği ayrıştıracak niteliği elle oluşturmaktansa, makinenin bu nitelikleri oluşturması süreci.
.. [2] Otomatik Kodlayıcılar: Genelde Kodlayıcı ve Çözücüden oluşan, temsilden nitelikli temsiller türetmeye ve türetilen temsillerden önceki hallerine dönmeye yarayan algoritmaların genel adı.
.. [3] Değişiklik unsurları: Bu unsurlar, gözlemlenenin gözlemlendiği halini oluşturduğu kabul edilen etmenler. Örneğin bir araba plakasının değişiklik unsurları, siyahlık, beyazlık, köşeli olmak, düz çizgili olmak, eğrilere sahip olmak, vs gibidir. 

