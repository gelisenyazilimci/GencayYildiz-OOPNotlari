# Nesne Modellemesi

---

## Giriş

- Bir nesne oluşturabilmek için o nesnenin öncelikle yazılım ortamında modellenmesi gerekir. Bu modelleme sınıflar (“class”) aracılığıyla yapılır.
- Modelleme, nesnenin sahip olacağı ortak özellikleri (alanlar) ve davranışları (metotlar) belirler.
- Modelden üretilen her bir nesne, bu modele uygun bireysel özelliklere sahip olur.

---

## Nesne Modellemesi Nedir?

- Nesne modellemesi, gerçek hayattaki varlıkları yazılım dünyasında temsil etmek için sınıfları kullanarak yapısal bir çerçeve oluşturur.
- Her nesne, modelin belirlediği genel özelliklere sahipken, bu özelliklerin değerleri nesneden nesneye farklılık gösterebilir.

### Örnek: Araba Modeli

Bir araba modelini yazılımda şu şekilde tanımlayabiliriz:

```csharp
class Araba {
    public string Marka { get; set; }
    public string Model { get; set; }
    public int BeygirGucu { get; set; }

    public void HareketEt() {
        Console.WriteLine($"{Marka} {Model} hareket ediyor.");
    }

    public void Dur() {
        Console.WriteLine($"{Marka} {Model} durdu.");
    }
}

// Nesne oluşturma
Araba araba1 = new Araba {
    Marka = "Mercedes",
    Model = "C200",
    BeygirGucu = 184
};

Araba araba2 = new Araba {
    Marka = "Tofaş",
    Model = "Şahin",
    BeygirGucu = 50
};

araba1.HareketEt();
araba2.Dur();
```

- Yukarıdaki örnekte, "Araba" sınıfı bir model olarak tanımlanmış ve bu modelden iki farklı araba nesnesi oluşturulmuştur.
- Her araba nesnesinin kendi bireysel özellikleri ("Marka", "Model", "BeygirGucu") vardır.

---

## Gerçek Hayattan Bir Analoji

- Devletin verdiği "T.C. Kimlik Kartı" bir model olarak düşünülebilir.
    - Her kimlik kartında ortak özellikler vardır: T.C. Kimlik Numarası, ad, soyad, doğum tarihi, vb.
    - Ancak, her bireyin kimlik kartındaki bilgiler kendine özgüdür. Örneğin, bir bireyin adı "Ahmet" iken diğer bireyinki "Ayşe" olabilir.

---

## Nesne Modelleme Avantajları

- **Modülerlik:** Nesne modelleme, kodun yeniden kullanılabilir ve modüler yapıda olmasını sağlar.
- **Bakım Kolaylığı:** Nesneler ve sınıflar arasındaki yapısal bağlantı, kodun daha kolay okunması ve güncellenmesini sağlar.
- **Gerçek Hayat Modelleri:** Gerçek hayatta var olan karmaşık yapıların yazılım ortamında temsil edilmesini kolaylaştırır.

---

Bu bölümde nesne modellemesinin temelini ve avantajlarını öğrendik. Bir sonraki bölümde nesne modellemesine dayalı daha karmaşık yapılarla çalışacağız.

