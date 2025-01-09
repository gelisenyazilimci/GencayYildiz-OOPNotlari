# Property İmzaları - Init-Only Properties - Init Accessor

---

## Temel Bilgiler
- Init-Only Properties, nesnenin sadece ilk yaratılış anında propertylerine değer atamaktadır.
- Böylece iş kuralı gereği run time'da değeri değişmemesi gereken nesneler için bir önlem alınmaktadır.
- Init-Only Properties, developer açısından süreç esnasında değiştirilmesi gereken property değerlerinin yanlışlıkla değiştirilmesinin önüne geçmekte ve böylece olası hata ve bug'lardan yazılımı arındırmaktadır.

## Auto Property Initializers vs Init-Only Properties

Auto Property Initializers'dan farkı ve getirisi şudur:
- Init-Only Properties, object initializer syntax ile nesne oluşturma sırasında değer atamaya izin verir
- Constructor'da değer atanabilir
- İlk değer atamasından sonra değiştirilmesi mümkün değildir (immutable)
- Daha esnek bir kullanım sunar

## Örnek Kullanım

```csharp
public class Personel
{
    // Init-only property
    public string TcKimlik { get; init; }
    public string Ad { get; init; }
    public string Soyad { get; init; }
    
    // Normal property
    public string Departman { get; set; }
}

// Kullanım örneği
var personel = new Personel 
{
    TcKimlik = "12345678901", // İlk oluşturmada atanabilir
    Ad = "Ahmet",
    Soyad = "Yılmaz"
};

// personel.TcKimlik = "98765432109"; // Hata! Init-only property'ler sonradan değiştirilemez
personel.Departman = "IT"; // Normal property değiştirilebilir
```

## Init Accessor'ın Avantajları
1. **Immutability (Değişmezlik)**:
    - Nesnenin kritik özelliklerinin değiştirilmesini engeller
    - Thread-safe kod yazımını kolaylaştırır

2. **Güvenlik**:
    - Hassas verilerin yanlışlıkla değiştirilmesini önler
    - Kimlik numarası, doğum tarihi gibi değişmemesi gereken bilgiler için idealdir

3. **Kod Kalitesi**:
    - Daha öngörülebilir kod yazımını sağlar
    - Hata ayıklamayı kolaylaştırır

## Kullanım Senaryoları

```csharp
public class BankaHesabi
{
    // Değişmeyecek bilgiler
    public string HesapNo { get; init; }
    public string IBAN { get; init; }
    public DateTime HesapAcilisTarihi { get; init; }
    
    // Değişebilir bilgiler
    public decimal Bakiye { get; set; }
    public string SubeKodu { get; set; }
}

// Record ile kullanım
public record Musteri
{
    public string MusteriNo { get; init; }
    public string Ad { get; init; }
    public string Soyad { get; init; }
}
```

## Init vs Readonly
- `readonly` sadece field'lar için kullanılabilirken, `init` property'ler için kullanılır
- `init` daha esnek bir kullanım sunar ve object initializer syntax'ı destekler
- `readonly` sadece constructor'da değer atanmasına izin verirken, `init` hem constructor'da hem de object initializer'da değer atanmasına izin verir

## En İyi Pratikler
- Değişmemesi gereken özellikleri `init` ile işaretleyin
- Domain modellerinde kimlik bilgileri için kullanın
- İş kuralları gereği sabit kalması gereken değerler için tercih edin
- Record'larla birlikte kullanarak immutable tipler oluşturun

## C# 9.0 ve Sonrası
- Init-only properties C# 9.0 ile gelmiştir
- Record types ile birlikte kullanıldığında çok güçlü bir immutability desteği sağlar
- .NET 5 ve üzeri versiyonlarda kullanılabilir

---

> **Not**: Init-only properties, özellikle Domain-Driven Design (DDD) yaklaşımında entity'lerin değişmez özelliklerini tanımlarken çok kullanışlıdır.