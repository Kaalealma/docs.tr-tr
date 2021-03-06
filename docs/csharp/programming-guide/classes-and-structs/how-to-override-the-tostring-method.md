---
title: 'Nasıl yapılır: ToString Yöntemini Geçersiz Kılma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: 86394f5fed55f57df8928648548fcfca117b00d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a>Nasıl yapılır: ToString Yöntemini Geçersiz Kılma (C# Programlama Kılavuzu)
Her sınıf veya yapı C# örtük olarak devralır <xref:System.Object> sınıfı. Bu nedenle, her nesne C# alır <xref:System.Object.ToString%2A> yöntemi nesnenin dize gösterimini döndürür. Örneğin, tüm değişkenler türü `int` sahip bir `ToString` bunları içeriklerini bir dize döndürecek şekilde etkinleştirir yöntemi:  
  
 [!code-csharp[csProgGuideInheritance#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_1.cs)]  
  
 Özel bir sınıf veya yapı oluşturduğunuzda, geçersiz kılmalısınız <xref:System.Object.ToString%2A> türünüz için istemci kodu hakkında bilgi sağlamak için yöntem.  
  
 Biçim dizeleri ve başka ile özel biçimlendirme türleri nasıl kullanılacağı hakkında bilgi için `ToString` yöntemi, bkz: [biçimlendirme türleri](../../../standard/base-types/formatting-types.md).  
  
> [!IMPORTANT]
>  Bu yöntemle sağlamak için hangi bilgilerin karar verdiğinizde, sınıf veya yapı hiç güvenilmeyen kod tarafından kullanılıp kullanılmayacağını göz önünde bulundurun. Kötü amaçlı kod tarafından yararlanılabilir herhangi bir bilgi sağlamaz emin olmak dikkatli olun.  
  
### <a name="to-override-the-tostring-method-in-your-class-or-struct"></a>Sınıf veya yapı ToString yöntemini geçersiz kılmak için  
  
1.  Bildirme bir `ToString` yöntemi aşağıdaki değiştiricileri ve dönüş türüne sahip:  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2.  Böylece bir dize döndürür yöntemi uygulayabilirsiniz.  
  
     Aşağıdaki örnek verileri yanı sıra sınıfın adı sınıfın belirli bir örneğine özel döndürür.  
  
     [!code-csharp[csProgGuideInheritance#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_2.cs)]  
  
     Test edebilirsiniz `ToString` yöntemini aşağıdaki kod örneğinde gösterildiği gibi değiştirin:  
  
     [!code-csharp[csProgGuideInheritance#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_3.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IFormattable>  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Dizeler](../../../csharp/programming-guide/strings/index.md)  
 [string](../../../csharp/language-reference/keywords/string.md)  
 [new](../../../csharp/language-reference/keywords/new.md)  
 [override](../../../csharp/language-reference/keywords/override.md)  
 [virtual](../../../csharp/language-reference/keywords/virtual.md)  
 [Biçimlendirme Türleri](../../../standard/base-types/formatting-types.md)
