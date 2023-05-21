# SQL Sorgu Alıştırmaları

Bu hafta SQL sorguları üzerine çalışıyorsunuz. Bugünkü alıştırmada sizin için hazırladığımız veritabanında aşağıda istediğimiz sonuçları elde etmenize yarayan SQL sorgularını oluşturacaksınız.

# Proje Kurulumu

Projeyi forklayın ve clonlayın. Tamamladığınızda da pushlayın.

## Kütüphane Bilgi Sistemi

Bu veritabanı, bir okulun kütüphanesinden öğrencilerin aldıkları kitapların bilgisini barındırmaktadır.

#Tablolar
`ogrenci` tablosu öğrencilerin listesini tutar.
`islem` tablosu öğrencilerin kütüphaneden aldıkları kitapların bilgilerini tutar
`kitap` tablosu kütüphanedeki kitapların bilgisini tutar
`yazar` tablosu kitapların yazarları bilgisini tutar
`tur` tablosu kitapların türlerini tutar.

Tablo ilişiklerini görmek için [ktphn.png] dosyasına göz atın.

Yazdığınız sorguları buradan test edebilirsiniz: [https://ergineer.com/assets/materials/fkg36so5-kutuphanebilgisistemi-sql/] (update, delete, drop sorguları iptal edilmiştir).

### Görevler

Aşağıda istenilen sonuçlara ulaşabilmek için gerekli SQL sorgularını altlarına yazın.

    1) ÖRNEK SORU: Öğrenci tablosundaki tüm kayıtları listeleyin.

    	CEVAP: select * from ogrenci


    2) Öğrenci tablosundaki öğrencinin adını ve soyadını ve sınıfını listeleyin.

    	select ograd,ogrsoyad,sinif from ogrenci

    3) Öğrenci tablosundaki kız öğrencileri listeleyin.

    	select ograd,ogrsoyad,sinif from ogrenci where cinsiyet = "K"

    4) Öğrenci tablosunda kaydı bulunan sınıfların adını her sınıf bir kez görüntülenecek şekilde listeleyiniz

    	select distinct sinif from ogrenci

    5) Öğrenci tablosunda, 10A sınıfında olan kız öğrencileri listeleyiniz.

    	select * from ogrenci where sinif = "10A" and cinsiyet = "K"

    6) Öğrenci tablosundaki 10A veya 10B sınıfındaki öğrencilerin adını, soyadını ve sınıfını listeleyiniz.

    	select ograd ,ogrsoyad ,sinif  from ogrenci where sinif in ("10A","10B")

    7) Öğrenci tablosundaki öğrencinin adını, soyadını ve numarasını okul numarası olarak listeleyiniz. (as kullanım örneği)

    	select ograd,ogrsoyad , ogrno as "okulnumarası"  from ogrenci

    8) Öğrenci tablosundaki öğrencinin adını ve soyadını birleştirip, adsoyad olarak listeleyiniz. (concat, as kullanım örneği)

    	select CONCAT(ograd ,ogrsoyad) as "ad-soyad" from ogrenci

    9) Öğrenci tablosundaki Adı ‘A’ harfi ile başlayan öğrencileri listeleyiniz.

    	select ograd ,ogrsoyad from ogrenci where ograd like "a%"

    10) Kitaplar tablosundaki sayfa sayısı 50 ile 200 arasında olan kitapların adını ve sayfa sayısını listeleyiniz.

    	select * from kitap where sayfasayisi BETWEEN 50 and 200

    11) Öğrenci tablosunda adı Fidan, İsmail ve Leyla olan öğrencileri listeleyiniz.

    	select * from ogrenci where ograd in ("Fidan","Ismail","Leyla")

    12) Öğrenci tablosundaki öğrencilerden adı A, D ve K ile başlayan öğrencileri listeleyiniz.

    	select ograd ,ogrsoyad from ogrenci WHERE ograd REGEXP '^(A|D|K)'

    13) Öğrenci tablosundaki sınıfı 9A olan Erkekleri veya sınıfı 9B olan kızların adını, soyadını, sınıfını ve cinsiyetini listeleyiniz.

    	select ograd ,ogrsoyad from ogrenci WHERE (sinif="9A" and cinsiyet= "E") or (sinif="9B" and cinsiyet="k")

    14) Sınıfı 10A veya 10B olan erkekleri listeleyiniz.

    	select ograd ,ogrsoyad from ogrenci WHERE (cinsiyet ="E") AND (sinif="10A" or sinif = "10B")

    15) Öğrenci tablosunda doğum yılı 1989 olan öğrencileri listeleyiniz.

    	select ograd ,ogrsoyad from ogrenci WHERE dtarih LIKE "%1989%"

    16) Öğrenci numarası 30 ile 50 arasında olan Kız öğrencileri listeleyiniz.

    	select ograd ,ogrsoyad from ogrenci WHERE (cinsiyet = "K") and ogrno BETWEEN "30" and "50"

    17) Öğrencileri adına göre sıralayınız (alfabetik).

    	select ograd,ogrsoyad from ogrenci order by ograd asc

    18) Öğrencileri adına, adı aynı olanlarıda soyadlarına göre sıralayınız.

    	SELECT * FROM ogrenci order by ograd asc, ogrsoyad asc

    19) 10A sınıfındaki öğrencileri okul numarasına göre azalan olarak sıralayınız.

    	select * from ogrenci where sinif = "10A" order by ogrno desc

    20) Öğrenciler tablosundaki ilk 10 kaydı listeleyiniz.
    [İPUCU: `Select top tüm mysql versiyonlarında düzgün çalışmaz. LİMİT kullanmak daha faydalıdır`]

    	select * from ogrenci limit 10

    21) Öğrenciler tablosundaki ilk 10 kaydın ad, soyad ve doğum tarihi bilgilerini listeleyiniz.

    	select ograd ,ogrsoyad ,dtarih  from ogrenci limit 10

    22) Sayfa sayısı en fazla olan kitabı listeleyiniz.

    	select *  from kitap order by sayfasayisi desc LIMIT 1

    23) Öğrenciler tablosundaki en genç öğrenciyi listeleyiniz.

    	select *  from ogrenci order by dtarih desc limit 1

    24) 10A sınıfındaki en yaşlı öğrenciyi listeyin.

    	select *  from ogrenci where sinif="10A" order by dtarih asc limit 1

    25) İkinci harfi N olan kitapları listeleyiniz.

    	select * from kitap where kitapadi like  ("_n%")

    26) Öğrencileri sınıflarına göre gruplayarak listeleyin.

    	select sinif,COUNT(*) as "ogrenci_sayisi"  from ogrenci group by sinif

    27) Öğrencileri her sorgulamada sıralaması farklı olacak şekilde rastgele listeleyin.
    [İPUCU: rand() fonksiyonu]

    	select *  from ogrenci order by RAND()

    28) Öğrenci tablosundan Rastgele bir öğrenci seçiniz.

    	select ograd ,ogrsoyad  from ogrenci order by RAND() LIMIT 1

    29) 10A sınıfından rastgele bir öğrencinin adını, soyadını, numarasını ve sınıfını getirin.

    	select ograd ,ogrsoyad,sinif,ogrno  from ogrenci WHERE sinif = "10A" order by RAND() LIMIT 1

    # Esnek
    30) Öğrenci tablosunda aynı isimde kaçar öğrenci olduğunu bulmak istiyoruz.
    Öğrenci isimlerinin sayısını "adet" olarak öğrencilerin isimleri "isim" olarak listeleyin.
    [İPUCU: count() ve group by]

    	select ograd as "isim" ,COUNT(*) as "adet"  from ogrenci group by ograd
