---
title: new Değiştiricisi (C# Başvurusu)
ms.date: 07/20/2015
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
ms.openlocfilehash: b66cfacc2203e0e529c19b5c566abad6c676f149
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="new-modifier-c-reference"></a>new Değiştiricisi (C# Başvurusu)
Bir bildirim değiştirici kullanıldığında `new` anahtar sözcüğü bir taban sınıftan devralınan üye açıkça gizler. Devralınmış bir üyeyi gizleme, üye türetilmiş sürümünü temel sınıf sürümü değiştirir. Kullanmadan üyeleri gizleyebilirsiniz rağmen `new` değiştiricisi, derleyici uyarısı alırsınız. Kullanırsanız `new` açıkça üyesi gizlemek için bu uyarıyı bastırır.  
  
 Devralınmış bir üyeyi gizlemek için aynı üye adı kullanarak türetilen sınıfta bildirme ve onunla değiştirmek `new` anahtar sözcüğü. Örneğin:  
  
 [!code-csharp[csrefKeywordsOperator#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_1.cs)]  
  
 Bu örnekte, `BaseC.Invoke` tarafından gizli `DerivedC.Invoke`. Alan `x` benzer ada göre değil gizlendiği etkilenmez.  
  
 Devralma yoluyla gizleme adı aşağıdaki biçimlerden birini alır:  
  
-   Genellikle, sabit, alan, özelliği veya bir sınıf veya yapı biriminde sunulan türü adını paylaşan tüm taban sınıfı üyeleri gizler.  Özel durumlar vardır.  Örneğin, yeni bir ad alanıyla bildirirseniz `N` invocable olmayan bir türü ve bir taban türü bildirir `N` bir yöntemi olması için yeni alan çağırma söz dizimi temel bildiriminde gizlemez.  Bkz: [5.0 C# dil belirtimi](https://www.microsoft.com/download/details.aspx?id=7029) için ayrıntıları ("İfadeleri" bölümünde "Üye araması" bölümüne bakın).  
  
-   Sınıfta veya yapı biriminde sunulan bir yöntemi, özellikleri, alanları ve temel sınıfı ad paylaşmak türleri gizler. Ayrıca, aynı imzaya sahip tüm taban sınıf yöntemlerini gizler.  
  
-   Bir sınıf veya yapı biriminde sunulan bir dizin oluşturucu aynı imzaya sahip tüm temel sınıf dizin oluşturucular gizler.  
  
 Her ikisi de kullanmak için bir hata olduğunu `new` ve [geçersiz kılma](../../../csharp/language-reference/keywords/override.md) aynı üye üzerindeki iki değiştiricileri birbirini dışlayan anlamları olduğundan. `new` Değiştiricisi aynı ada sahip yeni bir üye oluşturur ve gizli hale özgün üye neden olur. `override` Değiştiricisi devralınmış bir üyeyi uygulamasını genişletir.  
  
 Kullanarak `new` değiştiricisi devralınmış bir üyeyi gizlemez bildiriminde bir uyarı oluşturur.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, bir taban sınıf `BaseC`ve türetilmiş bir sınıf `DerivedC`, aynı alan adını kullanmak `x`, devralınan alanın değerini gizler. Örnek kullanımını gösteren `new` değiştiricisi. Ayrıca, temel sınıfın gizli üyeleri tam adlarını kullanarak erişmek nasıl gösterir.  
  
 [!code-csharp[csrefKeywordsOperator#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_2.cs)]  
  
## <a name="example"></a>Örnek  
 Bu örnekte, bir iç içe geçmiş sınıf taban sınıf içinde aynı ada sahip bir sınıf gizler. Örnek nasıl kullanılacağı ortaya `new` uyarı iletisi ve gizli sınıf üyeleri tam adlarını kullanarak erişim ortadan kaldırmak için değiştiricisi.  
  
 [!code-csharp[csrefKeywordsOperator#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_3.cs)]  
  
 Kaldırırsanız `new` değiştiricisi, program hala derleyin ve çalıştırın, ancak aşağıdaki uyarı alırsınız:  
  
```  
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.  
```  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [İşleç Anahtar Sözcükleri](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [Değiştiriciler](../../../csharp/language-reference/keywords/modifiers.md)  
 [Geçersiz Kılma ve Yeni Anahtar Sözcüklerle Sürüm Oluşturma](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)  
 [Geçersiz Kılmanın ve Yeni Anahtar Sözcüklerin Ne Zaman Kullanılacağını Bilme](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)
