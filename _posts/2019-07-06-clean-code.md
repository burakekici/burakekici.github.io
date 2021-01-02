---
title: "Clean Code Kitap Özeti"
layout: post
date: 2019-07-06 10:00
image: /assets/images/2019/clean-code/cover.jpg
headerImage: false
tag:
- clean code
- temiz kod
- yazılım
- programlama
- craftsmanship
- ustalık
- kitap
- özet
- uncle bob
- robert martin
category: dev
author: ekici
description: Temiz Kod (Clean Code) kitabından aldığım notlar.
---

Merhaba, 

Robert C. Margin, namıdiğer Uncle Bob, tarafından yazılan _Temiz Kod (Clean Code)_ adlı kitabı yakın bir zamanda okudum. Aldığım notları da birilerine faydalı olabileceği ihtimaliyle paylaşmak istedim.

* Eğer yazılımla ilgileniyorsanız kitabın orijinalini okumanızı kesinlikle öneririm. Fayda/zaman oranı en yüksek kitaplardan biri olduğunu düşünüyorum. 

* Türkçe içerik isterseniz öncelikle Büşra Uzun’un yazmış olduğu çok daha detaylı ve örneklerle bezeli [seriyi okumanızı öneririm](https://medium.com/@busrauzun/clean-code-kitabindan-notlar-1-temiz-kod-derken-44e6f7a27eb0). 

* Daha kısa bir içerik yeterli diyenler, bilgilerini tazelemek isteyenler ya da kitabı okumadan önce fikir sahibi olmak isteyenler; bu yazı sizin için.

<br>

---

<br>

# Temiz Kod

Temiz kod yazmak çaba gerektirir. Sadece kurallar ve örüntüler (patterns) yetmez, çok çaba gerektirir.

<br>

# İsimlendirmeler

**Değişken isimleri** mutlaka kolay anlaşılabilir, kısaltma içermeyen, mantıklı kelimelerden oluşmalı. 

**Sınıf isimlerinde** fiil olmamalı. 

**Fonksiyon isimlerinde** yapacağı işi anlatan bir fiil olmalı.

<br>

# Fonksiyonlar

**Fonksiyonlar 20 satırı kolay kolay geçmemeli**.

Yalnızca **TEK BİR İŞ** yapmalı. 

Kodlar tepeden tırnağa **bir hikaye okuyormuş gibi** okunabilmeli.

Uzun fonksiyon isimleri olabilir. Uzun bir isim, kısa ama muğlak bir isimden yeğdir. Uzun bir fonksiyon adı, uzun bir açıklayıcı yorum satırından da iyidir.

Fonksiyonların parametre sayısı için **en iyi argüman sayısı 0’dır**. Sonra 1, ve sonra da 2. 3 adet argüman alan bir fonksiyondan kaçınılmaya çalışılmalıdır. Çok elzem durumlar hariç 3’ten fazla argüman alan bir fonksiyon yazılmamalıdır. 

Fonksiyonlar bir dilin fiilleridir, sınıflar ise isimleri.

<br>

# Yorumlar

> “Don’t comment bad code - rewrite it.” - Brian Kernighan

Uncle Bob neden yorumlara daima ön yargılı olduğunu şöyle açıklıyor; **yorumlar yalan söyler** çünkü yazılımcılar yorumları güncellemek konusunda gereken özveriyi göstermez. Yorumlar eski kalır, hatalı anlamlar çıkarmaya elverişli olur.

Bu da Ron Jeffries’den gelsin:
> “Code never lies, comments sometimes do.” 

**Kullanılmayan kodları yorum satırına almak yerine silin**. Çünkü sizden sonraki kişiler bunu yapmaya cesaret edemeyecektir, bu kodun önemli ya da gerekli olduğunu düşünebilir. Versiyon kontrol sisteminden ihtiyacınız olan koda ulaşmak mümkün. Kullanılmayan kodun üretim kodunda tutulmasına gerek yok.

<br>

# Biçimlendirme (Formatting)

İnsanlar kaynak koduna baktığında onları kodun düzeni, tertibi ve detaylarıyla etkilemek isteriz. 

Kodu okurken sanki bir gazete makalesi okuyormuş gibi okuyabilmeliyiz. İsimler kısa, basit ve açıklayıcı olmalı. İsimlere bakarak doğru modülü inceleyip incelemediğimizi direkt olarak anlayabilmeliyiz. Kodun en üst kısmı bize algoritma ve konsepti kabaca anlatmalı. Aşağı inildikçe detaylar artmalı.

Değişkenler mümkün olduğunca kullanılacağı yerde tanımlanmalı.

<br>

# Nesneler ve Veri Yapıları

Değişkenleri _private_ yapmamızın bir sebebi var. Başka kimsenin onlara bağımlı olmasını istemeyiz.

_Demeter Kuralına_ göre (_Law of Demeter, LoD_ [*](https://www.wikiwand.com/en/Law_of_Demeter)), hiçbir modül bir diğer modülünü iç dünyasını bilmemeli. Vikipedi’de (evet 2 yıldır yasaklı olan Vikipedi’de) bu yasa aşağıdaki üç madde ile açıklanıyor:

* Her birim diğer birimler hakkında kısıtlı bilgiye sahip olmalıdır. Sadece birbiriyle yakından ilişkili olanlar birbirini tanımalı.
* Her birim yalnızca kendi arkadaşlarıyla konuşmalı; yabancılarla konuşmamalı.
* Sadece yakın arkadaşlarıyla konuşmalı.

Bu sayede _gevşekçe bağlı (loosely coupled)_ modüller üretilmiş olur. Bu da projenin esnekliğini, bakım yapılabilirliğini, anlaşılabilirliğini ve test edilebilirliğini artırır.

Zincirleme metot kullanımından kaçınılmalıdır. 

<br>

# Hataları Ele Alma

Bir fonksiyondan _null_ döndüğümüzde, aslında ele alınması gereken yeni bir iş çıkarıyoruz. Fonksiyondan _null_ dönmek de, bir fonksiyona parametre olarak _null_ vermek de kötüdür. Mümkün mertebe kaçınılmalıdır. 

Generic’ler kullanılarak kodun okunabilirliği artırılabilir.

<br>

# Testler

Üretimdeki kodu keşfetmek ve anlamak test yazabiliriz.  

_TDD_’de (_Test Driven Development_) testler ve üretim kodu birlikte yazılır, testler biraz önden gider.

Test kodları üretim kodu değiştikçe güncellenmelidir.

Test kodları üretim kodu kadar önemlidir.

Üretim kodunun esnek, bakım yapılabilir ve yeniden kullanılabilir olmasını birim testleri sağlar.

Testler olmadan her değişiklik, potansiyel bir hatadır.

Temiz bir testi ne sağlar? Üç şey: okunabilirlik, okunabilirlik, okunabilirlik.

Bir testi okunabilir kılan şeyler nelerdir? Normal bir kodu okunabilir kılan şeylerle aynı: netlik, sadelik ve anlaşılabilirlik.

Temiz bir test şu beş kuralı takip eder: **F.I.R.S.T.**
* _Fast_ : Hızlı
* _Independent_ : Birbirine bağımlı değil
* _Repeatable_ : Farklı ortamlarda tekrar tekrar kullanılabilir
* _Self-validating_ : Boolean çıktısı olan
* _Timely_ : Zamanında yazılmış (üretim kodu yazılmadan hemen önce)

<br>

# Sınıflar

Her sınıfın en üstünde değişkenler bulunmalıdır. Varsa _public static constants_, sonra _private static variables_, sonra _private instance variables_.

_Private utility_ fonksiyonlar, çağrıldığı _public fonksiyonlardan_ hemen sonra yazılmalı. Böylece kodun gazete makalesi gibi okunması sağlanabilir.

Sınıfların ilk kuralı: kısa olmalıdır. İkinci kural: daha da kısa olmalıdır. 

Sınıfların sorumlulukları 70 adet _public_ fonksiyonu aşmamalıdır. 

_SRP_’ye (_Single Responsibility Principle_ [*](https://www.wikiwand.com/en/Single_responsibility_principle)) göre **bir sınıf ya da modül sadece 1 amaca hizmet etmelidir**. 

Problem şu ki çoğumuz, program çalıştığında işimiz bitmiş sayarız. Geri dönüp birbirine bağımlı ve şişmiş sınıfları temizlemek yerine bir sonraki göreve atılırız.

Soru şu: iyi düzenlenmiş, etiketlenmiş ve net bir şekilde tanımlanmış birçok küçük çekmecelerin olduğu bir çekmecelik mi istersiniz? Yoksa her şeyi içine atıp kapattığınız birkaç çekmeceden oluşan bir çekmecelik mi? 

Sınıflar az sayıda _instance_ değişkenlerine sahip olmalıdır. 

Çoğu sistem için sürekli değişiklikler istenir. Her değişiklikte bu sistemin istenildiği gibi çalışmama riski yükselir. Temiz ve organize yazılmış sınıflar ise bu riski düşürmeye yarar.

Eğer bir sistem yeterince bağımsız parçalardan oluşuyorsa _(decoupled)_, daha esnek ve yeniden kullanılabilir bir yapıya kavuşacaktır. 

**Dependency Inversion Principle** [*](https://www.wikiwand.com/en/Dependency_inversion_principle) özünde der ki, sınıflar somut birimlere (_concrete_) değil soyut birimlere (_abstractions_) bağımlı olmalıdır.

<br>

Tüm detayları kendi başınıza yönetebilir misiniz? Muhtemelen hayır. Bir şehri yönetmek bile bir insan için fazladır. 

Bugün dev şehirleri yönetebiliyoruz çünkü yeterli soyutlama yapılmış ve modülarite sağlanmıştır. Bazı insanlar büyük resimden mesuldür, bazıları ise alt katmanlarla yani detaylarla ilgilenir.

<br>

**Separation of concerns** [*](https://www.wikiwand.com/en/Separation_of_concerns) (“meselelerin ayrılması”; ya da "etliyi sütlüyü karıştırmamak" daha iyi bir çeviri olabilir), en eski ve en önemli tasarım tekniklerinden biridir.

**Inversion of control** [*](https://www.wikiwand.com/en/Inversion_of_control) ile SRP'yi (Single Responsible Princible) desteklenerek modülarite artırılabilir.

<br>

“İlk seferinde doğru yap!“ bir efsanedir. 
Bilakis, sadece bugünün görevlerini kodlarız, refactor ederiz ve ertesi gün sistemi gereken şekilde genişletiriz. Bu, projenin esnek, çevik ve sürdürülebilir olmasının temel koşuludur. 

Eğer sistem doğru şekilde ayrılmış küçük birimlerden oluşuyorsa yeni birimler eklemek de mevcut birimlere bakım yapmak da kolaydır, maliyeti düşüktür. 

<br>

Yeterince büyük bir sistemde, bir şehir ya da yazılım projesi fark etmez, tüm kararları tek başına alabilen bir kişi ya da bir modül olamaz.

Kent Beck’e göre bir sistem tasarımını “basit” kılan kurallar şunlardır:
* Tüm testleri geçer.
* Hiçbir kopya ve tekrar yoktur.
* Yazılımcının niyeti doğrudan anlaşılırdır.
* Sınıfların ve metotların sayısı minimize edilir.

Tekrarlama (duplication [*](https://www.wikiwand.com/en/Duplicate_code)), iyi tasarlanmış bir sistemin baş düşmanıdır. Tekrarlar ekstra iş, ekstra risk ve istenmeyen gereksiz karmaşıklığa sebep olur.

**Bir yazılım projesinin esas maliyetini uzun dönemli bakımı oluşturur.**

İyi isimler seçerek kendinizi ifade etmelisiniz. Bir fonksiyonun adını okuduktan sonra yaptığı işe ve sorumluluklarına baktığımızda şaşırmak istemeyiz.

Fonksiyon ve sınıfları kısa tutmalısınız. Kısa sınıf ve fonksiyonlar kolay isimlendirilir, kolay yazılır, kolay anlaşılır.

Standartları takip etmelisiniz. Örneğin tasarım örüntüleri diğer insanlarla iletişim kurma ve anlamlılık açısından önemlidir.

<br>

Eğer geçtiğimiz yıllar boyunca bir şey öğrendiysek o da şudur, programlama bir bilimden çok zanaattır. **Temiz koda sahip olmak için önce kirli kod yazılır, sonra temizlenir.**

Çiçeği burnunda yazılımcılar (genellikle yeni mezunlar), kod çalıştığı anda öylece bırakıp bir sonraki göreve geçerler. Tecrübeli yazılımcılar bunun bir profesyonel intihar olduğunu bilir.

Çözüm ise basittir, kodu daimi olarak temiz ve basit tutmak.

<br>

Yorum satırları ile ilgili son bir derleme yapacak olursak, yorum satırları lüzumsuz hiçbir şey içermemelidir. Sadece kod ile anlatılamayacak teknik detayları içermelidir.

Eğer bir yorum yazacaksanız, vaktinizi kullanın ve yazabildiğiniz en iyi yorumu yazın. Kelimelerinizi itinayla seçin. Dil bilgisi ve imla kurallarına uyun. Lafı uzatmayın. Zaten apaçık görünen bir detayı yazmayın. Kısa kesin.

<br>

# Sistem

Herhangi bir kodun kopyasını (duplication) gördüğünüz zaman anlayın ki bir soyutlama (abstraction) fırsatı kaçırılmıştır.

Doğru bir şekilde tanımlanan interface az sayıda fonksiyon barındırır böylece bağımlılıklar azalır.

Verinizi saklayın. Yardımcı fonksiyonlarınızı (utility functions) saklayın. Sabit değerlerinizi ve geçici değerlerinizi saklayın. Çok fazla sayıda metot ve değişken barındıran sınıflar oluşturmayın.

Herhangi bir yerde ölü, lüzumsuz, kullanılmayan kod bulduğunuzda gerekeni yapın, gözünün yaşına bile bakmayın… 

Lokal değişkenler kullanıldığı yerlerden yüzlerce satır uzakta olmamalıdır.

Private fonksiyonlar ilk kez kullanıldığı yerin hemen altında olmalıdır. 

Anlam belirsizliği ve beklenmeyen durumları oluşturan kodlar ya anlaşmazlık ya da tembellik eseridir. Her iki durumda da düzeltilmelidir.

Soyutlama seviyelerini belirlemek en önemli kod düzenleme (refactoring) aşamalarından biridir, aynı zamanda en zorlarından biridir. 

Eğer A, B ile çalışıyorsa, B de C ile çalışıyorsa biz A’nın C’yi tanımasını istemeyiz. a.getB().getC().doSomething(); şeklinde erişmemelidir.

Demeter Yasasını (Law of Demeter) inceleyebilirsiniz. Pragmatik programcılar “Utangaç kod” olarak adlandırır. Modüller yalnızca direkt olarak iş birliği yaptığı modüllerle tanışıklık kurmalıdır, tüm sisteme erişememelidir. 

Okunabilir kod yazmak, daimi bir iyileştirme sürecine ihtiyaç duyar.

---

# Kapanış

Bu kitaptan edindiğim en kıymetli ders şu oldu: temiz kod bir çırpıda yazılmaz. Önce kirli kod yazılır, sonra düzenlenir. Bu süreçte de mümkün olduğunca basit, küçük, anlaşılır ve bağımsız modüller yazmak gereklidir. 

İlgilenen olursa bana ulaştığı takdirde notlarımın İngilizce halini gönderebilirim. 

Kodlarınız temiz, gününüz güzel olsun; hoşça kalın! 

