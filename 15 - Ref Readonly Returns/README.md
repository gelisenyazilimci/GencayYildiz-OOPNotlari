# Ref Readonly Returns

--- 

- Ref Readonly returns, bir sınıf (class) içerisindeki field'ı referansıyla döndürmemizi sağlayan ve biryandan da bu değişkenin değerini read only yapan özelliktir. Bu özellik C# 7.2 ile birlikte gelmiştir ve oldukça spesifik senaryolarda kullanılır.

## Neden Kullanılır?

- Performans kritik uygulamalarda, özellikle büyük veri yapılarıyla çalışırken, gereksiz kopya oluşturmadan veriye güvenli erişim sağlamak için kullanılır.
- Değerin kopyalanmasını önlerken (`ref` sayesinde), aynı zamanda değiştirilmesini de engeller (`readonly` sayesinde).
- Özellikle game development, yüksek frekanslı trading sistemleri veya büyük veri işleme uygulamalarında tercih edilebilir.

## Kullanım Örneği

```csharp
public class PerformanceCriticalData
{
    private readonly BigStruct _data; // Büyük boyutlu bir struct

    public ref readonly BigStruct GetData()
    {
        return ref _data;
    }
}
```

## Dikkat Edilmesi Gerekenler

1. Bu özellik ileri düzey bir C# özelliğidir ve günlük uygulamalarda nadiren ihtiyaç duyulur.
2. Yanlış kullanımı performans kazancı yerine kayıplarına yol açabilir.
3. Sadece aşağıdaki durumlarda kullanımı düşünülmelidir:
   - Struct gibi büyük değer tiplerinin kopyalanmasını önlemek istediğinizde
   - Verinin değiştirilmemesi gerektiğinde
   - Performansın kritik önemde olduğu durumlarda

## Ne Zaman Kullanılmamalı?

- Küçük boyutlu değer tipleri için (int, bool, vb.)
- Reference type'lar için (zaten referans olarak geçilirler)
- CRUD operasyonları yapılan normal iş uygulamalarında
- Kodun okunabilirliği ve maintainability'nin performanstan daha önemli olduğu durumlarda

## Örnek Senaryo

```csharp
public struct LargeVector
{
    public double X, Y, Z, W;
    // Diğer büyük miktarda veri...
}

public class VectorProcessor
{
    private LargeVector[] _vectors = new LargeVector[1000000];

    // Kötü kullanım - Her çağrıda büyük struct kopyalanır
    public LargeVector GetVector(int index)
    {
        return _vectors[index];
    }

    // İyi kullanım - Kopya oluşturmaz ve değiştirilmeyi engeller
    public ref readonly LargeVector GetVectorEfficient(int index)
    {
        return ref _vectors[index];
    }
}
```

## Özet

Bu özellik, çok spesifik performans gereksinimlerinde kullanılmak üzere tasarlanmıştır. Normal iş uygulamalarında kullanımı genellikle over-engineering olarak değerlendirilir. Kullanmadan önce gerçekten ihtiyaç olup olmadığı dikkatle değerlendirilmelidir.

---

### Önemli kaynaklar.

Burdaki kaynakları okuyup üzerinden geçmek önemli!!

[C# 7.2 – Ref Readonly Returns](https://www.gencayyildiz.com/blog/c-7-2-ref-readonly-returns/)

[ref ve params kullanımı](https://www.gencayyildiz.com/blog/c-metodlarda-ref-ve-params-kullanimi/)

[learn.microsoft.com / ref readonly parameters ](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/proposals/csharp-12.0/ref-readonly-parameters)
