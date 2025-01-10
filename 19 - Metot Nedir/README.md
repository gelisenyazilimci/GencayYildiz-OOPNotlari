# Metot

---

## Temel Bilgiler
- Nesne üzerinde, field'larda ki yahut dışarıdan parametreler eşliğinde gelen değerler üzerinde işlemler yapmamızı sağlayan temel programatik parçalardır.
- Metotlar, bir sınıfın davranışlarını temsil eder ve belirli bir işi yapmak için tasarlanmış kod bloklarıdır.
- Property'lerden farklı olarak, metotlar daha karmaşık işlemleri gerçekleştirebilir ve birden fazla parametre alabilirler.

## Metot vs Property Karşılaştırması
- **Property**: Bir sınıfın özelliklerini temsil eder, genellikle veri okuma/yazma işlemleri için kullanılır. (Sıra sıra ilerliyorsanız biliyorsunuz varsayıyorum ama tekrardan hatırlatmakta fayda var.)
- **Metot**: Bir sınıfın davranışlarını temsil eder, işlem yapmak ve sonuç döndürmek için kullanılır

## Metot Yapısı
```csharp
[erişim belirleyici] [geri dönüş tipi] MetotAdi(parametreler)
{
    // Metot gövdesi
    // İşlemler
    return sonuc; // Eğer geri dönüş tipi void değilse
}
```

## Örnek Kullanımlar

```csharp
public class Hesaplama
{
    // Parametre alan ve değer döndüren metot
    public int Topla(int sayi1, int sayi2)
    {
        return sayi1 + sayi2;
    }
    
    // Void metot - değer döndürmez
    public void EkranaYaz(string mesaj)
    {
        Console.WriteLine(mesaj);
    }
    
    // Varsayılan parametreli metot
    public double HesaplaKdv(double fiyat, double kdvOrani = 0.18)
    {
        return fiyat * (1 + kdvOrani);
    }
    
    // Çoklu parametre alan metot
    public double OrtalamaHesapla(params int[] sayilar)
    {
        return sayilar.Average();
    }
}
```

## Metot Özellikleri
1. **Parametreler**:
    - Metotlar sıfır veya daha fazla parametre alabilir
    - Parametreler farklı veri tiplerinde olabilir
    - Optional ve named parametreler kullanılabilir

2. **Geri Dönüş Değeri**:
    - void: Değer döndürmez
    - Herhangi bir veri tipi: int, string, bool, custom class vb.
    - Task: Asenkron metotlarda kullanılır

3. **Erişim Belirleyiciler**:
   - public: Herkese açık
   - private: Sadece sınıf içinden erişilebilir
   - protected: Sadece sınıf ve türetilen sınıflardan erişilebilir
   - internal: Aynı assembly içinden erişilebilir
   - protected internal: Protected veya internal erişimine sahip olan herkes erişebilir
   - private protected: Aynı assembly içindeki türetilmiş sınıflardan erişilebilir
    

## İyi Pratikler
- Metot isimleri açıklayıcı olmalıdır (örn: HesaplaKdv, KullaniciKaydet)
- Bir metot sadece bir iş yapmalıdır (Single Responsibility)
- Metot gövdesi çok uzun olmamalıdır
- Parametreler anlamlı isimlendirilmelidir
- XML documentation kullanılmalıdır

## Örnek Senaryo

```csharp
public class BankaHesabi
{
    private decimal bakiye;
    
    // Property - hesabın özelliği
    public decimal Bakiye
    {
        get { return bakiye; }
    }
    
    // Metot - hesap üzerinde işlem yapma
    public void ParaYatir(decimal miktar)
    {
        if (miktar <= 0)
            throw new ArgumentException("Miktar pozitif olmalıdır.");
            
        bakiye += miktar;
    }
    
    // Metot - hesap üzerinde işlem yapma
    public bool ParaCek(decimal miktar)
    {
        if (miktar <= 0)
            throw new ArgumentException("Miktar pozitif olmalıdır.");
            
        if (bakiye >= miktar)
        {
            bakiye -= miktar;
            return true;
        }
        return false;
    }
}
```

## Metot Türleri
1. **Instance Metotlar**: Nesne örneği üzerinden çağrılır
2. **Static Metotlar**: Sınıf üzerinden direkt çağrılır
3. **Extension Metotlar**: Var olan tiplere yeni metotlar ekler
4. **Async Metotlar**: Asenkron işlemler için kullanılır

---

> **Not**: Metotlar, OOP'nin temel yapı taşlarından biridir ve kodun yeniden kullanılabilirliğini artırır.