# Field Kavramı

---

## Giriş

- Field (alan), nesne tabanlı programlamada bir sınıfın içinde tanımlanan ve nesnelerin veri tutmasını sağlayan temel yapısal bir bileşendir.
- Field, bir nesne içinde depolanan veya saklanan veriyi ifade eder.

---

## Field Nedir?

- Field, bir sınıf içerisinde tanımlanır ve nesne türetilmesi durumunda her nesne, kendine ait alanlara sahip olur.
- Bir field, herhangi bir veri türünden olabilir (örneğin: `int`, `string`, `float`, vb.).
- Sınıf içerisinde tanımlanan ancak metot veya property gibi yapıların içinde bulunmayan değişkenlere field denir.

---

## Field Tanımlama

Bir field tanımlamak için, sınıf içerisinde değişken tanımlarız:

```csharp
class Araba {
    public string Marka;
    public int Yil;
}
```

### Örnek:

```csharp
class Araba {
    public string Marka;
    public int Yil;
    public string Renk;
}

// Nesne oluşturma
Araba araba1 = new Araba();
araba1.Marka = "Toyota";
araba1.Yil = 2021;
araba1.Renk = "Kırmızı";

Console.WriteLine($"Marka: {araba1.Marka}, Yıl: {araba1.Yil}, Renk: {araba1.Renk}");
```

---

## Field’ın Özellikleri

1. **Sınıf İçinde Tanımlanmalı:**
    - Field, bir sınıfın scoopu içerisinde tanımlanmalıdır. Metotlar veya property’ler içinde tanımlanan değişkenler field sayılmaz.

2. Varsayılan Değer:
   - Field’lar, türlerine göre varsayılan değer alır:
   
    | Veri Türü | Varsayılan Değer |
    |-----------|------------------|
    | `int`     | 0                |
    | `float`   | 0.0f             |
    | `bool`    | false            |
    | `string`  | null             |
    | `char`    | '\0'             |




### Örnek:

```csharp
class Test {
    public int Sayisal;
    public string Metinsel;
    public bool Mantiksal;
}

// Nesne oluşturma
Test test = new Test();
Console.WriteLine(test.Sayisal);  // Çıktı: 0
Console.WriteLine(test.Metinsel); // Çıktı: null
Console.WriteLine(test.Mantiksal); // Çıktı: false
```

3. **Erişim Belirleyicileri:**
    - Field'lar varsayılan olarak `private` tanımlanır. Dışarıdan erişim sağlamak için `public` anahtar kelimesi kullanılabilir.

### Erişim Belirleyici Örnek:

```csharp
class Kisi {
    private string isim; // Varsayılan private

    public void IsimAyarla(string deger) {
        isim = deger;
    }

    public string IsimAl() {
        return isim;
    }
}
```

---

## Ek Notlar

1. **Field Tanımı Üzerine:**

    - Field'lar sadece sınıfın scoopu içinde tanımlanabilir.
    - Main metodu veya herhangi bir metot içerisinde tanımlanan değişkenler field değildir.

2. **Varsayılan Değerlerin Önemi:**

    - Field’ların türlerine göre varsayılan değer alabilmesi, yazılımda hatalı durumları önlemede etkilidir.
    - Ancak metot içindeki değişkenlerde bu durum geçerli olmadığından, bu değişkenlere değer atanmadığında hata alınabilir.

3. **Field Kullanımı:**

    - Field kullanılacaksa, her bir field'a ihtiyaç duyulan amaca uygun şekilde erişim belirleyici atanmalıdır (private, public vb.).

---

## Kısa Notlar

- Field, objenin içinde tanımlanan en temel yapısal bölümüdür.
- Sınıf içindeki tanımlanmış değişkenlerdir.
- Bir sınıfın içerisinde tanımlanan field'lar varsayılan bir değer alır (türüne göre).
- Metot içerisinde tanımlanan değişkenler varsayılan değer almaz. Varsayılan değer verilmediğinde hata oluşur.
- Field'lar, sınıftan türetilen her nesne için ayrı değerler tutabilir.
- Field, türüne göre varsayılan değerleri ile yazılımda kolaylık sağlar ve düzeni korur.

---

