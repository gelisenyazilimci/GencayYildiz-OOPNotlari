# Automatically Property Initializers

---

- Bir property'nin ilk değerini nesne ayağıya kaldırır kaldırılmaz aşağıdaki gibi verebilirsiniz. Bu özellik C# 6.0 ile birlikte gelmiştir ve property'lerin başlangıç değerlerini daha temiz ve okunabilir bir şekilde atamamızı sağlar.

```csharp
public string FirstName { get; set; } = "Jane";
public string SecondName { get; set; } = "Ohm";
public int age { get; set; } = 31; 
```

- Automatically Property Initializers özelliği sayesinde read only olan prop'lara hızlıca değer atanabilir. Bu, özellikle immutable (değişmez) sınıflar oluştururken çok kullanışlıdır.

- Bu özellik constructor'da yapılan başlangıç değeri atamalarını daha temiz hale getirir. Örneğin, aşağıdaki iki kod bloğu aynı işi yapar:

```csharp
// Eski yöntem (Constructor kullanarak)
public class Person
{
    public string DefaultCountry { get; }
    public List<string> AllowedLanguages { get; }

    public Person()
    {
        DefaultCountry = "Türkiye";
        AllowedLanguages = new List<string> { "Türkçe", "İngilizce" };
    }
}

// Yeni yöntem (Auto Property Initializers kullanarak)
public class Person
{
    public string DefaultCountry { get; } = "Türkiye";
    public List<string> AllowedLanguages { get; } = new List<string> { "Türkçe", "İngilizce" };
}
```

- Dikkat edilmesi gereken noktalar:
  - Property initializer'lar constructor'dan önce çalışır.
  - Readonly property'ler için sadece get; tanımlaması yeterlidir.
  ```csharp
  public string Name {get;} = "Ali";
  ```
  - Complex tipleri (örn: List, Dictionary) de initialize edebilirsiniz
  ```csharp
  public List<int> Numbers { get; set; } = new List<int> { 1, 2, 3 };
  public Dictionary<string, int> Ages { get; set; } = new Dictionary<string, int>
  {
      ["Ali"] = 25,
      ["Ayşe"] = 30
  };
  ```
  - Expression kullanabilirsiniz (örn: DateTime.Now, Math.PI * 2)
  ```csharp
  public DateTime CreatedDate { get; } = DateTime.Now;
  public double CirclePerimeter { get; } = Math.PI * 2;
  ```

- Bu özellik özellikle configuration sınıfları, default değerler ve immutable objeler oluştururken çok kullanışlıdır. 