# Target-Typed New Expressions (C# 9.0)

---

C# 9.0 sürümü, nesne oluşturma süreçlerinde semantik açıdan büyük bir kolaylık sağlayan **Target-Typed New Expressions** özelliğini tanıttı. Bu özellik, nesne oluşturma sürecinde oluşturulacak nesne eğer doğrudan bir referansa atanıyorsa, tür bilgisi referanstan anlaşılabileceği için türü yeniden belirtme zorunluluğunu ortadan kaldırır.

### Örnek Kullanım:

Normalde bir nesne oluşturmak için şu semantik kullanılır:

```csharp
Type x = new Type();
```

C# 9.0 ile birlikte bu işlem artık daha kısa bir şekilde yapılabilir:

```csharp
Type x = new();
```

Bu yöntem, özellikle daha karmaşık veri türlerinde veya generic yapıların kullanımında fayda sağlar.

---

### Generic Kullanımı:

Generic bir modelden nesne oluşturulurken veya generic bir koleksiyon kullanıldığında da bu özellikten faydalanabilirsiniz.

Örneğin, normalde aşağıdaki gibi yazmanız gerekiyordu:

```csharp
MyClass<string> myClass = new MyClass<string>();
```

Ancak artık bu ifadeyi şu şekilde sadeleştirebilirsiniz:

```csharp
MyClass<string> myClass = new();
```

Bu özellik, yazılımda gereksiz tekrarları azaltır ve kodun daha okunabilir olmasını sağlar.

---

### Uyumluluk:

Bu özelliği kullanabilmek için projenizin **.NET 5.0** veya daha yüksek bir sürümde olması gerekir. Eğer **.NET 5.0** altındaki bir sürümü kullanıyorsanız, bu özelliği kullanmaya çalıştığınızda hata alırsınız.

**Çözüm:** Projenizi .NET 5.0 veya daha yeni bir sürüme yükseltin ve ardından projeyi yeniden derleyin (**Rebuild**). Bu işlem, sorununuzu tamamen çözecektir.

---