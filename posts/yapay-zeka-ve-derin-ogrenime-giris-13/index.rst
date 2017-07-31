.. title: Yapay Zeka ve Derin Öğrenime Giriş 1.3
.. slug: yapay-zeka-ve-derin-ogrenime-giris-13
.. date: 2017-05-28 03:52:32 UTC+02:00
.. tags: yapay-zeka, derin-öğrenim, makine öğrenimi
.. category: yapay-zeka
.. link: 
.. description: 
.. type: text

Merhaba Arkadaşlar,

.. contents::


Bir `önceki yazımda <https://d-k-e.github.io/yapayzeka-eski-metinler/posts/yapay-zeka-ve-derin-ogrenime-giris-2/>`_ *Temsil Öğrenimi* veya diğer bir adıyla *Nitelik Öğrenimi* konusuna değinmiştim.
Otomatik kodlayıcıların aldıkları işlevlerden ve temsilde açığa çıkan değişiklik unsurlarıyla, gözlemlenenlerin ayrıştırıcı özellikleri arasındaki ilişkiden bahsetmiştim.
Ayrıştırıcı özelliklerin arasındaki karşılıklı etkileşim dolayısıyla temsil öğrenimindeki aşılması güç gözüken bir sorun olan değişiklik unsurlarının birbirinden ayrıştırılması işlemini açıklamaya çalıştım.

Bu yazıda, önceki yazıda duyurduğum gibi *Derin Öğrenimin* bahsettiğim kavramlarla ilişkisine ve yukarıda belirttiğim probleme nasıl bir çözüm getirdiğine değineceğim.
Bu giriş yazı dizisinin son yazısı olduğu için, kavramlarla aşina olmayanlar için serinin ilk iki yazısına da göz atmalarını tavsiye ederim, aksi takdirde bazı şeyler havada kalacaktır.

*Derin Öğrenimin* yaptığı karmaşık temsilleri daha basit temsiller cinsinden ifade etmeye çalışmaktır.
Örneğin, beyaz bir tahtaya çizilmiş bir üçgeni düşünelim.
Üçgene baktığımızda gördüğümüz önce beyazdan farklı olandır.
Sonrasında bu farklı olanın düz çizgilerden oluştuğunu fark ederiz.
Ardından bu düz çizgilerin köşeler oluşturduğunu fark ederiz.
Nihayetinde oluşan köşelerin sayısı bize üçgeni verir.
Bu işleyiş derin öğrenim sürecinde makinenin işleyişine benzerdir.
Makine başta imgecik değerlerinden, beyaz olmayanları gruplar.
Sonrasında gruplananların pozisyonlarını karşılaştırarak alarak onların kenar mı köşe mi olduğunu belirler.
Son olarak da köşe sayısını hesaplar ve ilgili köşe sayısına tekabül ettiği kendisine verilmiş sonucu size sunar.

O halde fark etmiş olabileceğiniz üzere burada işleyen imgecik değerlerinde açıkça gözlemediğimiz 4-5 tane kavram var.
Siyah, beyaz, düz çizgi, kenar, köşe, köşe sayısı.
Siyahı, beyaz olmayan diyerek, ve imgecik değerlerindeki farklılıktan yakaladık diyelim.
Beyaz olmayan imgeciklerin düz bir çizgi oluşturduğunu ifade edebilmemiz için, bu imgeciklerin konumu hakkında bize yargı veren bir model olması lazım.
Bu açıkça görüldüğü üzere ne üçgenle ne de imgeciklerin kendisiyle doğrudan ilişkili bir yapı, sadece belirli konumlarda olanların düz olmaya tekabül ettiğini belirten bir model.
Bu modelin elimizdeki üçgen problemine uygulanışında modele sunulan imgeciklerin konumu, ancak salt model açısından bakıldığında konumu verilen araba tekerleği, havadaki uçaklar, ya da endoplazmik retikulumlarda olabilirdi.
Aynı durum kenar, köşe kavramları içinde geçerli, yani bunlar da üçgen mahsus olmayan, imgeciklerle de doğrudan bir bağlantısı olmayan kavramlar.
Eldeki örnekte düz çizgilerin başladıkları ve bittikleri yerler olarak tanımlanıyor olmalarında ne üçgene ne de imgeciklere mahsus bir durum var.
Buna karşın, köşe sayısı ve üçgen arasındaki ilişki bir hayli doğrudan. O kadar ki bunun üçgen üzerinden modellenmiş bir nitelik olduğu fark ediliyor.
Makine elimizdeki örnekte bahsettiğimiz aşamalardan geçerek ne yapmış oldu peki ?
Çok basit, modeller arasındaki bir hiyerarşiyi takip ederek, yani onların ilgilendiği değerlerin hesaplanışında bir öncelik sonralık ilişkisi güderek, örneğin, önce siyah-beyaz, sonra çizgi, sonra kenar-köşe, vs. gibi, ham veriden, yani imgeciklerden, yakalamak istediğimiz varlığın ayrıştırıcı özelliğini, üç köşeli olmak, buldu.

Bu yaklaşımdaki esas nokta, farklı modeller tarafından hesaplanan sonuçların daha sonra kendilerine atıfta bulunulabilecek şekilde saklanmaları, bu sistemin kendi kendisini değerlendirebilmesini sağlayan yegane özellik.
Elimizdeki örnekte fark etmesi birazcık zor olmakla birlikte, diyelim ki ABC üçgeninin BC kenarının ortasında ufak bir boşluk var.
Silgi çarpmış, kolumuz değmiş, vs. herhangi bir şey olabilir.
Bu şartlar altında, üçgeni yakalamaya çalışan sistemimizin bu durumda çalışmaya devam etmesi, ve o boşluğu, kenarların ortasındaki boşluk olarak temsil edebilmesi lazım.
Modellerin sonuçlarının atıfta bulunulabilmesi burada devreye giriyor.
Elimizdeki örnekte makine diyelim ki düz çizgileri saptadı, ortaya açık bir şekil çıktı, dolayısıyla kenar diye bir şeyden söz edemememiz lazım.
Daha sonraki aşamada makine köşeleri ve köşe sayısını hesapladı ve şeklin üç köşe sayısı şartını sağladığını hesapladı.
Bu hesap ışığında makine, daha önceki model tarafından verilen açık şekil olmak sonucuna tekrar dönebilir, ve açıklık belirten değişiklik unsurunu, makineye daha öncesinden verdiğimiz talimatlar ışığında, görmezden gelebilir, veya bu sonucun kapsamını daraltabilir, yani örneğin şekil açıktır yerine çizgi bir nokta da kesilmiştir sonucunu sunabilir vs. 

Bu yöntemin derin öğrenim olarak ifade edilmesinin sebebi de, girdideki temsil ile çıktıdaki temsil arasında birbirinden görece bağımsız modeller tarafından üretilen temsillerin olması.
Derin Öğrenim algoritmalarını birer merdiven olarak da düşünebilirsiniz.
Her basamak aslında bir basamak, o basamağı bir başka basamağın üstüne ya da altına koyduğunuz için yukarıya ya da aşağıya doğru giden bir basamak. Kendi başına bıraksanız, yani merdivenden çıkarsanız basamağı ve yere koysanız, öyle ufak bir yükselti olur.

Derin öğrenim modellerinin, derinlik ölçümü için kullanılan, temelde iki yaklaşım var.
Birincisi, bir derin öğrenim modelinin değerlendirilebilmesi için gerekli talimatların uzunluğu.
İkincisiyse, birbirleriyle ilişkilenen kavramların temsilini sunan çizgenin derinliği.
İlki hangi işlemin adım olarak sayılacağına göre değişiklik gösterir.
Kullandığımız modellerden birinin K-Ortalamalar Kümesi algoritması olduğunu düşünelim.
Bu algoritma bilindiği üzere aslında iki aşamalıdır: Merkezlere eleman tayin etme ve elemanların pozisyonlarını eniyileme.
Birinci kriter ışığında derinliğimiz bu iki aşamayı ayrı ayrı saymak ya da bu iki aşamayı aynı algoritmaya tabi olduğu için bir olarak saymak bağlamında değişiklik gösterecektir.
İkinci kriterle konuya yaklaşıldığı zamansa ortaya yukarıda üçgen için tarif ettiğim modele benzer bir model ortaya çıkıyor.
Elimizde, örneğin, düz çizgi, kenar, köşe gibi kavramlar var ve derinlik bunların birbiriyle olan ilişkilerini temsil eden çizgede gözleniyor.
Bu yaklaşımdaki dikkat edilmesi gereken noktaysa, kavramlar arasındaki ilişkilerden çıkan çizgedeki derinliğin, hesaplanma sürecini ifade eden çizgenin derinliğinden bir hayli farklı olması.

Bu iki yaklaşımın ikisi de eşit derecede doğru ve geçerli, zira kişiler kendi modellerini kurgularken farklı birimleri temel alıyorlar.
Bir modelin derin olarak adlandırılabilmesi için de uzlaşılagelmiş bir ölçüm yok. O halde *Derin Öğrenim* nedir ?
Tek cümleyle özetleyecek olursak, derin öğrenim, dünyayı içiçe geçmiş hiyerarşik temsiller şeklinde kurgulayarak karmaşık kavram ve temsilleri, daha basit kavram ve temsiller aracılığıyla hesaplayan, makine öğrenimi alanıdır.


Bu yazıyı burada noktalıyorum ve böylelikle Derin Öğrenime Giriş serisini tamamlamış oluyorum.
Bundan sonraki seri, derin öğrenim algoritmalarını anlamak için olmazsa olmaz olan doğrusal cebir üzerine olacak.
Anlaşılmayan, ya da çok açık gözükmeyen noktaları lütfen yorumlarda belirtin.
Elimden geldiğince açıklamaya çalışırım.

Sağlıcakla,

Kaan
