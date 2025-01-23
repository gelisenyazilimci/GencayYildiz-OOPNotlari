## **`MemberwiseClone` Nedir?**

- **`MemberwiseClone`**, C# dilinde `Object` sınıfında tanımlı bir metottur ve bir nesnenin **yüzeysel kopyasını (shallow copy)** oluşturur.
- Bu metot, bir nesnenin **değer tipindeki alanlarını kopyalar** ve **referans tipindeki alanları aynı referansı paylaşacak şekilde kopyalar.**

---

## **Kullanımı**

- `MemberwiseClone` doğrudan `Object` sınıfından gelir. Yani, her nesnede kullanılabilir.
- Genellikle, sınıfın bir kopyalama (`Clone`) metodunu yazarken kullanılır.

---

### **Kısıtlamalar**
- **Referans tipleri** derinlemesine kopyalamaz. Bu nedenle, iç içe geçmiş nesneler bağımsız kopyalar yerine aynı referansı paylaşır.
- Daha karmaşık yapılar için, **derin kopyalama (deep copy)** işlemi manuel olarak yapılmalıdır.

---

## **Kod Örneği**

```csharp
class MyClass
{
    public int Number; // Değer tipi
    public string Text; // Referans tipi

    public MyClass Clone()
    {
        return (MyClass)this.MemberwiseClone();
    }
}

class Program
{
    static void Main(string[] args)
    {
        MyClass obj1 = new MyClass { Number = 42, Text = "Hello" };
        MyClass obj2 = obj1.Clone();

        // Değer tipinde bağımsız kopya
        obj2.Number = 100;
        // Referans tipinde aynı nesneyi işaret eder
        obj2.Text = "World";

        Console.WriteLine($"obj1: Number={obj1.Number}, Text={obj1.Text}");
        Console.WriteLine($"obj2: Number={obj2.Number}, Text={obj2.Text}");
    }
}
```

---

### **Kod Açıklaması**

1. **`Clone` metodu:**
    - `MemberwiseClone` kullanılarak `MyClass` nesnesinin yüzeysel bir kopyası alınır.
    - Yeni bir nesne (`obj2`) oluşturulur, ancak referans tipleri (örneğin `Text`) aynı adresi paylaşır.

2. **Değer Tipleri (Value Types):**
    - `Number` bir değer tipi olduğu için, `obj1` ve `obj2` bağımsız kopyalara sahiptir.

3. **Referans Tipleri (Reference Types):**
    - `Text` bir referans tipi olduğu için, `obj1` ve `obj2` aynı `string` nesnesini paylaşır.
    - Bu nedenle, `obj2.Text` değiştiğinde, `obj1.Text` de değişir.

---

### **Çıktı:**
```plaintext
obj1: Number=42, Text=World
obj2: Number=100, Text=World
```

---

## **Sonuç**

- `MemberwiseClone`, **hızlı bir şekilde yüzeysel kopya** almak için idealdir.
- Ancak, referans tipleri bağımsız yapmak (derin kopya) için ek işlem yapılması gerekir.