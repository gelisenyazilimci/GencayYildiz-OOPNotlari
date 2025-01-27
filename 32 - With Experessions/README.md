# With Experessions 

---

- Immutable türlerde çalışırken nesne üzerinde değişiklik yapabilmek için ilgi nesneyi ya çoğaltmamız/klonlamamamız([deep copy](../27%20-%20Deep%20Copy/README.md)) ve üzerinde değişiklik yapmamız gerekmekte ya da manuel bir nesne üretip mevcut nesnedeki değerleri, değişkliği yansıtacak şekilde aktarmamız gerekmetedir. 
- Misal, aşağı kod örneğinde bu tarz durumlarda istinadn yazılımcıların yılların deneyiminden getirdiği `With function` çözümü ele alınmaktadır.

```csharp
Employee emp1 = new Employee
{
    Name = "Batu",
    Surname = "RoketAtar",
    Position = 1
};
Employee emp2 = new Employee
{
    Name = "Ramadan",
    Surname = emp1.Surname,
    Position = 2
};

public class Employee
{
    public string Name {get; init;}
    public string Surname {get; init;}
    public int? Position {get; init;}
    
    public Employee With (int position)
    {
        return new Employee 
        {
            Name = this.Name,
            Surname = this.Surname,
            Position = position
        }; 
    }
}
```

- Ya da aşağıdaki gibi record oluşturulabilir ve With Function yazmadan direkt olarak `with expressions'ları` kullanabilirsiniz. 

```csharp
Employee emp1 = new Employee
{
    Name = "Batu",
    Surname = "RoketAtar",
    Position = 1
};

Employee emp2 = emp1 with {Name = "Ramadan", Position = 2};
Employee emp3 = emp1 with {Name = "Ayberk", Surname = "Yıldız", Position = 3};
Employee emp4 = emp1 with {Surname = "musk"};

public record Employee
{
    public string Name {get; init;}
    public string Surname {get; init;}
    public int? Position {get; init;}
}

```

- Şimdi iki örneğe baktığınız zaman hangisi güzel diye soru sorsam ve 2. örnek daha güzel ve `with expressions` yazımı anlaşılabilir diyeceksiniz. 