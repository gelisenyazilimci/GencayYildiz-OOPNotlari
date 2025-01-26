# Init-Only Properties

---

- C# 9.0 ile, herhangi bir nesnenin property'lerine ilk değerlerin atanması ve sonraki süreçte bu değerlerin **değiştirilmemesini** garanti altına alan `Init-Only Properties` özelliği tanıtılmıştır.
- Bu özellik sayesinde, nesnenin sadece ilk oluşturulma anında property'lere değer atanabilir ve böylece iş kuralları gereği runtime'da değişmemesi gereken değerler için ideal bir önlem alınır.
- `Init-Only Properties`, developer açısından değişmemesi gereken property değerlerinin **yanlışlıkla** değiştirilmesini engeller, olası hata ve bug'ları azaltır.
- `Getter-Only Properties` ile arasındaki fark şudur: `Getter-Only Properties` yalnızca `Object Initializer` işlevselliği ile uyumlu değildir, ancak `Init-Only Properties` bu avantajı sunar. 

```csharp
Book book = new Book 
{
    Author = "Robert Greene",
    Name = "İnsan Doğasının Yasaları"
};
```

- Eğer bir nesnenin property'lerine değer atamaya çalıştığınızda hata alıyorsanız, bu property'ler `Getter-Only Properties` olarak tanımlanmış olabilir.
- Eğer nesneyi oluşturduğunuz anda property'lere değer atamak istiyor ve ardından bu değerlerin sadece okunabilir (`readonly`) olmasını istiyorsanız, `Init-Only Properties` kullanmanız gerekir.
- `Init-Only Properties` özelliği, `init` keyword'ü ile tanımlanır.

### Init-Only Properties Örneği

`Getter-Only Properties` yerine `Init-Only Properties` kullandığımız bir örnek:

```csharp
Book book = new Book 
{
    Author = "Robert Greene",
    Name = "İnsan Doğasının Yasaları"
};
book.Author = "Başka Bir Kitap"; // HATA: Init-Only Properties, sadece ilk atamayı destekler.
```
- Yukarıdaki kodda `Author` ve `Name` property'lerine nesne oluşturulurken değer atanabilir, ancak nesne oluşturulduktan sonra değer değiştirilmeye çalışılırsa hata alırsınız.
- Bu özellik sayesinde property'ler, oluşturulma sonrasında **readonly** olur.

### Init-Only Properties Kullanım Şekli

```csharp
class Book
{
    public string Name { get; init; }
    public string Author { get; init; }
}
```

- Bu şekilde tanımlanan `Init-Only Properties`, `init` keyword'ü olmadan çalışmaz.
- Yapısı gereği `set` bloğu kullanılamaz. `get; init;` bir araya geldiğinde property, readonly olur.
- İlk değerler constructor veya auto-property initializer'lar üzerinden atanabileceği gibi `Object Initializer` ile de atanabilir.
- Eğer **getter-only-properties** yerine çalışmaktansa readonly bir field işlemler yapmanız gerekiyorsa eğer aşağıdaki gibi `init` bizlere eşlik edebilmektedir

```csharp
class Book 
{
    private readonly string name;
    private readonly string author; 

    public string Name { get => name; init => name = value; }
    public string Author { get => author; init => author = value; }
}
```

---

## Kısa Özet

1. `Init-Only Properties`, property'lerin sadece nesne oluşturulurken değer almasını sağlar.
2. `init` anahtar kelimesi ile tanımlanır ve `set` bloğunu desteklemez.
3. `Object Initializer` işlevselliği ile uyumludur ve runtime sırasında property'lerin değiştirilmesini engeller.
4. `Getter-Only Properties` ile farkı, **Object Initializear'dan** değer alabilmesidir.
5. Kod güvenliği ve yazılım hatalarını önlemek için iş kurallarında kullanılabilir.
