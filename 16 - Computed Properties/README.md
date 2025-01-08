#  Computed (Hesaplanmış) Properties

--- 

- İçerisinde türetilmiş bir bağıntı taşıyan property'lerdir.

```csharp
    int s1 = 31, s2 = 69; 
    public int Topla {get {return s1 + s2;}};
```
- yukarıdaki örnek kadar başka şöyleyebileceğim bir şey yok. 
- Normal bildiğiniz property'nin ta kendisi. Sadece farkı dışarıdan alınan değerin get veya set'in içerisinde hesaplamalar yapıyorsanız oradan almış bir isim türüdür. Bunu aklınızda tutmanıza bile gerek yok. 