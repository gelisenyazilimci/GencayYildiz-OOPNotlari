# Sınıf Nedir?

---

## Giriş

- Sınıf (Class), nesne tabanlı programlamanın temel yapı taşıdır. Bir sınıf, nesnelerin modelini oluşturur ve bu model üzerinden nesneler üretilir.
- Sınıflar, bir nesnenin sahip olabileceği özellikleri (alanlar) ve davranışları (metotlar) tanımlar.

---

## Neden Sınıf Yapısı Kullanılır?

- **Modülerlik Sağlar:** Kodun düzenli ve okunabilir bir yapıda olmasını sağlar.
- **Yeniden Kullanılabilirlik:** Sınıflar bir kez tanımlandıktan sonra birçok nesne oluşturulabilir.
- **Karmaşıklığı Azaltır:** Karmaşık projelerde yapıların bir bütün olarak anlaşılmasını kolaylaştırır.

---

## Sınıf ve Nesne İlişkisi

- Sınıf, bir nesnenin şablonudur. Nesneler bu şablondan üretilir.
- Sınıf, özellikler (alanlar) ve işlevler (metotlar) tanımlar. Nesneler ise bu tanımlamalara uygun şekilde oluşturulur.

---

## Örnek: Sınıf Tanımlama ve Nesne Üretimi

Aşağıda "Araba" sınıfını ve bu sınıftan üretilen nesneleri örnekleyelim:

```csharp
class Araba {
    // Özellikler
    public string Marka { get; set; }
    public string Model { get; set; }
    public int Yil { get; set; }

    // Metotlar
    public void HareketEt() {
        Console.WriteLine($"{Marka} {Model} hareket ediyor.");
    }

    public void Dur() {
        Console.WriteLine($"{Marka} {Model} durdu.");
    }
}

// Sınıftan Nesne Oluşturma
Araba araba1 = new Araba {
    Marka = "Toyota",
    Model = "Corolla",
    Yil = 2020
};

araba1.HareketEt(); // Çıktı: Toyota Corolla hareket ediyor.
```

### Açıklama
- "Araba" sınıfı, bir aracın ortak özelliklerini ve davranışlarını tanımlar.
- "araba1" nesnesi, "Araba" sınıfının bir örneğidir ve belirtilen özelliklerle oluşturulmuştur.

---

## Sınıfların Temel Yapısı

1. **Alanlar (Fields):** Nesnelerin sahip olabileceği veriler. Örneğin, bir kişinin adı veya yaşı.
2. **Metotlar (Methods):** Nesnelerin gerçekleştirebileceği işlemler. Örneğin, bir araba nesnesinin hareket etmesi.
3. **Property'ler:** Alanlara erişim kontrolü sağlar. Get ve set anahtar sözcükleri ile tanımlanır.

---

## Sınıf Oluşturmanın Adımları

1. **Tanımlama:**
    - `class` anahtar kelimesi kullanılarak sınıf tanımlanır.
2. **Özelliklerin Belirlenmesi:**
    - Sınıfa ait özellikler (alanlar ve property'ler) tanımlanır.
3. **Davranışların Tanımlanması:**
    - Sınıfa ait metotlar tanımlanır.
4. **Nesne Üretimi:**
    - Tanımlanan sınıftan nesneler oluşturulur.

---

## Daha İleri Konular

1. **Abstract Sınıflar:**
    - Türetilmesi gereken sınıfların temel yapısını tanımlar. Doğrudan nesne üretilemez.
2. **Interface:**
    - Sınıflar arasında ortak bir iletişim protokolü sağlar. Özellikle soyutlama için kullanılır.
3. **Inheritance (Kalıtım):**
    - Bir sınıfın başka bir sınıfın özelliklerini ve metotlarını devralmasını sağlar.

---

Bu bölümde sınıf kavramını ve nesne üretimindeki temel yapısını ele aldık. İlerleyen bölümlerde sınıflarla ilgili daha karmaşık konuları inceleyeceğiz.

