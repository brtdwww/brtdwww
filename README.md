import time

class Soru:
    def __init__(self, soru_metni, cevaplar, dogru_cevap):
        self.soru_metni = soru_metni
        self.cevaplar = cevaplar
        self.dogru_cevap = dogru_cevap

    def soruyu_goster(self):
        print(self.soru_metni)
        for i, cevap in enumerate(self.cevaplar, 1):
            print(f"{i}. {cevap}")
    
    def cevap_kontrol(self, kullanici_cevabi):
        return kullanici_cevabi == self.dogru_cevap

def oyun():
    sorular = [
        Soru("Python hangi tür bir dilidir?", ["Derleme", "Yorumlama", "Her ikisi de değil"], 2),
        Soru("Python'da bir değişken nasıl oluşturulur?", ["create variable", "var x", "x = 5"], 3),
        Soru("Python'un yaratıcısı kimdir?", ["Guido van Rossum", "Bill Gates", "Mark Zuckerberg"], 1),
    ]

    skor = 0

    for soru in sorular:
        soru.soruyu_goster()
        kullanici_cevabi = input("Cevabınızı girin (1, 2, 3): ")
        
        if soru.cevap_kontrol(int(kullanici_cevabi)):
            print("Doğru!\n")
            skor += 1
        else:
            print(f"Yanlış! Doğru cevap: {soru.dogru_cevap}\n")

        time.sleep(1)

    print(f"Oyun bitti! Toplam skorunuz: {skor}/{len(sorular)}")

if __name__ == "__main__":
    oyun()
