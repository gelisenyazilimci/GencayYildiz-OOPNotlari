# This Keyword

---

## This Nedir ve Sınıf Nesnesini Neden Temsil Eder?
- `this` keyword'ü, bir sınıfın o anki nesne örneğini (instance) temsil eder.
- Sınıfın içerisindeki metotlarda, property'lerde veya constructor'larda kullanılabilir.
- O anki nesnenin referansını taşır ve sınıfın üyelerine erişim sağlar.

```csharp
public class Personel
{
    private string ad;
    
    public void BilgiYazdir()
    {
        Console.WriteLine($"Bu nesnenin referansı: {this}");
        // this, bu metodu çağıran Personel nesnesini temsil eder
    }
}
```
 
- ### Yukarıdaki örnek kodun çıktısı: 
```
Bu nesnenin referansı: NamespaceAdı.Personel
```

## Field ve Parametre İsim Çakışmalarını Çözme
- Aynı isme sahip field ve parametre olduğunda, `this` keyword'ü field'ı işaret etmek için kullanılır.
- Bu kullanım, 1. sorudaki this'in nesneyi temsil etmesiyle doğrudan bağlantılıdır çünkü field'lar nesneye aittir.
- `this` keyword'ü ilgili class yapılanmasının o anki nesnesine karşılık gelir. This kullanmak zorunda değiliz. (1. madde de yazdığı gibi field ve parametre aynı isme sahip ise kullanmak zorundasınız! )

```csharp
public class Ogrenci
{
    private string ad; // field
    
    public void SetAd(string ad) // parametre
    {
        this.ad = ad; // this.ad -> field'ı, ad -> parametreyi temsil eder
    }
}
```

## Constructor Chaining (Constructor'lar Arası Geçiş)
- Bir constructor'dan başka bir constructor'ı çağırmak için `this()` syntax'ı kullanılır.
- Bu sayede kod tekrarından kaçınılır ve constructor'lar arası hiyerarşi sağlanır.
- Buraya çok ileride ve ayrıntılı tekrardan değineceğiz fakat aşağıda size küçük bir örnek bıraktım merak edenler için :)

```csharp
public class Urun
{
    private string ad;
    private decimal fiyat;
    
    // Ana constructor
    public Urun(string ad, decimal fiyat)
    {
        this.ad = ad;
        this.fiyat = fiyat;
    }
    
    // Sadece ad alan constructor
    public Urun(string ad) : this(ad, 0)
    {
        // Ana constructor'ı çağırır
    }
    
    // Parametresiz constructor
    public Urun() : this("İsimsiz", 0)
    {
        // Ana constructor'ı çağırır
    }
}
```

---

## Örnek Kullanım Senaryoları

```csharp
public class Musteri
{
    private string ad;
    private string soyad;
    private int yas;
    
    // Constructor chaining örneği
    public Musteri() : this("Bilinmiyor", "Bilinmiyor")
    {
    }
    
    public Musteri(string ad, string soyad) : this(ad, soyad, 0)
    {
    }
    
    public Musteri(string ad, string soyad, int yas)
    {
        this.ad = ad;
        this.soyad = soyad;
        this.yas = yas;
    }
    
    // Field-parametre çakışması örneği
    public void BilgileriGuncelle(string ad, string soyad)
    {
        this.ad = ad;        // this ile field'ı işaret ediyoruz
        this.soyad = soyad;  // this ile field'ı işaret ediyoruz
    }
    
    // Nesne referansını kullanma örneği
    public Musteri KendiniKopyala()
    {
        return new Musteri(this.ad, this.soyad, this.yas);
    }
}
```

## Önemli Noktalar
- `this` keyword'ü sadece instance metotlarda kullanılabilir, static metotlarda kullanılamaz.
- Constructor chaining'de döngüsel çağrılardan kaçınılmalıdır.
- `this` kullanımı her zaman zorunlu değildir, isim çakışması olmayan durumlarda opsiyoneldir.

---