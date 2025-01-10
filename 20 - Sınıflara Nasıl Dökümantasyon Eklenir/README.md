# Sınıflara Nasıl Dökümantasyon Eklenir

Kod yazarken dokümantasyon, hem kendi kodunuzu hem de başkalarının kodunuzu anlamasını kolaylaştıran önemli bir unsurdur. C# dilinde XML tabanlı açıklama etiketleri olan **`<summary>`** ve **`<param>`**, kodunuzu daha okunabilir ve anlaşılır hale getirmek için güçlü araçlardır. Bu doküman, bu etiketlerin nasıl kullanılacağını ve neden önemli olduğunu anlatmaktadır.

---

## `<summary>` Nedir?

**`<summary>`** etiketi, bir sınıfın, metodun, özelliğin veya başka bir kod öğesinin ne yaptığını açıklamak için kullanılır.
Bu açıklamalar, kod üzerinde çalışan diğer geliştiricilerin (ve gelecekte sizin) kodun amacını hızlıca anlamasına yardımcı olur.

### **Faydaları:**
1. Kodun anlaşılabilirliğini artırır.
2. Visual Studio'nun veya herhangi ide'nin Intellisense özelliğiyle entegrasyon sağlar.
3. Harici dokümantasyon üretiminde kullanılır.
4. Ekip çalışmasında iletişim maliyetlerini azaltır.

### **Kullanımı:**
```csharp
/// <summary>
/// Bu sınıf, bir öğrencinin bilgilerini ve notlarını tutar.
/// </summary>
public class Ogrenci
{
    public string Ad { get; set; }
    public string Soyad { get; set; }
    public int Not { get; set; }
}
```

---

## `<param>` Nedir?

**`<param>`** etiketi, bir metodun aldığı parametrelerin ne işe yaradığını açıklamak için kullanılır. Her bir parametre için ayrı bir **`<param>`** etiketi yazılır.

### **Faydaları:**
1. Metodun parametrelerinin anlamını açıklar.
2. Intellisense ile kullanımı kolaylaştırır.
3. Yanlış parametre kullanımını azaltır.
4. Harici dokümantasyon araçları tarafından kullanılabilir.

### **Kullanımı:**
```csharp
/// <summary>
/// İki sayıyı toplar ve sonucu döndürür.
/// </summary>
/// <param name="a">Birinci sayı.</param>
/// <param name="b">İkinci sayı.</param>
/// <returns>Toplam sonucu.</returns>
public int Topla(int a, int b)
{
    return a + b;
}
```

---

## `<summary>` ve `<param>` Birlikte Kullanımı

Bu iki etiket genellikle birlikte kullanılır ve bir metodun hem genel açıklamasını hem de parametrelerinin detaylarını verir. Aşağıda detaylı bir örnek verilmiştir:

### **Örnek Kullanım:**
```csharp
/// <summary>
/// Kullanıcı girişini doğrular.
/// </summary>
/// <param name="username">Kullanıcının kullanıcı adı.</param>
/// <param name="password">Kullanıcının şifresi.</param>
/// <param name="isPersistent">Oturumun kalıcı olup olmayacağını belirtir.</param>
/// <returns>Giriş başarılı ise true, aksi halde false döner.</returns>
public bool ValidateUser(string username, string password, bool isPersistent)
{
    // Kod burada
    return true;
}
```

### **Intellisense Görünümü:**
Bu açıklamalar, Visual Studio'da veya herhangi bir ide'de metodun üzerine geldiğinizde ya da kullanırken otomatik olarak gösterilir:

![Intellisense Örneği](https://learn.microsoft.com/en-us/visualstudio/ide/media/vs-2022/using-intellisense/intellisense-list-members.png?view=vs-2017&viewFallbackFrom=vs-2022)

---

## Neden Kullanmalıyız?
- **Profesyonellik:** Kodunuzu daha profesyonel ve standartlara uygun hale getirir.
- **Okunabilirlik:** Karmaşık kodlar bile kolayca anlaşılır.
- **Bakım Kolaylığı:** Gelecekte yapılacak düzenlemelerde kolaylık sağlar.
- **Ekip Çalışması:** Başka geliştiricilerin kodunuzu hızlıca anlamasını sağlar.

---

## İyi Pratikler
1. **Kısa ve Öz Olun:** Açıklamalar çok uzun olmamalı, doğrudan işlevi açıklamalıdır.
2. **Tutarlılık Sağlayın:** Tüm sınıf ve metotlarda aynı yapıyı kullanın.
3. **Dokümantasyonu Güncel Tutun:** Kod değiştikçe açıklamaları da güncelleyin.

---

## Sonuç
C#’ta **`<summary>`** ve **`<param>`** etiketlerini kullanmak, hem kendi kodunuzun hem de takım arkadaşlarınızın işini kolaylaştırır. Bu etiketler, kodunuzu profesyonel, okunabilir ve sürdürülebilir hale getirir.

Daha fazla bilgi için [Microsoft Docs](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/xmldoc/) sayfasına bakmanızı tavsiye ederim.
