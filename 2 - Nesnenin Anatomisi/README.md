# Nesnenin Anatomisi

---

## Giriş

- Nesnenin anatomisini anlamak, nesne tabanlı programlamanın temelini oluşturur. Eğer bu kavramı iyi kavrarsanız, nesne tabanlı programlamanın büyük bir kısmını öğrenmiş olacaksınız.
- Nesne tabanlı programlamada en temel yapı taşı "nesne" ya da "obje" olarak adlandırılır. Bu nesneler, gerçek hayattaki herhangi bir varlığı veya olguyu temsil edebilir. Örneğin: bir araba, bir kişi, bir ürün, bir adres.

## Nesnenin Temel Yapısı

1. **Alanlar (Fields):**
    - Nesneler, içerisinde veri tutabilecek alanlara sahiptir.
    - Bu alanlar, nesnenin özelliklerini temsil eder. Örneğin: bir "Araba" nesnesinin "rengi" veya "markası" gibi özellikleri alan olarak tanımlanabilir.
    - Alanların sayısında bir sınırlama yoktur; istediğiniz kadar özellik ekleyebilirsiniz.

2. **Metotlar (Methods):**
    - Nesneler, kendi içlerinde bulunan verilere işlem yapabilmek için metodlara sahiptir.
    - Metotlar, nesnelerin davranışlarını tanımlar. Örneğin: bir "Araba" nesnesi için "hareket et" veya "dur" gibi metotlar tanımlanabilir.
    - Bu metotlar sayesinde nesne içerisindeki veriler işlenir ve yeni sonuçlar üretilebilir.

3. **Sınıf (Class):**
    - Tüm nesneler bir sınıf modellemesinin örneğidir. Bir sınıf, nesnelerin nasıl oluşturulacağını ve ne tür özelliklere sahip olacağını tanımlar.
    - Nesneler bir sınıftan üretilir. Bu nedenle, bir nesne oluşturmak istiyorsanız öncelikle bir sınıf tanımlamanız gerekir.
    - Örneğin: "Araba" sınıfı, tüm arabaların genel özelliklerini ve davranışlarını tanımlarken; her bir araba nesnesi bu sınıfın bir örneği olur.

## Nesnelerin Özellikleri ve Örnekleme

- Bir sınıftan istediğiniz kadar nesne oluşturabilirsiniz. Örneğin, bir "Kimlik" sınıfından Türkiye'deki her vatandaş için bir kimlik nesnesi oluşturabilirsiniz.
- Sınıf, bir şablon veya model gibidir. Nesneler ise bu modelden üretilmiş somut örneklerdir.

### Örnek

```csharp
// Bir sınıf tanımlıyoruz
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

// Bir nesne oluşturuyoruz
Araba benimArabam = new Araba();
benimArabam.Renk = "Kırmızı";
benimArabam.Marka = "Toyota";
benimArabam.HareketEt();
```

- Yukarıdaki örnekte, "Araba" sınıfından bir nesne (benimArabam) oluşturulmuştur.
- Bu nesne, kendi renk ve marka gibi alanlarını tanımlayabilir ve hareketEt, dur gibi metotları çağırabilir.

## Nesne Tabanlı Programlamanın Avantajları

- **Modülerlik:** Kodlarınız daha düzenli ve modüler bir yapıya kavuşur.
- **Yeniden Kullanılabilirlik:** Bir sınıftan birçok nesne oluşturabilir, aynı kodu tekrar tekrar kullanabilirsiniz.
- **Bakım Kolaylığı:** Kodlar daha kolay anlaşılır ve güncellenebilir hale gelir.
- **Gerçek Hayat Modelleri:** Yazılım, gerçek dünyadaki kavramları daha iyi modelleyebilir.

---

Bu bölümde nesnelerin temel anatomisini ve bunların sınıf temelli yapılarını öğrendik. İlerleyen bölümlerde bu kavramları daha detaylı inceleyip uygulamalar yapacağız.

