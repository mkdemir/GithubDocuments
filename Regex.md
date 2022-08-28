# REGEX NEDİR

* Regex - Regular Expressions yani düzenli ifadeler. Düzenli veya düzensiz verileri düzenli bir şekilde alabilmenizi sağlayacak.

## REFERANSLAR

1. Kablosuz Kedi
   * [Github Link](https://github.com/gkandemi/regex)
   * [Youtube Link](https://www.youtube.com/watch?v=bF_zEzFQZuA&list=PLEFit5s1mKgPN7Mrn_K9DvBvN_pEdYrJJ&ab_channel=kablosuzkedi)

## NEDEN REGEX'E İHTİYACIMIZ VAR

Neden regex'e ihtiyacımız var. Sizin 1 tane kullanıcıdan veri aldığınız bir formunuz var. Kullanıcı telefon numarası giriyor. Yada e-mail adresini giriyor. Yada web sayfası URL'si giriyor. Bunların gerçekten bir şey olup olmadığını kontrol etmek istiyorsunuz. Yada geçerli bir şey olup olmadığını yada telefon numarası olup olmadığını kontrol etmek istiyorsunuz.

* Telefon numarasındaki alan kodunu, operatörü ve telefon numarsının kendisini ayrı ayrı gruplara almak da istiyor olabilirsiniz.

* Sizin bir veri setiniz var içerisinde 10.000 tane satır olan bir metin belgesi var. Metin belgesi içerisinde şöyle bir formatınız var. URL, title vb. düzenli olmayan veriniz var. Yani ayraçları düzenli olmayan veriler var.

* Regex tüm dillerde aynıdır. (MySQL - Oracle - MsSQL)

## REGEX'İN FARKLILIKLARI (Yazılmlar Arasından Değişen Özellikler)

1. İşleyişi ve işlenişi dile göre değişiyor (JS üzerinden gidecek olursak siz regex'inizi birincisi validate edebilirsiniz. Yani validasyonda kullanabilirsiniz - Geçerli mi geçersiz mi benim verdiğim regex göre doğru bir yapıda değil mi) Buna validasyon deniyor - "test".
2. Regexdeki yazdığım cümleye göre eşleşmeleri bana teker teker ver kısmı.
Bu iki aksiyon dilden dile değişebilir. Değişen tek kısım.

## g GLOBAL FLAG VE NOTASYONLAR

* Global olduğu için "regexr.com" üzerinden ilerleyeceğim. Bize güzel avantajlar sağlıyor.
* Bir regex cümlesi / ile başlar / ile biter. Daha sonraki arkadaşımız ise flagleri ifade eder.
        *  Örnek: g flag'i var (global).
* /o/ -> Tek bir karakter seçme. Burada o'yu seçtik.
  * Sadece ilk o'yu seçti.
    * Bunun nedeni ilk gelen herhangi bir flag set edilmemişse bu arkadaş ilk denk gelen ifadeyi seçer bırakır.
      * Eğer g (global) aktif hale getirirsek tüm o'ların hepsini seçer.
* /ne/ -> / ile / arasına yazılan ifadeyi bize getirir. Örnek olarak ne ifadesini getirdik.

  1. ( + ) (one or more: Yani bu arkadaşımız bizim için bir nicelik, notasyon, Bir tane veya şarta uyan birden fazla karakteri tek bir ifade olarak seçer) -> Bir öncesindeki karakter ya da şimdilik karakter diyoruz. Sonrasında bu karakter grubu da olabilir hale gelecek. Karakterin devamında da benzerine rastlarsa onları bir grup olarak seçer (Bir öncesindeki karakter ya da şimdilik karakter diyor. Sonrasında bu karakter grubunun devamını sağlarken).
     * Örnek: o+ -> Tüm o'lar teker teker seçmek yerine bir adımda seçti.
     * Örnek: oo+ -> Yine aynısı devam edecekti.
  2. ? -> bura?da "a" opsiyoneldir (Olsada olur).
     * Örnek 1: burada ve burda
     * Örnek 2: bura?dad?ı?r?
  3. *  -> ? (opsiyonel) ile +'nın birleşimi yani yapacağı şey bunu opsiyonel olarak kontrol et ama bunun devamı varsa onlarıda bir grup olarak bana getir.
  4. . -> Tek bir karakter seçimi (Not: Karakterin ne olduğunun bir önemi yok bu çok önemli).  * Örnek 1: /./ -> Bütün karakterleri seçtik.
     * Örnek 2: /.+/g Bütün karakterleri seçti ve bunları bir grup olarak bize verdi. Tek bir selection olarak vermiş oldu.
     * .A. -> A'dan önce A ve A'dan sonra 1 karakteri seç.
       * Not 1: Kelime satır başı ise bu regex satır başı olan için çalışmayacaktır.
       * Not 2: Kelime yeni satıra geçerse . geçersiz kalır.
         * Örnek: ce..
       * Örnek: b.nce -> Oradaki karakterinin ne olduğu önemli değil
     * i -> Case insensitive ama bazı durumlarda bunu aktif olarak hale getirmek bizim sonuçlarımızı baya bir değiştirebilir fark yaratabilir. Bunu siz regexinizde halletmeniz gerekmektedir.

## ÖZEL SEÇİCİLER

Bunların hepsi karakterleri tek tek seçer.

* \w -> Herhangi bir karakteri yani kelime karakterini bize getirir. (Undernumeric, underscore ve alfanümeric) _ Buda geçerlidir.
  * ü'leri almadı nedeni ise flaglerden unicode 'un aktif hale gelmemesi (Aktif olmazsa browser kaynaklı olabilmektedir Türkçe karakterlerde).
* \W -> Küçük w ters bir ifade. \w'de olmayan her şeyi alır (Buda boşluklara özel karakterlere denk gelir underscore hariç(_)).
* \s -> Sadece space'leri alır.
* \S -> s'nin tersi (space olmayan her şeyi alır).
* \d -> (digit) Sayıları seçmek için tek tek. Örnek -> \d+ bunları bir grup olarak yazdı.
* \D -> (Dijit) olmayan her şeyi seçer.

## ARALIK BELİRLEME

* .{}-> Seçilen karakter veya karakter grubundan ki bunu yapacağız. Karakter grubundan bana teker teker seçmek yerine bunları 2'li gruplar halinde seç. Hece gibi düşün (Bunun ismi aralık belirleme gibi düşünebilirsiniz).
  * Örnek: .{2} Herhangi bir karakter benim için .{2} li gruplar halinde gelsin.
  * Örnek: En az 2'li olacak şekilde beşerli al .{2,5}
  * .{3,}-> En az 3 olmak üzere sınırsız al

## KARAKTER GRUPLAMA

Örnek1: fat cat hat tat nat Fat Cat 4at 5at _at gruplayarak al.

Cevap: \w{3}

Örnek 2:fat cat hat tat nat Fat Cat 4at 5at ?at _at

Cevap: [fchtnFC4A5?_]at -> Karakter gruplama. Başında f c h t n F C 4 A 5 ? _ olabilir ama sonu at olması lazım.

Örnek 3: fat cat hat tat nat Fat Cat 4at 5at ?at _at

## KARAKTER GRUPLAMA ARALIK BELİRLEME

* [] -> Bu köşeli parantez bize bir range sağlamayı tanımlamamızı sağlıyor. Yani bir aralık belirlememizi sağlıyor.
* [a-z]at -> a'dan z'ye ne varsa başında kabul et sonunda at bekle kadar. Gelenler: fat cat hat tat nat
* [a-zA-Z]at -> fat cat hat tat nat Fat Cat
* [a-zA-Z0-9]at -> fat cat hat tat nat Fat Cat 4at 5at
* [a-zA-Z0-9?_]at ya da [a-zA-Z0-9\w?]at  ya da [a-zA-Z0-9\w\W]at -> Spesifik olarak  ?, \_ belirtebilirsiniz yazabilirsiniz. -> fat cat hat tat nat Fat Cat 4at 5at ?at _at
  * [a-zA-Z0-9\w\W]at Burada bir tric var  at -> Bu arkadaşa boşlukta dahil. Az bir veriniz varsa  spesifik olarak belirtebilirsiniz.

## KARAKTER GRUBU VE VEYA OPERATÖRÜ

Kullanıcının yazmış olduğu telefon numarasındaki operatörün ne olduğunu çekmek isteyebilirsiniz. Onu bu yüzden gruplamanız gerekebilir. İşte bu gruplar bu işe yarıyor. Örnek: 555 546 3456

* gray grey -> İkisi aynı anlamda ve aynı şeyi ifade etmekte ama aksan farklılkarı nedeniyle yazımda bir değişiklik bulunmaktadır.
  * Çözüm: gray, grey -> gra?e?y hangisi var denk olanı getir. Ama çok güzel bir yöntem değil.
    * gr[ae]y -> Böylede bir kullanım yapılabilir ama grup yok.
    * Bunun yerine gruplama yapabiliriz.
* Gruplama yapabilmek için () Paronormal bir parantez açıyoruz.

* gr(a|e)g -> a veya e içeriyorsa sıkıntı yok.
* Örnek: colour ve color almak için -> colou?r u burada opsiyoneldir. Gruplamaya gerek yok ama kuulanmak istersek. colo(u)?r

* re+ -> rerere grup olarak seçmesini beklereken seçmedi neden. İfadenin okunuşu r var. r'nin yanında e olacak. Öncesindeki karakterin aynısını yada şartını ifadenin şartını sağlayan herşeyi sonuna ekle yani reeeeeeeeeeeeeeeeeeeee beklediği yani e'yi devam ettirir. Ben re'yi devam ettirmesini istiyorsam. Bunları parantez içerisine alırım. (re)+  "rerere" bir grup olarak aldı.

(re){2} -> r grubundan 2 tane yan yana olsun (Karakter veya karakter grubu (re){2,} -> Bu karakter grubundan 2 tane arka arkaya varsa veya daha fazla varsa bunları tek bir grup olarak al).

Biz bide re'nin yanına ra'yıda almak istiyorsak. (re|ra){2,} veya bunun yerine + basarız. Hepsi kaç tane varsa.

Örnek:
Sokakta yanlız yürüyorum.
Sokak bunun farkında bile değil

* ^ -> İse ifadesi bu arkadaş birinci satırın satır başına bakar.
  * Örnek: Satır başındaki ^A ise seç. Yada karakter grubunu temsil eder ^()
Cevap1: ^S -> Ama burada mutli line flagiğini aktif hale getirdikten sonra seçtik.
S
S
* multiline flagini aktif hale getirmedik.

* $ -> Sondaki karakteride tespit etmek için kullanılır.
  * Örnek: k$ -> Sonu k ile biten
    * .$ -> Nokta dediğim şey aslında bizi aldatıyor. Seçti gibi gözüküyor. Bu seçtiğimiz arkadaş doğru değil kontrol etiği şey sonunda bir karakter var mı yok mu diye kontrol ediyor.
  * \.$ -> Eğer nokta ifadesini seçmek istersek.

### LOOK BEHIND AND LOOK AHEAD GİRİŞ (X GERİSİNE BAK VE X İLERİSİNE BAK )(BABALARA GELDİK)

Bazen seçmek istediğiniz ifade x iken bu ifadenin sonunda seçmek istediğniz bir ifade olabilir. Yada bu ifadenin başında bir ifade olabilir.
(basinda)x(sonunda) -> Bazen x seçmek için sonundaki ifadeye bakabilirsiniz bazen x seçebilmek için başındaki ifadeye bakabilirsiniz. Bu iki kompleks araç sayesinde biz x'i tanımlayıp x'i direk oradan çekebiliriz.

* (lookbehind)x(lookahead) -> (x'in gerisi) x (x'in ilerisi)
* lookbehind -> Hedefin gerisinde aradığımız kelimedir.
* lookahead -> Hedefin ilerisindeki aradığımız ifadelerdir.

## LOOKAHEAD (İlerisine Bak)

* İlk göreceğimiz arkadaşımız lookahead (İlerisine bak) seçmek istediğim hedefin ilerisinde şu var mı varsa o zaman seçimi yap. x'i seç.

### POZİTİF LOOK AHEAD

* lookahead ve lookbehind pozitif ve negatif diye 2'ye ayrılır. Lookahead'in pozitifi ile başlayalım.Kısacası seç
  * Örnek: quantity and qrcode are really useful.
  * .(?=u) -> Neyi peki seçelim, "." bir karakter seç, devamında bir şey olacak lookahead şu şekilde kullanılıyor. ?= Bir karakter seç, karakterimden hemen sonra "u" olsun.
    * [a-zA-z](?=r)

### NEGATİF LOOK AHEAD

* Devamında .(?!r) "r" olmayanı bana seç bu arkdaş seçme yapar.
  * Örnek bir kullanım: src="url" -> ...(?=")

## LOOKBEHIND

Yine seçeceğim karakterin, seçmek istediğim ifadenin  başındaki ifadeyle ilgileniyorum. Tek yaptığım şey bu.

### POZİTİF LOOK BEHIND

* Bir tane karakter seç "." başında, "(?<=)" negatifi ise "(?<!)"

### NEGATİF LOOK BEHIND

* (?<!q). -> Öncesindeki q olan karakteri seçme.

## NOT

(.*) -> Her şeyi al, bu herhangi bir karaktere uyan tık, tık seç.

### ÖRNEK-> URL Parsing

* Örnek 1: Url Parçalama
  * Example: src="http://<`midTierServer`>/arsys/shared/login.jsp?goto=<`URL`>&server=<`serverName`>"
    * (?<=src=")(.*)(?=") -> URL içindeki değeri alır.
* Örnek 2: Date Parçalama
  * Example: 2016-09-28 04:30:30, Info                  CBS    Loaded Servicing Stack v6.1.7601.23505 with Core: C:\Windows\winsxs\amd64_microsoft-windows-servicingstack_31bf3856ad364e35_6.1.7601.23505_none_681aa442f6fed7f0\cbscore.dll
    * (^)(.*)(?=,) -> 2016-09-28 04:30:30

### ÖRNEK -> Telefon Numarası

* Örnek: Telefon Numarası
  * 1234567890
    * `\d+, \d{10}, \d{3}\d{3}\d{4}, (\d{3})(\d{3})(\d{4}),(\d{3})-?(\d{3})-?(\d{4}), (\d{3})[ -]?(\d{3})[ -]?(\d{4})`
  * 123-456-7890
    * `(\d{3})-(\d{3})-(\d{4}), (\d{3})-?(\d{3})-?(\d{4}), (\d{3})[ -]?(\d{3})[ -]?(\d{4})`
  * 123 456 7890
    * `(\d{3})-? ?(\d{3})-? ?(\d{4}), (\d{3})[ -]?(\d{3})[ -]?(\d{4})`
  * (123) 456-7890
    * `\(?(\d{3}\)?)[ -]?(\d{3})[ -]?(\d{4})`
  * +90 123 456 7890
    * `(\+\d{2})? \(?(\d{3}\)?)[ -]?(\d{3})[ -]?(\d{4}), (\+\d{2})?[ ]?\(?(\d{3}\)?)[ -]?(\d{3})[ -]?(\d{4}) , (?<areaCode>\+\d{2})?[ ]?\(?(\d{3}\)?)[ -]?(\d{3})[ -]?(\d{4})
    (?<areaCode>\+\d{2})?[ ]?\(?(?<operator>\d{3})\)?[ -]?(?<main>\d{3})[ -]?(?<number>\d{4})`

### ÖRNEK -> Tarih Formatları

* `(?<gun>\d{2})[\/\-\.](?<ay>\d{2})[\/\-\.](?<yil>\d{2,4})`
  * 14/02/2018
    14-02-2018
    14.02.2018
    14.02.18

### ÖRNEK -> URL Formatları

* `[https://www.videosinif.com~videosinif]`

  * (?<=\[)(.*)(?=~)
  * `(?<=\[)(?<url>.*)(?=~)~(?<title>.*)(?=\])`
  * `<a href="url">title</a>`
`
ÖRNEK -
* [https://www.videosinif.com~videosinif]
* [https://www.kablosuzkedi.com,kablosuzkedi]
* [https://www.youtube.com/kablosuzkedi|kablosuzkedi youtube kanalı]
`

`(?<=\[)(?<url>.*)(?=[\~\,\|])[\~\,\|](?<title>.*)(?=\])`

### ÖRNEK: Email Validation

* [a-zA-Z0-9_] -> \w+
* example@example.com -> \w+@\w+\.[a-zA-Z]{2,}

* Örnek: Mail validation örnekleri
  * (https?:\/\/)?(www\.)?([a-zA-Z0-9]+)(\.[a-zA-Z0-9])
-> test@test.com
-> www.test.com
-> http://www.test.com
-> https://www.test.com

### ÖRNEK: Hashtag  Alma

* `#` alma


### ÖRNEK: Windows Date Log'unu Alma

* 2016-09-28 04:30:30, Info                  CBS    Loaded Servicing Stack v6.1.7601.23505 with Core: C:\Windows\winsxs\amd64_microsoft-windows-servicingstack_31bf3856ad364e35_6.1.7601.23505_none_681aa442f6fed7f0\cbscore.dll
  * `(?<date>(?<year>\d{4})\W(?<month>\d{2})-(?<day>\d{2}))\W(?<time>\d{2}:\d{2}:\d{2}),.`

### ÖRNEK

* 
data-config-url="https://player.vimeo.com/video/488734703/config?autopause=1&amp;autoplay=1&amp;byline=0&amp;collections=1&amp;context=Vimeo%5CController%5CClipController.main&amp;default_to_hd=1&amp;outro=nothing&amp;portrait=0&amp;share=1&amp;title=0&amp;watch_trailer=0&amp;s=8be48fe12cfacadb79085e9c2acbd6568c1fb641_1609112069" data-fallback-url="//player.vimeo.com/video/488734703/fallback?js"

ZeroMQ nedir isimli video şu an yayında! https://www.youtube.com/watch?v=YAYp7hbOu7o

Pentagram'ın güzel bir şarkısı güzel bir şarkı gibi sanki ama eski tadını vermiyor https://www.izlesene.com/video/pentagram-bu-duzen-yikilsin/10523935

    * (https:\/\/)(www\.)?(?<vimeo>(player\.vimeo\.com\/video\/[0-9]+\/)?)(?<youtube>youtube\.com\/watch\?v=[a-zA-Z0-9]+)?(?<izlesene>(izlesene\.com\/video\/[a-zA-Z0-9\/-]+))?

# ÖRNEK -> JS Email Validasyonu

' Javascript
const email_regex = /\w+@\w+\.[a-zA-Z]{2,}/g;
if (email_regex.test("gokhan@gkandemir.com")) {
    alert("Başarılı");
} else {
    alert("Başarısız")
}
'

# ÖRNEK -> 

const regex = /#[a-zA-Z0-9şığüçö]+/gm;

const str = `Regex için video hazırlıyorum. #Regex ile çözümlemek için Bana uğraştığınız merak ettiğiniz metinleri yazabilir misiniz? Mesela #Web sayfasındaki <body></body> #tag 'leri arasındaki bilgileri almak gibi. Bu #kolay tabi :) #Derdimianlatabilmişimdirumarım :) #360dayscleancode`;

// console.log(str.match(regex));

str.match(regex).forEach(h => console.log(h));