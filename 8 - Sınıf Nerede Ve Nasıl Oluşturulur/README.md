# Sınıf Nerede ve Nasıl Oluşturulur?

---

## Giriş

- Nesne tabanlı programlama (OOP) dünyasında sınıflar (classes), nesnelerin şablonlarıdır. Her programlama dilinde OOP'yi destekleyen temel bir yapıdır.
- C# dilinde, bir sınıfı tanımlamak ve uygun bir yerde oluşturmak, kodun yapısal ve okunabilir olmasını sağlar.

---

## Sınıfı Nasıl Oluştururuz?

1. **Sınıf Tanımı**
    - Sınıf oluşturmak için `class` anahtar sözcüğü kullanılır.
    - Bir sınıf ismi tanımlanır ve süs parantezleri içinde sınıfın içeriği yazılır.

### Temel Örnek:

```csharp
class Araba {
    public string Marka { get; set; }
    public string Model { get; set; }

    public void HareketEt() {
        Console.WriteLine($"{Marka} {Model} hareket ediyor.");
    }
}
```

### Açıklama:

- `class Araba` ile bir sınıf oluşturulur.
- `Marka` ve `Model` isimli iki özellik tanımlanır.
- `HareketEt` isimli bir metot, sınıfın davranışını tanımlar.

---

## Sınıf Nerede Oluşturulabilir?

1. **Namespace İçerisinde:**
    - Sınıflar genellikle `namespace` blokları içerisinde tanımlanır.
    - Bu yaklaşım, kodu mantıksal bloklara ayırır ve yeniden kullanılabilir hale getirir.

### Örnek:

```csharp
namespace Araçlar {
    class Araba {
        public string Marka { get; set; }
    }
}
```

2. **Namespace Dışında:**
    - Sınıflar namespace dışında da tanımlanabilir ancak bu yaklaşım nadiren tercih edilir.
    - Namespace dışı sınıflar, daha güvenliksizdir ve çakışma riski taşır.

### Örnek:

```csharp
class Araba {
    public string Model { get; set; }
}
```

3. **Sınıf İçerisinde (Nested Types):**
    - Bir sınıf, başka bir sınıfın içinde tanımlanabilir.
    - Bu yaklaşım, sınıflar arasında mantıksal bir ilişki kurmak için kullanılır.

### Örnek:

```csharp
class Motor {
    public class Parça {
        public string ParcaAdi { get; set; }
    }
}
```

4. **Sınıf Dışında:**
    - Bağımsız bir yapıda sınıf oluşturabilirsiniz ancak bu yaklaşım genellikle tavsiye edilmez.

### Örnek:

```csharp
class BağımsızSınıf {
    public string Bilgi { get; set; }
}
```

---

## Sınıf Tanımlamasında Dikkat Edilmesi Gerekenler

1. **Aynı İsim Kullanılamaz:**
    - Aynı namespace veya blok içinde birden fazla sınıf aynı isimle tanımlanamaz.

2. **Namespace Kullanımı:**
    - Farklı namespace’lerde tanımlanan sınıflar, isimleriyle birlikte namespace adı verilerek çağrılır.

### Örnek:

```csharp
namespace Araçlar {
    class Araba {}
}

namespace Evler {
    class Araba {}
}

// Kullanım
Araçlar.Araba araba1 = new Araçlar.Araba();
Evler.Araba araba2 = new Evler.Araba();
```

---

## Sonuç

- C# dilinde sınıf oluşturmak, kodun modüler ve düzenli olmasını sağlar.
- Sınıfın nerede ve nasıl tanımlandığı, projenin organizasyonu açısından kritik bir rol oynar.
- Namespace kullanımı, kodun okunabilirliğini ve yapısal bütünlüğünü artırır.

Bu bölümde, sınıfların nerede ve nasıl oluşturulur sorusunu cevapladık ve bu programlama üzerindeki etkisini detaylı olarak inceledik.