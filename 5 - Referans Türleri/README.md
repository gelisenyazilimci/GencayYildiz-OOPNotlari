# Referans Türleri

---

## Giriş

- **Yazılımda Türler:** Yazılımda değişkenler iki ana türe ayrılır: **değer türlü** ve **referans türlü** değişkenler.
- **Değer Türlü:** Kendi değerini doğrudan tutar ve bellekte "stack" adı verilen alanda saklanır.
- **Referans Türlü:** Verinin adresini tutar ve bellekte "heap" adı verilen alanda depolanan verilere dolaylı erişim sağlar.

Referans türlü değişkenler, özellikle nesneler ve sınıflarla çalışırken kritik bir öneme sahiptir, çünkü karmaşık veri yapılarının esnek ve dinamik bir şekilde kullanılmasına olanak tanır.

---

## Değer Türlü ve Referans Türlü Arasındaki Farklar

| **Özellik**            | **Değer Türlü**                                    | **Referans Türlü**                                    |
|-------------------------|---------------------------------------------------|-----------------------------------------------------|
| **Bellek Konumu**       | Stack                                             | Heap                                                |
| **Veri Depolama**       | Değeri doğrudan taşır.                             | Verinin bellekteki adresini taşır.                  |
| **Hız**                 | Daha hızlıdır (stack kullanımı nedeniyle).         | Daha yavaştır (heap erişimi gerektirir).            |
| **Paylaşılabilirlik**   | Veriler bağımsızdır, bir kopya oluşturulur.        | Veriler paylaşılır, aynı nesne birden fazla referansla erişilir. |
| **Örnekler**            | `int`, `float`, `bool`                            | `class`, `string`, `array`                         |

---

## Referans Türlerinin Temel Özellikleri

1. **Heap ve Stack Kullanımı:**
    - Stack, değişkenlerin referanslarını tutar.
    - Heap, referans edilen nesnelerin kendilerini depolar.

2. **Garbage Collector (GC):**
    - Heap'teki kullanılmayan nesneler, Garbage Collector tarafından otomatik olarak temizlenir.

3. **Dinamik Yapı:**
    - Referans türlü değişkenler, dinamik olarak tahsis edilen bellek üzerinde çalışır. Bu, daha büyük ve karmaşık veri yapılarını yönetmek için idealdir.

---

## Örnek: Referans Türlü Değişkenler

Bir sınıf tanımlayarak referans türlü değişkenlerin nasıl çalıştığını gösterelim:

```csharp
class Ogrenci {
    public string Isim { get; set; }
    public int Yas { get; set; }
}

// Referans türü bir nesne oluşturma
Ogrenci ogrenci1 = new Ogrenci();
ogrenci1.Isim = "Ahmet";
ogrenci1.Yas = 20;

Ogrenci ogrenci2 = ogrenci1; // ogrenci2, ogrenci1'i referans eder
ogrenci2.Isim = "Mehmet";

Console.WriteLine(ogrenci1.Isim); // Çıktı: Mehmet
```

### Açıklama
- `ogrenci1` ve `ogrenci2`, aynı heap alanındaki nesneyi referans eder. Bu nedenle, birindeki değişiklik diğerini etkiler.

---

## Bellek Yönetimi: Stack ve Heap

### Stack
- Küçük, kısa ömürlü veriler için idealdir.
- Değişkenlerin referanslarını ve temel türleri saklar.
- Hızlı bir yapıdır çünkü lifo (last in, first out) prensibiyle çalışır.

### Heap
- Karmaşık ve büyük veri yapıları için kullanılır.
- Daha yavaştır, ancak daha geniş bir alan sağlar.
- Dinamik bellek tahsisi yapılır ve Garbage Collector yönetir.

---

## Daha Kapsamlı Bellek Örneği

```csharp
class Araba {
    public string Marka { get; set; }
    public string Model { get; set; }
}

Araba araba1 = new Araba(); // Referans stack'te, nesne heap'te tutulur
araba1.Marka = "Toyota";
araba1.Model = "Corolla";

Araba araba2 = araba1; // araba2, araba1'i referans eder
araba2.Model = "Yaris";

Console.WriteLine(araba1.Model); // Çıktı: Yaris
```

### Detaylı Açıklama
- `araba1` ve `araba2` aynı heap alanındaki nesneyi işaret eder.
- Heap'teki nesneye yapılan bir değişiklik, tüm referansları etkiler.

---

## Referans Türlerinin Avantajları

1. **Dinamik Bellek Yönetimi:**
    - Karmaşık yapıların ve dinamik verilerin daha etkili bir şekilde işlenmesini sağlar.

2. **Bellek Paylaşımı:**
    - Aynı nesne birden fazla referansla paylaşılabilir, bu da bellek tasarrufu sağlar.

3. **Karmaşık Yapılar:**
    - Diziler, listeler ve sınıflar gibi karmaşık veri tiplerini yönetmek için uygundur.

4. **Esneklik:**
    - Büyük ve değişken boyutlu verilerin yönetimi için idealdir.

---

## Dezavantajlar

1. **Bellek Sızıntısı:**
    - Kullanılmayan nesneler Garbage Collector tarafından temizlenmezse bellek sızıntısına neden olabilir.

2. **Yan Etkiler:**
    - Aynı nesneyi işaret eden birden fazla referans, beklenmedik değişikliklere yol açabilir.

3. **Performans:**
    - Heap erişimi stack'e göre daha yavaştır.

---

## Örnek: Referans Türü ile Bellek Yönetimi

```csharp
class Kisi {
    public string Ad { get; set; }
    public string Soyad { get; set; }
}

Kisi kisi1 = new Kisi { Ad = "Ali", Soyad = "Veli" };
Kisi kisi2 = kisi1;
kisi2.Ad = "Ahmet";

Console.WriteLine(kisi1.Ad); // Çıktı: Ahmet
```

### Açıklama
- `kisi1` ve `kisi2`, aynı nesneyi işaret eder. Bu nedenle, birinde yapılan değişiklik diğerinde de görülür.

---

Bu bölümde referans türlerini derinlemesine inceledik ve avantajlarını, dezavantajlarını ve bellek yönetimindeki rollerini detaylandırdık. Bir sonraki bölümde, referans türlerinin uygulama senaryolarını ve tasarım desenleriyle entegrasyonunu ele alacağız.

