# Full Property

---

## Temel Bilgiler
- En sade property yapılandırmasıdır.
- İçerisinde get ve set blokları tanımlıdır.
- Property'ler, sınıf içindeki private field'lara kontrollü erişim sağlar.

---

![img.png](img.png)

## Property Yapısı
- [erişim belirleyicisi] = public, private, protected, internal, protected internal ve private protected olmak üzere 6 farklı erişim belirleyici vardır.
- [geri dönüş değeri] = int, string, bool, double vb. herhangi bir veri tipi olabilir.
- [property adı] = Pascal Case kuralına göre isimlendirilir (örn: FirstName, Age)

## Önemli Noktalar
- Full property'lerde set bloğu tanımlanmazsa sadece okunabilir (read only), get bloğu tanımlanmazsa sadece yazılabilir (write only) olur.
- **Property'ler temsil ettikleri field'ın veri tipiyle aynı olmak zorundadır.**
- Property isimleri, temsil ettikleri field'ların baş harfi büyük olacak şekilde isimlendirilir (camelCase -> PascalCase).
- get bloğu, property üzerinden değer okunmak istendiğinde çalışır.
- set bloğu, property'e değer atanmak istendiğinde çalışır ve value keyword'ü ile gelen değeri yakalar.

## Örnek Kullanım

```csharp
class MyClass 
{
    int age;
    string b; 
    public int Age 
    {
        get 
        {
            // property üzerinden değer talep edildiğinde bu blok tetiklenir.
            // Yani değer buradan gönderilir.
            return age - 10; // yaşı 50 olan birisini karşı taraf 40 olarak görür.
        }
        
        set 
        {
            age = value;
        }   
    }
}
```

## Property Kullanım Örnekleri
- **Console.WriteLine(MyClass.Age)** : get metodu tetiklenir ve değer okunur.
- **MyClass.Age = 31** : set metodu tetiklenir, value parametresi 31 değerini alır ve age field'ına atanır. Get metodu çağrıldığında 21 değeri döner (age - 10 işleminden dolayı).

## Ek Bilgiler
- Property'ler, field'lara doğrudan erişimi engelleyerek enkapsülasyon (kapsülleme) sağlar.
- get ve set blokları içerisinde validation (doğrulama) işlemleri yapılabilir.
- Property'ler sayesinde field değerleri üzerinde kontrollü değişiklikler yapılabilir.
- Backing field olmadan da property tanımlanabilir (auto-implemented properties).

## Gerçek Hayat Örneği - Banka Hesabı

```csharp
public class Banka
{
    private double bakiye; // backing field
    private const double GunlukParaCekmeLimiti = 5000;
    
    public double Bakiye
    {
        get
        {
            // Bakiye bilgisi istenmeden önce günlük faiz hesaplaması yapılabilir
            HesabaGunlukFaizEkle();
            return bakiye;
        }
        set
        {
            if (value < 0)
            {
                throw new ArgumentException("Bakiye negatif olamaz!");
            }
            
            // Para çekme işlemi
            if (value <= bakiye)
            {
                double cekilmekIstenen = bakiye - value;
                if (cekilmekIstenen > GunlukParaCekmeLimiti)
                {
                    throw new InvalidOperationException($"Günlük para çekme limiti {GunlukParaCekmeLimiti:C2}'dir!");
                }
            }
            
            bakiye = value;
        }
    }
    
    private void HesabaGunlukFaizEkle()
    {
        // Örnek: Günlük %0.1 faiz
        bakiye += bakiye * 0.001;
    }
}
```

## Banka Sınıfı Kullanım Örnekleri

```csharp
Banka hesap = new Banka();

// Para yatırma
try
{
    hesap.Bakiye = 1000; // Set bloğu çalışır
    Console.WriteLine($"Güncel bakiye: {hesap.Bakiye:C2}"); // Get bloğu çalışır
}
catch (ArgumentException ex)
{
    Console.WriteLine($"Hata: {ex.Message}");
}

// Para çekme
try
{
    hesap.Bakiye -= 3000; // Günlük limit dahilinde
}
catch (InvalidOperationException ex)
{
    Console.WriteLine($"Hata: {ex.Message}");
}
```

## Property'lerin Avantajları
- **Veri Doğrulama**: Yukarıdaki örnekte görüldüğü gibi, set bloğunda bakiyenin negatif olması engelleniyor.
- **İş Kuralları**: Günlük para çekme limiti gibi iş kuralları property içinde uygulanabilir.
- **Otomatik Hesaplama**: Get bloğunda faiz hesaplaması gibi otomatik işlemler yapılabilir.
- **Güvenlik**: Private field'a doğrudan erişim engellendiği için veri güvenliği sağlanır.

## Property Kullanım Senaryoları
1. **Sadece Okunabilir Property**:
```csharp
public double ToplamBakiye
{
    get { return bakiye + birikimHesabi; }
}
```

2. **Sadece Yazılabilir Property**:
```csharp
public string Sifre
{
    set { sifre = HashPassword(value); }
}
```

3. **Auto-Implemented Property**:
```csharp
public string HesapNo { get; private set; }
```

## En İyi Pratikler
- Property isimleri açıklayıcı olmalıdır
- Set bloğunda mutlaka gerekli validasyonlar yapılmalıdır
- Get bloğu mümkün olduğunca hızlı çalışmalıdır
- İş mantığı karmaşıksa, ayrı metodlara taşınmalıdır
- Exception fırlatırken özel exception sınıfları kullanılmalıdır
---