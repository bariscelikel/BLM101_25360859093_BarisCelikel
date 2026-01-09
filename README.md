o Öğrenci Bilgileri: Barış Çelikel   25360859093
o Proje Konusu: Makine Dili ve Brookshear Mimarisi


o Proje Açıklaması:

# Brookshear Makine Dili Yorumlayıcısı (Decoder)

--  Proje Amacı  --
Bu projenin amacı, Brookshear sanal makinesinde kullanılan 4 haneli
onaltılık (hexadecimal) makine dili komutlarını analiz ederek,
bu komutların ne iş yaptığını Türkçe cümleler hâlinde kullanıcıya
açıklayan bir Python programı geliştirmektir.

Program, makine dili – donanım ilişkisini ve
Op-code / Operand kavramlarını somutlaştırmayı hedeflemektedir.


--  Program Ne Yapar?  --
Bu program:
- Kullanıcıdan **4 haneli bir HEX kod** alır.
- Kodun geçerli olup olmadığını kontrol eder.
- Kodu **Op-code**, **Register** ve **Operand** olacak şekilde parçalar.
- Brookshear Appendix C tablosuna göre komutun ne yaptığını belirler.
- Sonucu **Türkçe açıklama** olarak ekrana yazdırır.

Örnek:
Girdi: 14A3
Çıktı: A3 adresindeki bellek hücresinin içeriğini, 4 numaralı kaydediciye yükle.


--  Kurulum Gerekli mi?  --
Hayır.  
Program **yalnızca Python** kullanır ve harici kütüphane gerektirmez.

--  Gereksinimler:  --
- Python 3.x
- '.py' uzantılı dosya


--  Program Nasıl Çalıştırılır?  --

1. Python dosyasının bulunduğu klasöre gidilir.
2. Terminal / CMD açılır.
3. Aşağıdaki komut çalıştırılır:

python dosya_adi.py















# BLM101_25360859093_BarisCelikel
