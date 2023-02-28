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

Yazdığınız sorguları buradan test edebilirsiniz: [https://ergineer.com/assets/materials/fkg36so5-kutuphanebilgisistemi-sql/]

# Görevler

Aşağıda istenilen sonuçlara ulaşabilmek için gerekli SQL sorgularını yazın.

    1) ÖRNEK SORU: Yazar tablosunu KEMAL UYUMAZ isimli yazarı ekleyin.



    2) Biyografi türünü tür tablosuna ekleyiniz.


    3) 10A sınıfı olan ÇAĞLAR ÜZÜMCÜ isimli erkek, sınıfı 9B olan LEYLA ALAGÖZ isimli kız ve sınıfı 11C olan Ayşe Bektaş isimli kız öğrencileri tek sorguda ekleyin.


    4) Öğrenci tablosundaki rastgele bir öğrenciyi yazarlar tablosuna yazar olarak ekleyiniz.


    5) Öğrenci numarası 10 ile 30 arasındaki öğrencileri yazar olarak ekleyiniz.


    6) Nurettin Belek isimli yazarı ekleyip yazar numarasını yazdırınız.
    (Not: Otomatik arttırmada son arttırılan değer @@IDENTITY değişkeni içinde tutulur.)


    7) 10B sınıfındaki öğrenci numarası 3 olan öğrenciyi 10C sınıfına geçirin.


    8) 9A sınıfındaki tüm öğrencileri 10A sınıfına aktarın


    9) Tüm öğrencilerin puanını 5 puan arttırın.


    10) 25 numaralı yazarı silin.


    11) Doğum tarihi null olan öğrencileri listeleyin. (insert sorgusu ile girilen 3 öğrenci listelenecektir)


    12) Doğum tarihi null olan öğrencileri silin.


    13) Kitap tablosunda adı a ile başlayan kitapların puanlarını 2 artırın.


    14) Kişisel Gelişim isimli bir tür oluşturun.


    15) Kitap tablosundaki Başarı Rehberi kitabının türünü bu tür ile değiştirin.


    16) Öğrenci tablosunu kontrol etmek amaçlı tüm öğrencileri görüntüleyen "ogrencilistesi" adında bir prosedür oluşturun.


    17) Öğrenci tablosuna yeni öğrenci eklemek için "ekle" adında bir prosedür oluşturun.


    18) Öğrenci noya göre öğrenci silebilmeyi sağlayan "sil" adında bir prosedür oluşturun.


    19) Öğrenci numarasını kullanarak kolay bir biçimde öğrencinin sınıfını değiştirebileceğimiz bir prosedür oluşturun.


    20) Öğrenci adı ve soyadını "Ad Soyad" olarak birleştirip, ad soyada göre kolayca arama yapmayı sağlayan bir prosedür yazın.


    21) Daha önceden oluşturduğunu tüm prosedürleri silin.


    #Esnek görevler (Esnek görevlerin hepsini Select in Select ile gerçekleştirmeniz beklenmektedir.)
    22) Select in select yöntemiyle dram türündeki kitapları listeleyiniz.


    23) Adı e harfi ile başlayan yazarların kitaplarını listeleyin.


    24) Kitap okumayan öğrencileri listeleyiniz.


    25) Okunmayan kitapları listeleyiniz


    26) Mayıs ayında okunmayan kitapları listeleyiniz.

# Görevler

Aşağıda istenilen sonuçlara ulaşabilmek için gerekli SQL sorgularını yazın.

    1) ÖRNEK SORU: Yazar tablosunu KEMAL UYUMAZ isimli yazarı ekleyin.

    	INSERT INTO yazar (yazarad,yazarsoyad) VALUES ("KEMAL", "UYUMAZ")

    2) Biyografi türünü tür tablosuna ekleyiniz.

    	INSERT INTO tur (turadi) VALUES ("Biyografi")

    3) 10A sınıfı olan ÇAĞLAR ÜZÜMCÜ isimli erkek, sınıfı 9B olan LEYLA ALAGÖZ isimli kız ve sınıfı 11C olan Ayşe Bektaş isimli kız öğrencileri tek sorguda ekleyin.

    	INSERT INTO ogrenci(ograd,ogrsoyad,cinsiyet,sinif) VALUES ("Çağlar","Üzümcü","E", "10A"), ("Leyla","Alagöz","K","9B"), ("Ayşe","Bektaş","K","11C")

    4) Öğrenci tablosundaki rastgele bir öğrenciyi yazarlar tablosuna yazar olarak ekleyiniz.

    	INSERT INTO yazar (yazarad,yazarsoyad) select ograd,ogrsoyad from ogrenci order by rand() limit 1

    5) Öğrenci numarası 10 ile 30 arasındaki öğrencileri yazar olarak ekleyiniz.

    	INSERT INTO yazar (yazarad,yazarsoyad) select ograd,ogrsoyad from ogrenci where ogrno between 10 and 30

    6) Nurettin Belek isimli yazarı ekleyip yazar numarasını yazdırınız.
    (Not: Otomatik arttırmada son arttırılan değer @@IDENTITY değişkeni içinde tutulur.)

    	INSERT INTO yazar (yazarad,yazarsoyad) VALUES ("Nurettin","Belek")
    	SELECT @@IDENTITY

    7) 10B sınıfındaki öğrenci numarası 3 olan öğrenciyi 10C sınıfına geçirin.

    	UPDATE ogrenci SET sinif = "10C" WHERE ogrno = "3"

    8) 9A sınıfındaki tüm öğrencileri 10A sınıfına aktarın

    	UPDATE ogrenci SET sinif = "10A" WHERE sinif = "9A"

    9) Tüm öğrencilerin puanını 5 puan arttırın.

    	UPDATE ogrenci SET puan = puan + 5

    10) 25 numaralı yazarı silin.

    	DELETE FROM yazar WHERE yazarno=25

    11) Doğum tarihi null olan öğrencileri listeleyin. (insert sorgusu ile girilen 3 öğrenci listelenecektir)

    	SELECT * FROM ogrenci WHERE dtarih IS NULL

    12) Doğum tarihi null olan öğrencileri silin.

    	DELETE FROM ogrenci WHERE dtarih IS NULL

    13) Kitap tablosunda adı a ile başlayan kitapların puanlarını 2 artırın.

    	UPDATE kitap SET puan = puan + 2 WHERE kitapadi LIKE "A%"

    14) Kişisel Gelişim isimli bir tür oluşturun.

    	INSERT INTO tur (turadi) VALUES ("Kişisel Gelişim")

    15) Kitap tablosundaki Başarı Rehberi kitabının türünü bu tür ile değiştirin.

    	UPDATE kitap SET turno = (SELECT turno from tur where turadi = "Kişisel Gelişim") WHERE kitapadi ="Başarı Rehberi"

    16) Öğrenci tablosunu kontrol etmek amaçlı tüm öğrencileri görüntüleyen "ogrencilistesi" adında bir prosedür oluşturun.

    	CREATE PROCEDURE ogrencilistesi AS SELECT * FROM ogrenci GO;

    	EXEC ogrencilistesi

    17) Öğrenci tablosuna yeni öğrenci eklemek için "ekle" adında bir prosedür oluşturun.

    	CREATE PROCEDURE ekle @ograd nvarchar(30), @ogrsoyad nvarchar(30), @sinif nvarchar(15)
    	AS (BEGIN)
    	INSERT INTO ogrenci (ograd,ogrsoyad,sinif)
    	VALUES (@ograd,@ogrsoyad,@sinif)
    	GO;

    18) Öğrenci noya göre öğrenci silebilmeyi sağlayan "sil" adında bir prosedür oluşturun.

    	CREATE PROCEDURE sil @ogrno
    	AS
    	DELETE FROM ogrenci WHERE ogrno = @ogrno
    	GO;

    19) Öğrenci numarasını kullanarak kolay bir biçimde öğrencinin sınıfını değiştirebileceğimiz bir prosedür oluşturun.

    	CREATE PROCEDURE changeClassByStNumber @ogrno, @sinif
    	AS
    	UPDATE ogrenci SET sinif = @sinif WHERE ogrno = @ogrno
    	GO;
    	----
    	CREATE PROCEDURE sinifDegis (
    	In no INT
    	In newsinif TEXT
    	)
    	AS
    	BEGIN
        update ogrenci set sinif = newsinif where ogrno = no
    	END
    	GO;

EXEC sinifDegis(1,"10A")

    20) Öğrenci adı ve soyadını "Ad Soyad" olarak birleştirip, ad soyada göre kolayca arama yapmayı sağlayan bir prosedür yazın.

    	CREATE PROCEDURE search
    	AS
    	SELECT concat(ograd, ogrsoyad) as adSoyad from ogrenci
    21) Daha önceden oluşturduğunu tüm prosedürleri silin.



    #Esnek görevler (Esnek görevlerin hepsini Select in Select ile gerçekleştirmeniz beklenmektedir.)
    22) Select in select yöntemiyle dram türündeki kitapları listeleyiniz.

    	SELECT * from kitap WHERE turno IN (SELECT turno FROM tur WHERE turadi="Dram")

    23) Adı e harfi ile başlayan yazarların kitaplarını listeleyin.

    	SELECT * from kitap WHERE yazarno IN (SELECT yazarno,yazarad FROM yazar WHERE yazarad LIKE "E%")

    24) Kitap okumayan öğrencileri listeleyiniz.

    	SELECT * from ogrenci WHERE ogrno not in (SELECT ogrno from islem)

    25) Okunmayan kitapları listeleyiniz

    	select * from kitap where kitapno not in (select kitapno from islem where)
    	ontrol : select distinct kitapno from islem  order by kitapno ;

    26)Mayıs ayında okunmayan kitapları listeleyiniz.

    	select * from kitap where kitapno in (select kitapno from islem where atarih not like "%-05-%")
