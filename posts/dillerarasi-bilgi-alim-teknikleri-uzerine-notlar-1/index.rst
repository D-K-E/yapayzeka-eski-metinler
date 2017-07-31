.. title: Dillerarası Bilgi Alım Teknikleri Üzerine Notlar - 1
.. slug: dillerarasi-bilgi-alim-teknikleri-uzerine-notlar-1
.. date: 2017-07-17 14:48:38 UTC+02:00
.. tags: yapay-zeka, bilgi-alım, mathjax
.. category: 
.. link: 
.. description: 
.. type: text


Merhaba Arkadaşlar,

.. contents::
   
Bu yazı dizisinde dillerarası bilgi alım tekniklerine değineceğim. Kullandığım temel kaynak: Nie, Jian-Yun, Cross-Language Information Retrieval, Synthesis Lectures in Human Language Technologies, 8 (2010).
Internette kendisini bulmak mümkün.

Önce konuya bir giriş niteliğinde olması için genel bilgi alım yöntemlerinin uygulama alanları, karşılaşılan sorunlar ve bu sorunlara cevap niteliğinde gelen modellerden bahsedeceğim.

######################################
`Bilgi Alımda Karşılaşılan Sorunlar`_
######################################

Bilgi alım yöntemleri, adı üstünde, ulaşmak istediğiniz bilgiyi size sunmaya çalışır.
Sayısal ortamda gerçekleştirilen bir bilgi alım sürecinin kabaca iki ana unsuru var:

- Bilgi ihtiyacını temsil eden
- Bilgi ihtiyacına cevap veren

Bu ikisinin ne olduğu ve aralarındaki ilişkinin nasıl kurulduğu, daha doğrusu ne olduğuna bağlı olarak nasıl kurulduğu, bilgi alımda yöntemlerinin temel uygulama alanlarını ve ilgilendiği sorunları oluşturuyor.

Bir bilgi alım problemi örneği verelim:

Diyelim sevdiğiniz bir müzisyenin örneğin Emiltan Erten'in ya da Müşfik Can Müftüoğlunun bir parçasını dinlemek istediniz.
Ya da tatildesiniz, örneğin Kaş'ta, ve dalış yapmak istiyorsunuz, sizinle dalan hocanın adı aklınızda, Anıl Bozkırlı, tekne de aklınızda naturablue, ama teknenin kalkış saatlerini hatırlamıyorsunuz.
Elinizde parçanın adı var, müzisyenin adı var. İşte bunar bilgi ihtiyacınızı temsil edenler, dinlemek istediğiniz parçaysa bilgi ihtiyacınıza cevap veren, ya da teknenin saatleri bilgi ihtiyacınıza cevap veren.

Daha aykırı bir örnek verelim:

Bir şarkı bestelediniz, çok tuttu.
Öyle ki başka insanlar sizden telif almadan sağda solda parçanızı çalmaya ve hatta kendi parçalarıymış gibi pazarlamaya başladılar.
Siz bu insanları dava etmek istiyorsunuz. Bu senaryoda bilgi ihtiyacını temsil eden sizin parçanız, bilgi ihtiyacına cevap verense diğer insanların parçaları.
Bu senaryoda gerçekleşecek olan şey şu. Bir arama motoruna kendi parçanızı yükleyeceksiniz, o da size sizin parçalarınıza benzer parçaların listesini verecek.

Geneli itibariyle bilgi alım süreçleri ve metodları her ne kadar metin dışındaki aracılara da uygulanabiliyor olsa da, genel uygulama alanı metindir, yani genelde bilgi ihtiyacını temsil eden ve ona cevap veren uzunluğu değişebilir olmak kaydıyla bir karakter zinciridir.

#######################################
`Bilgi Alım Yöntemlerinin Unsurları`_
#######################################

Kabaca bir bilgi alım sürecinde etkin olan beş unsur vardır:

Belge derlemi
    Belge derlemi genellikle bilgi ihtiacına cevap vermesi beklenen belgelerin toplamından oluşur. Bu örneğin bir arama motoru için, internetteki sayfalardır.

Sorgu
    Bu bir kelime de olabilir, bir belge de, bir cümle de. Bilgi ihtiyacını arayan failin bilgi ihtiyacına verene ulaşmak için kullandığı aracıdır. Örneğin, ulaşmak istediğiniz sayfanın çıkması için arama motoruna yazdığınız kelimeler.

Dizinleme
    Bu belge ve sorgu için belge bir süreçtir. Genellikle belgenin ve sorgunun temsil şeklinin değiştirilmesi sayesinde olur. Örneğin, girdiğiniz sorguyu, girerken kullandığınız kelimelerin sıklığı ve sırası olarak temsil edebilirsiniz, bu derleminizdeki belgeler içinde geçerli.

Benzerlik Notu
    Sorgu ve belge arasındaki benzerliğin ne kadar olduğunu hesaplamaya yarayan algoritmalar sonucunda ortaya çıkan nottur. Genellikle, bilgi ihtiyacına cevap verenlerin sıraya konmasında kullanılır.

Geri Bildirim
    Bilgi ihtiyacının karşılanması adına sunduğunuz belgelerin ne kadar ilgili olduğuna dair kullanıcıların yaptığı geri dönüştür. Pratikte kullanıcılar nadiren böyle bir sürece dahil olurlar. Bu yüzden genelde *yalancı ilgililik geri bildirimleri* kullanırlar. Bu da tıklanan tepedeki belgelerin daha ilgili olduğunu varsaymak şeklinde gerçekleşir.
    

Bu yazıyı burada bitiriyorum, zira bundan sonra gelen konu bilgi alım modelleri ve başlı başına bir yazı olmayı hak ediyor.

Sağlıcakla,

Kaan
