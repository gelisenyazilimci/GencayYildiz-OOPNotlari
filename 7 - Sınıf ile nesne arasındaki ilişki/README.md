# Sınıf ile Nesne Arasındaki İlişki

---

## Giriş

- Sınıf (Class) ve nesne (Object) arasındaki temel bağlantı, nesnelerin bir sınıftan türetilmesi üzerine kuruludur.
- Sınıf, bir nesnenin modelini oluşturur; nesne ise bu modelin gerçek hayattaki somut bir temsilidir.

---

## Temel Kavramlar

1. **Sınıf:**
    - Nesnelerin sahip olacağı ortak alanları ve davranışları tanımlar.
    - Örnek: Bir “Araba” sınıfı, tüm arabaların sahip olduğu genel özellikleri ve davranışları tanımlar (renk, model, hareket etme, durma).

2. **Nesne:**
    - Bir sınıftan üretilen somut yapı.
    - Her nesne, sınıfın tanımladığı özelliklere ve davranışlara sahiptir ancak kendine özgün veri değerleri taşıyabilir.

---

## Sınıf ile Nesne Arasındaki İlişki

1. **Birden Fazla Nesne Üretilebilir:**
    - Bir sınıftan istediğiniz kadar nesne türetebilirsiniz. Ancak, bellekte tahsis edilen alanla sınırlısınızdır.

2. **Ortak Alanlar ve Davranışlar:**
    - Sınıflar, nesneler arasında ortak olan alanları ve davranışları tanımlar. Bu alanların değerleri nesnelerden nesnelere farklılık gösterebilir.

3. **Bağımsız Veri Değerleri:**
    - Her nesne, kendi veri değerlerini taşır. Örneğin, "ad" alanı tüm nesnelerde bulunur ancak bir nesne çin "Ali", diğeri için "Veli" olabilir.

---

## Örnek: Sınıf ile Nesne Arasındaki İlişki

```csharp
class Memur {
    public string Adi { get; set; }
    public int Yas { get; set; }

    public void BilgiYazdir() {
        Console.WriteLine($"Ad: {Adi}, Yaş: {Yas}");
    }
}

// Sınıftan Nesne Üretilmesi
Memur memur1 = new Memur {
    Adi = "Ali",
    Yas = 30
};

Memur memur2 = new Memur {
    Adi = "Veli",
    Yas = 25
};

memur1.BilgiYazdir(); // Çıktı: Ad: Ali, Yaş: 30
memur2.BilgiYazdir(); // Çıktı: Ad: Veli, Yaş: 25
```

### Açıklama

- "Memur" sınıfı, her memurun adı ve yaşı gibi ortak özelliklerini tanımlar.
- "memur1" ve "memur2" adlı nesneler, "Memur" sınıfından türetilmiştir ve her biri kendi veri değerlerine sahiptir.

---

## Önemli Notlar

1. **Bellek Yönetimi:**
    - Nesneler, heap bölgesinde saklanır. Bu nedenle dinamik olarak bellekte yer tahsis edilir.
    - Sınıf tanımları stack bölgesinde referanslarla işaretlenir.

2. **Ortak Tanımlar:**
    - Tüm nesneler, sınıf tarafından tanımlanan özelliklere sahip olur ancak bu özelliklerin değerleri nesne bazında farklı olabilir.

3. **Bir Projede Birden Fazla Sınıf:**
    - Bir projede birden fazla sınıf tanımlanabilir. Bu, projenin modüler yapıda olmasını sağlar.

---

## Sonuç

- Sınıf ile nesne arasındaki ilişki, nesne tabanlı programlamanın temelini oluşturur.
- Sınıflar, nesnelerin özelliklerini ve davranışlarını tanımlarken; nesneler, bu tanımlara uygun üretilen somut yapılardır.

Bu bölümde, sınıfların ve nesnelerin birbiriyle olan bağlantısını ve bu yapıların programlama üzerindeki etkisini detaylı olarak inceledik.

