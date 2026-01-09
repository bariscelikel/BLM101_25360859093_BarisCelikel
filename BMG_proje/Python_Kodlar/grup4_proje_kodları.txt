# =========================================================
# Brookshear Makine Dili Yorumlayıcısı (Decoder)
# Bu program, kullanıcıdan alınan 4 haneli HEX kodu
# Brookshear makine diline göre çözümler ve
# komutun ne yaptığını Türkçe olarak açıklar.
# =========================================================


def hex_kontrolu(kod):
    # -----------------------------------------------------
    # Bu fonksiyon, girilen kodun geçerli bir HEX kod
    # olup olmadığını kontrol eder.
    # Kontroller:
    # 1) Kod 4 haneli mi?
    # 2) Sadece hexadecimal (0-9, A-F) karakterler içeriyor mu?
    # Geçerliyse True, değilse False döndürür.
    # -----------------------------------------------------

    if len(kod) != 4:
        return False

    try:
        int(kod, 16)  # Kod HEX mi diye kontrol edilir
        return True
    except ValueError:
        return False


def brookshear_decoder(kod):
    # -----------------------------------------------------
    # Bu fonksiyon, Brookshear makine dili komutunu çözümler.
    # Girilen 4 haneli HEX kodu parçalara ayırır:
    # - 1. hane : Op-code
    # - 2. hane : Register
    # - 3-4. hane : Operand (adres veya diğer registerlar)
    # Op-code'a göre komutun açıklamasını döndürür.
    # -----------------------------------------------------

    opcode = kod[0]   # Komut türünü belirleyen Op-code
    r = kod[1]        # İşlem yapılacak register
    op = kod[2:]      # Bellek adresi veya sabit değer
    x = kod[2]        # İlk operand register
    y = kod[3]        # İkinci operand register

    # Op-code kontrolü yapılır
    if opcode == "0":
        return "Programı durdur (HALT)."

    elif opcode == "1":
        # Bellekten register'a yükleme
        return op + " adresindeki bellek hücresinin içeriğini, " + r + " numaralı kaydediciye yükle."

    elif opcode == "2":
        # Sabit değeri register'a yükleme
        return op + " sabit değerini, " + r + " numaralı kaydediciye yükle."

    elif opcode == "3":
        # Register içeriğini belleğe yazma
        return r + " numaralı kaydedicideki değeri, " + op + " adresindeki belleğe yaz."

    elif opcode == "4":
        # Bir register'dan diğerine kopyalama
        return x + " numaralı kaydedicideki değeri, " + y + " numaralı kaydediciye kopyala."

    elif opcode == "5":
        # Tam sayı toplama işlemi
        return r + " numaralı kaydediciye, " + x + " ve " + y + " numaralı kaydedicilerin TAM SAYI toplamını yaz."

    elif opcode == "6":
        # Kayan nokta toplama işlemi
        return r + " numaralı kaydediciye, " + x + " ve " + y + " numaralı kaydedicilerin KAYAN NOKTA toplamını yaz."

    elif opcode == "7":
        # OR (VEYA) mantıksal işlemi
        return r + " numaralı kaydediciye, " + x + " ve " + y + " numaralı kaydedicilerin OR işlemini yaz."

    elif opcode == "8":
        # AND (VE) mantıksal işlemi
        return r + " numaralı kaydediciye, " + x + " ve " + y + " numaralı kaydedicilerin AND işlemini yaz."

    elif opcode == "9":
        # XOR mantıksal işlemi
        return r + " numaralı kaydediciye, " + x + " ve " + y + " numaralı kaydedicilerin XOR işlemini yaz."

    elif opcode == "A":
        # Register içeriğini döndürme (rotate)
        return r + " numaralı kaydediciyi " + op + " kadar sağa döndür (ROTATE)."

    elif opcode == "B":
        # Koşullu dallanma (jump)
        return "Eğer " + r + " numaralı kaydedici sıfırsa, programı " + op + " adresine atla."

    elif opcode == "C":
        return "Programı durdur (HALT)."

    else:
        # Geçersiz op-code durumu
        return "Geçersiz Op-code!"


# ---------------------------------------------------------
# ANA PROGRAM
# ---------------------------------------------------------

# Kullanıcıdan HEX kodu alınır
kod = input("4 haneli HEX kodu giriniz: ").upper()

# Girilen kodun geçerli olup olmadığı kontrol edilir
if not hex_kontrolu(kod):
    print("HATALI GİRİŞ! 4 haneli geçerli bir HEX kod giriniz.")
else:
    # Kod geçerliyse çözümleme yapılır
    print("Komut Açıklaması:")
    print(brookshear_decoder(kod))
