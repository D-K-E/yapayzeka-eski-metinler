.. title: Yapay Zeka ve Derin Öğrenime Giriş - 1.1
.. author: Doğu Kaan Eraslan
.. slug: yapay-zeka-ve-derin-ogrenime-giris-1
.. date: 2017-05-26 02:13:15 UTC+02:00
.. tags: yapay-zeka, derin-öğrenim, makine öğrenimi
.. category: yapay-zeka
.. link: 
.. description: 
.. type: text

Yapay Zeka ve Derin Öğrenime Giriş - 1.1
########################################

Merhaba arkadaşlar,

Bu yapay zeka ve derin öğrenim ile ilgili yazmaya başladığım serinin ilk bölümü. Temel olarak kullandığım kaynak [DeepLearning2016]_. Bu bölümde::

- Yapay zeka çalışmaları nedir ?
- Hangi sorunlara cevap vermeye çalışmaktadır ?
- İçindeki çalışma alanları nelerdir ?

Gibi sorulara değineceğim. Sonraki yazılarda daha teknik konulara yer yer algoritmalara da gireceğim. Bu yazıda bahsettiğim konular, referans verdiğim kaynağın 1. bölümüne tekabül etmektedir.

Yapay zeka esasen fark etme ve tanımlama sorunsalı üzerinden okunabilecek bir alan. Bir şeyleri 5 duyudan ve onları sentetize eden bir beyinden yoksun bir varlığa fark ettirme sorunsalı. Fark etmenin gerçekleşmesi içinde yapılması gerekense, fark edilecek şeyin duyusal içerikten bağımsız bir biçimde tanımlanması.

Bilgisayarlar genel olarak, soyut kuralları takip etme işinde bizden daha iyiler. Bunun güzel bir örneği, bizden daha hızlı matematik işlemi yapabiliyor olmalarında, bir başka örneği yine bizden daha iyi satranç oynuyor olmalarında. Counter Strike vs gibi oyunlarla ilgilenen arkadaşların, internet kafede hedef botu kullanan adamı dövmesindeki sebepte yine bilgisayarın verili kuralları bizden daha iyi uygulayabiliyor olmasında.

Ancak bilgisayarlar 5 duyu gerektiren işlerde açık ara kötüler. Örneğin soru sorana cevap verme, karşıdan karşıya geçerken gelen arabayı görüp durma vs gibi işleri beceremiyorlar, zira bu işler çok fazla farklı türden veriyi birbiriyle ilişkilendirmiş olarak zihnimizde barındırmamız sayesinde mümkün oluyor. Biz bu işleri otomatik yapıyoruz ve aslında ne kadar karmaşık bir ilişkiler ağının ürünü olduğunun genelde farkında değiliz. Çok fark etmeye başladığımız zaman da deliriyoruz zaten, ancak şu da bir gerçek ki bilgisayarın günlük hayatımızı gerçekten kolaylaştırabilmesi, büyük oranda bu cins işleri yapabilmesine bağlı. Yani siz dizi izlerken makinenin, akşam yemeği, ev temizliği, hatta ofis işlerinizin belirli bir bölümü gibi işlevleri gerçekleştirebilmesi için, bu 5 duyu gerektiren işlerde de sonuç alabilmeleri gerekiyor.

İşte yapay zeka çalışmaları makinenin bu işleri yapabilmesini sağlayacak yöntemleri araştırıyor.
Denen yöntemlerden biri, makinenin dünyaya ilişkin bilmesi gereken her şeyi kodlamaya çalışmak, ki buna yapay zekaya bilgi temelli yaklaşım [1]_ deniyor. Siz bilgileri anlamsal içerikten yoksun bir dille ifade etmeye çalışıyorsunuz. Bilgisayarda genel mantık çerçevesinde dizayn edilmiş çıkarım kurallarını kullanarak, kendisine gelen bilgiden çıkarımlar yapıyor. Bu çok tutmadı, zira varolanı anlamdan yoksun bir dille ifade etmek hem bizim çok iyi yapamadığımız bir şey, hem de çok ağır işleyen bir süreç.

Her şeyin el ile kodlanması gerektiği sistemlerde karşılaşılan güçlükler,bizi makinelerin ham haldeki veriden kendilerinin tekrar eden kalıpları çıkarsamasını sağlayacak sistemler yaratmaya yöneltti. Bu minvalden gelen çalışmalara da genel adıyla makine öğrenimi [2]_ alanında yapılan çalışmalar deniyor. Bu alanda yürütülen çalışmaların günlük hayattaki etkileri daha gözlemlenebilir durumda. Örneğin Naive Bayes algoritmasını kullanarak sahte e-postaları ayırt edebiliyoruz, ya da Doğrusal Bağlanımları kullanarak elimizdeki malzeme stoklarını ne zaman yenilememiz gerektiğine dair akıl yürütmeler yapabiliyoruz, veya Netflix gibi büyük şirketler çok basit K-Ortalamalar Kümesi gibi gruplama algoritmalarıyla sizin hangi filmlerden hoşlanabileceğiniz size sunuyorlar [Algoritmalar]_. 

Bu yaklaşım iyi hoş ama önemli bir sorunu var, o da verinin temsil [3]_ edilmesi gerekliliği. Yukarıda bahsettiğim algoritmaların işleyebilmesi için, verinin belirli işlemlerden geçmesi gerekiyor. Bu çok basit bir biçimde bir metni boşlukları kullanarak, kelimelere ayırmak olabileceği gibi, kelimelerin belge içindeki sıklığı kere kelimelerin içinde görüldüğü belge sayısının kesri, boyutlarından oluşan uzunluğu standartlaştırılmış belge yöneyleriyle kosünüs benzerliği hesapları yapmak gibi görece daha karmaşık işlemleri de kapsayabiliyor [TF-IDF]_. İşlem görmüş ham veri içerisinde dikkate alınan her bir parçaya nitelik [4]_ deniyor. Yani ham veriye dair makinenin çıkarımlar yapabilmesini istiyorsanız onu bir nitelikler bütününe dönüştürmeniz lazım.

Üzerinde çalıştığınız problemin gerektirdiği verilerin hangi özelliğinin çözüme ilişkin olduğunu ve bu özelliğin ne şekilde bir niteliğe dönüştürebileceğini saptamanız gerekiyor. Bu bir hayli meşakatli bir iş. Örneğin, elinizde 100 bin tane kırmızı ışıkta geçen araba resmi var. Bu arabalara ceza kesilebilmesi için, plakalarının fotoğraflarda ayrıştırılabilmesi gerekiyor. Bilgisayar için arabanın tamponu ile plakası arasında bir fark yok. İkisi de imgecik. Örneği ilgili terimlerle ifade edersek::

- Problem: Işıktan geçen araba resminden plaka alma
- Özellik: Plaka: Beyaz bir dikdörtgen, üstünde siyahla yazılmış rakamlar ve sayılar var, bazılarında tire işareti de oluyor.
- Temsil: İmgecikler.

Çözüm ne peki ? Temsilden özelliği türetmemizi sağlayacak nitelikleri ayrıştırmakta. Bunu nasıl yapacağız ? İşte makine öğreniminin temel sıkıntısı burada yatıyor. 

Bu yazıyı burada noktalıyorum, zira ara vermek için güzel bir nokta. Daha sonrasında *Temsil Öğrenimi* ya da diğer bir adıyla *Nitelik Öğrenimini* açıklamaya çalışacağım. Çok katmanlı temsil gruplamalarından, değişiklik unsurlarından ve bunların öğrenimdeki rollerinden bahsedeceğim. Üçüncü yazımdaysa *Derin Öğrenimin* bu bahsettiğim kavramlarla olan ilişkisine, ve *derinliğin* nereden geldiğine değineceğim.

Sağlıcakla,

Kaan



=========
Terimler
=========
 

.. [1] Bilgi Temelli Yaklaşım: Makinenin dünyaya ilişkin bilmesi gereken her şeyi elle kodlamaya çalışmak.

.. [2] Makine Öğrenimi: Makinenin ham veriden tekrar eden kalıplar çıkarsaması.

.. [3] Temsil: Verinin sayısal ortamdaki hali.

.. [4] Nitelik: Temsilde bir özelliği ayrıştırmaya yarayan ölçülebilir yapı.

============
Notlar
============


.. [DeepLearning2016] Goodfellow I.,Y. Bengio, Deep Learning, Cambridge, 2016.

.. [Algoritmalar] Bahsettiğim algoritmaları açıklayan yazılar da yayımlayacağım.

.. [TF-IDF] Kabaca tarifini yaptığım algoritmanın adı genellikle arama motorlarında kullanılan bir sıralama algoritması. İlk bölümü ts-tbs, açılımı, terim sıklığı-ters belge sıklığı algoritması (ingilizcesi t(erm) f(requency)-i(nverse) d(ocument) f(requency)), ikinci bölümüyse, kosünüs benzerliği. Bu ikisi arama motorlarındaki 'buna benzer sayfaları göster' gibi işlemlerin gerçekleşmesini sağlıyor. Bu algoritmayı açıklayan yazıları da ileride paylaşacağım.

