

### Deep Copy

**Deep Copy** (Derin Kopyalama), bir veri yapısındaki orijinal verilerin birebir kopyalarının oluşturulmasıdır. Bu kopyalama yöntemi, verilerin bellekte tamamen farklı bir adres alanında yeniden oluşturulmasını sağlar. Yani, kopyalanan veriler orijinal veriyle bağımsızdır ve birinin üzerinde yapılan değişiklik diğerini etkilemez.

---

#### Örnek

```csharp
int a = 5;
int b = a;
```

Bu örnekte:

1. **`a` değişkeni** bir değer tutar ve değeri `5` olarak belirlenir.
2. **`b` değişkeni**, `a` değişkeninin değerini alır. Ancak bu işlem sırasında `b`, `a`'nın referansını değil, sadece içindeki değeri (`5`) kopyalar.
3. Bellek üzerinde, **`a`** ve **`b`** iki ayrı yerde `5` değerini tutar. Bu yüzden, `b` üzerinde yapılan herhangi bir değişiklik, `a`'yı etkilemeyecektir (ve tersi).

---

#### Detaylı Açıklama

- **Deep Copy'nin Amacı:** Orijinal veri ve kopya veri arasında tam bir bağımsızlık sağlar. Bu, özellikle veri yapılarında (örneğin, listeler, diziler veya nesneler) önemli bir konudur. Orijinal veride bir değişiklik olduğunda, kopya verinin etkilenmemesi isteniyorsa, deep copy tercih edilir.

- **C#'ta Varsayılan Davranış:** Değer türündeki değişkenler birbirlerine atanırken, varsayılan olarak **deep copy** gerçekleştirilir. Yani, yukarıdaki örnekte olduğu gibi, `int` gibi değer türleri birbirine atandığında, otomatik olarak yeni bir kopya oluşturulur.

