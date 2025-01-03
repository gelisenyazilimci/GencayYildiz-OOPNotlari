# Nesne Kavramı

---

## Giriş

- Nesne kavramı, nesnelik felsefesine dayanır ve kainattaki her şeyi bir nesne olarak görüp yorumlama fikrine dayanır.
- Programlama dünyasında, gerçek hayattaki objelerin dijital muadillerini oluştururuz. Bu, yazılımın gerçek hayata uyumunu kolaylaştırır.
- Gerçek hayattaki herhangi bir varlığı (bir kişi, ürün veya yer gibi) yazılımda bir nesne olarak modelleyebiliriz.

## Nesne Nedir?

- **Nesne (Object):**
    - Gerçek hayattaki elle tutulur, gözle görülür varlıkları yazılım dünyasında temsil eder.
    - Bir nesne, genellikle belirli bir "sınıf" üzerinden tanımlanır ve bu sınıfın özelliklerini taşır.

## Nesne ve Sınıf İlişkisi

- Nesneler bir sınıftan üretilir. Sınıflar, nesnelerin sahip olacağı alanları (field) ve davranışları (method) tanımlar.
- Bir sınıftan çok sayıda nesne üretilebilir. Örneğin:

```csharp
class Araba {
    public string Renk { get; set; }
    public string Marka { get; set; }

    public void HareketEt() {
        Console.WriteLine("Araba hareket ediyor.");
    }

    public void Dur() {
        Console.WriteLine("Araba durdu.");
    }
}

// Nesne oluşturma
Araba benimArabam = new Araba();
benimArabam.Renk = "Kırmızı";
benimArabam.Marka = "Toyota";
benimArabam.HareketEt();
```

## Nesnenin Parçaları

1. **Alanlar (Fields):**
    - Nesnenin verilerini tutar. Örneğin, "Araba" nesnesinin "Renk" ve "Marka" gibi alanları olabilir.
    - Alanlar, nesnenin durumunu temsil eder.

2. **Metotlar (Methods):**
    - Nesnenin davranışlarını tanımlar. Örneğin, "HareketEt" veya "Dur" gibi metotlar, nesneye belirli bir işlev kazandırır.

3. **Property'ler:**
    - Alanları kontrol etmek ve dışarıya erişim sağlamak için kullanılır. "Getter" ve "Setter" ile veri manipüle edilebilir.

## Nesne Kavramına Genel Bakış

- Nesneler, yazılımı daha sistematik ve okunabilir hale getirir.
- Nesneler kendi içerisinde veri tutma ve bu veriler üzerinde işlem yapabilme kapasitesine sahiptir.
- Gerçek hayattaki karmaşık yapıları basitleştirerek, yazılım geliştirme süreçlerini daha düzenli hale getirir.

## Uygulama Örneği

```csharp
class Ogrenci {
    public string Isim { get; set; }
    public int Yas { get; set; }

    public void BilgiYazdir() {
        Console.WriteLine($"Öğrenci: {Isim}, Yaş: {Yas}");
    }
}

// Nesne oluşturma
Ogrenci ogrenci1 = new Ogrenci();
ogrenci1.Isim = "Ahmet";
ogrenci1.Yas = 20;
ogrenci1.BilgiYazdir();
```

Bu örnekte "Ogrenci" sınıfından bir nesne oluşturulmuş ve o nesneye ait bilgiler ekrana yazdırılmıştır.

---

Bu bölümde nesne kavramının temelini, sınıflarla olan ilişkisini ve özelliklerini ele aldık. İlerleyen bölümlerde daha detaylı uygulamalar yapılacak.

