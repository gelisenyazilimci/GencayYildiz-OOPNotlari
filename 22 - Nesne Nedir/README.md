# Nesne Nedir?

Nesne, canlı bir organizma gibidir. Birbiriyle ilişkili ve anlamlı verileri içinde barındıran, sadece veri tutmakla kalmayıp bu veriler üzerinde işlemler yapabilen ve sonuçlar üretebilen bir yapılandırmadır.

Günlük hayattan bir örnek vermek gerekirse: Ali adında bir kişiyi düşünelim. Ali'nin göz rengi, adı, soyadı, ayak numarası gibi özellikleri bir araya geldiğinde bir nesneyi oluşturur.

Programlama dünyasında ise nesne, olguya dair verileri tutan ve bu verilerle işlem yapabildiğimiz class (sınıf) yapılarından üretilen bir kavramdır. Class'ı nesnenin içindeki organizma gibi düşünebiliriz (kalıtım gibi biyolojik konulara şimdilik girmiyoruz).

## Nesne Nedir? (Programatik Açıdan)

- Nesneler, class yapılandırmalarından üretilen verilerdir
- Complex (karmaşık) veri türlerine sahiptirler. Teknik dokümanlarda "complex type" ifadesiyle karşılaşırsanız, bunun bir nesneye işaret ettiğini bilmelisiniz

### Örnek:
Bir şirketteki çalışanları temsil edecek bir nesne oluşturalım:

```csharp
class Personal { 
    int adi, soyadi; 
    bool medeniHali; 
    int yas; 
}
```

Bu örnekte, bir çalışanı temsil eden temel özellikleri tanımladık. Ev kirası veya araba markası gibi yan özellikler bir çalışanı doğrudan temsil etmediği için dahil edilmemiştir. Bu tanımlanan değerler "field" türünde olmak zorundadır.

## Neden Nesne Kullanıyoruz?

Bu sorunun birçok cevabı olmakla birlikte, pratik bir örnek verelim: 10 öğrencinin verisini tutmak istediğinizi düşünün. Bu verileri tek tek manuel olarak yönetmek yerine, nesne yapısı kullanarak daha düzenli ve yönetilebilir bir sistem oluşturabilirsiniz. Bu, programlamanın temel prensiplerinden biridir.

## Bir Sınıftan Nesne Üretme/Türetme/Oluşturma

```csharp
class MyClass 
{
    public int A {get; set;}
    public void X () {}
}
```

Sınıfı oluşturduktan sonra nesneyi kullanabilmek için ["new" operatörünü](../23%20-%20New%20Operator/README.md) kullanmamız gerekir. Bu konunun detayları için [New Operatörü](../23%20-%20New%20Operator/README.md) bölümüne bakabilirsiniz.