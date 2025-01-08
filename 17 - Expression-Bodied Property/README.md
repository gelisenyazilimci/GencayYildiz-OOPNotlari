# Expression-Bodied Property

---
- Tanımlanan property'de # Expression-Bodied Property

---

## Temel Bilgiler
- Expression-bodied property, C# 6.0 ile gelen ve property tanımlamayı daha kısa ve öz hale getiren bir özelliktir.
- [Lambda Expression](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/lambda-expressions) (`=>`) kullanarak tek satırda property tanımlamamızı sağlar.
- Özellikle hesaplama gerektiren read-only property'lerde çok kullanışlıdır.

## Geleneksel Property vs Expression-Bodied Property

```csharp
// Geleneksel Property
public string AdSoyad
{
    get { return $"{Ad} {Soyad}"; }
}

// Expression-Bodied Property
public string AdSoyad => $"{Ad} {Soyad}";
```

## Önemli Noktalar
- Bu şekilde expression-bodied ile imzalanan property'ler varsayılan olarak read-only'dir.
- Sadece get accessor'ı olan property'ler için kullanılabilir.
- Birden fazla satır gerektiren işlemler için uygun değildir.
- Performans açısından normal property'lerle aynıdır, sadece syntax sugar'dır.

## Kullanım Örnekleri

```csharp
public class Calisan
{
    public string Ad { get; set; }
    public string Soyad { get; set; }
    public decimal MaasGunluk { get; set; }
    
    // Basit string birleştirme
    public string TamAd => $"{Ad} {Soyad}";
    
    // Hesaplama içeren property
    public decimal AylikMaas => MaasGunluk * 30;
    
    // Ternary operatör kullanımı
    public string MaasKategorisi => AylikMaas > 10000 ? "Yüksek" : "Normal";
    
    // LINQ ile kullanım
    public int EnBuyukSayi => new[] { 1, 2, 3, 4, 5 }.Max();
}
```

## Ne Zaman Kullanmalı?
1. **Basit Hesaplamalar**:
```csharp
public double Alan => Genislik * Yukseklik;
```

2. **String Formatlama**:
```csharp
public string Baslik => $"Sayın {Ad} {Soyad}";
```

3. **Koşullu İfadeler**:
```csharp
public bool YetiskinMi => Yas >= 18;
```

## Ne Zaman Kullanılmamalı?
1. **Karmaşık Logic**:
```csharp
// Bunun yerine normal property kullanın
public decimal KarHesapla => 
    Gelir - Gider - Vergiler - Masraflar; // Karmaşık hesaplamalar için uygun değil
```

2. **Exception Handling Gerektiren Durumlar**:
```csharp
// Bunun yerine normal property kullanın
public string DosyaIcerigi => 
    File.ReadAllText("dosya.txt"); // Hata yönetimi gerektiğinde uygun değil
```

## İyi Pratikler
- Tek satırda ifade edilebilecek basit işlemler için kullanın
- Okunabilirliği artırmak için karmaşık ifadelerden kaçının
- Hesaplama gerektiren read-only property'lerde tercih edin
- Performance-critical durumlarda normal property'lerle aynı olduğunu unutmayın

## C# 7.0+ ile Gelen Yenilikler
C# 7.0 ile birlikte set accessor'lar için de expression-bodied syntax kullanılabilir:

```csharp
private string _ad;
public string Ad
{
    get => _ad;
    set => _ad = value?.Trim();
}
```

---

> **Not**: Expression-bodied member'lar sadece property'lerde değil, metotlarda, constructor'larda ve diğer class member'larında da kullanılabilir. kullanmamızı sağlayan söz dizilimidir.
---
- Expression-Bodied Automatically Property Initializers'ın akrabası diyebiliriz...