---
title: Dönüşüm İşleçleri Kullanma (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
- implicit conversion operators [C#]
- explicit conversion operators [C#]
ms.assetid: caf36e89-c6c0-4b87-9f9e-85780a45c9a4
ms.openlocfilehash: e03fb12200bc15de9c1686edd40921201598621f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="using-conversion-operators-c-programming-guide"></a>Dönüşüm İşleçleri Kullanma (C# Programlama Kılavuzu)
Kullanımı daha kolay olan `implicit` dönüştürme operatörlerini veya kodu okuyan herkese bir türü dönüştürdüğünüzü açıkça gösteren `explicit` dönüştürme operatörlerini kullanabilirsiniz. Bu konuda, her iki dönüştürme operatörü türü gösterilir.  
  
> [!NOTE]
>  Basit tür dönüşümleri hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir dizeyi sayıya dönüştürme](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), [nasıl yapılır: byte dizisini int'e dönüştürme](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [nasıl yapılır: Dönüştür arasında onaltılık dizeler ve sayısal Türleri](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md), veya <xref:System.Convert>.  
  
## <a name="example"></a>Örnek  
 Bu bir açık bir dönüştürme operatörü örneğidir. Bu operatör, <xref:System.Byte> türünden `Digit` isimli değer türüne dönüştürür. Tüm baytlar bir basamak değerine dönüştürülemediğinden, dönüştürme açıktır; yani `Main` yönteminde gösterildiği gibi bir yayın kullanılması gerektiği anlamına gelir.  
  
 [!code-csharp[csProgGuideStatements#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_1.cs)]  
  
## <a name="example"></a>Örnek  
 Bu örnek, önceki örnekte yapılanı geri alan bir dönüştürme aracı tanımlayarak kapalı bir dönüştürme aracı gösterir: `Digit` olarak adlandırılan bir değer sınıfını <xref:System.Byte> integral türüne dönüştürür. Herhangi bir rakam bir <xref:System.Byte>'a dönüştürülebilir olduğundan, kullanıcıların dönüştürme hakkında açık olmaya zorlamaya gerek yoktur.  
  
 [!code-csharp[csProgGuideStatements#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_2.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Dönüştürme İşleçleri](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)  
 [is](../../../csharp/language-reference/keywords/is.md)
