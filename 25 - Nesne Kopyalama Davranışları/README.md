# Nesne ve Değer Kopyalama Davranışları

C# programlama dilinde nesneler ve değer türleri arasında farklı kopyalama davranışları bulunur. Bu davranışlar, değişkenlerin bellekte nasıl saklandığını ve nasıl davrandığını etkiler.

---

## 1. Değer Türleri (Value Types)

Değer türleri `struct` olarak tanımlanır ve bellekte **stack** üzerinde saklanır. Değer türleri kopyalandığında **verinin tamamı kopyalanır**. Bu nedenle, kopya değişken üzerindeki değişiklikler orijinal değişkeni etkilemez.

### Örnek

```csharp
using System;

struct Point
{
    public int X;
    public int Y;
}

class Program
{
    static void Main()
    {
        Point p1 = new Point { X = 10, Y = 20 };
        Point p2 = p1; // p2, p1'in bir kopyasıdır.

        p2.X = 30; // Sadece p2'nin X değeri değişir.

        Console.WriteLine($"p1: X={p1.X}, Y={p1.Y}"); // X=10, Y=20
        Console.WriteLine($"p2: X={p2.X}, Y={p2.Y}"); // X=30, Y=20
    }
}
```
---

## 2. Referans Türleri (Reference Types)
Referans türleri class olarak tanımlanır ve bellekte heap üzerinde saklanır. Referans türleri kopyalandığında, sadece bellek adresi kopyalanır. Bu nedenle, bir değişken üzerindeki değişiklik diğer değişkeni de etkiler.
```csharp
using System;

class Person
{
    public string Name { get; set; }
}

class Program
{
    static void Main()
    {
        Person person1 = new Person { Name = "Alice" };
        Person person2 = person1; // person2, person1'in adresini kopyalar.

        person2.Name = "Bob"; // Hem person1 hem de person2 etkilenir.

        Console.WriteLine($"person1.Name: {person1.Name}"); // Bob
        Console.WriteLine($"person2.Name: {person2.Name}"); // Bob
    }
}

```

---

## 3. Derin Kopya (Deep Copy)
Bir nesnenin bağımsız bir kopyasını oluşturmak için derin kopyalama kullanılır. Bu işlem, yeni bir nesne oluşturulmasını ve eski nesnedeki verilerin kopyalanmasını içerir.

---

## 4. Sığ Kopya (Shallow Copy)
Sığ kopyalama sırasında, nesnenin yalnızca bir üst düzey referansı kopyalanır. İç içe geçmiş nesneler paylaşılır.

---

## 5. Özelleştirilmiş Kopyalama (ICloneable)
C#'da kopyalama işlemini özelleştirmek için `ICloneable` arayüzü kullanılabilir. Bu yöntem hem sığ hem de derin kopyalama işlemlerini destekleyecek şekilde özelleştirilebilir.


