---
title: double (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- double
- double_CSharpKeyword
helpviewer_keywords:
- double data type [C#]
ms.assetid: 0980e11b-6004-4102-abcf-cfc280fc6991
ms.openlocfilehash: 3683b51dfd0ef653ab8bfff6705b96a37e21a10a
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
---
# <a name="double-c-reference"></a>double (C# Başvurusu)
`double` Anahtar sözcüğü 64-bit kayan nokta değerlerini depolayan basit bir tür belirtir. Aşağıdaki tabloda duyarlık ve yaklaşık aralığının gösterir `double` türü.  
  
|Tür|Yaklaşık aralığı|Duyarlık|.NET Framework türü|  
|----------|-----------------------|---------------|-------------------------|  
|`double`|±5.0 × 10<sup>−324</sup> ±1.7 × 10 için<sup>308</sup>|15-16 basamak|<xref:System.Double?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Sabit değerler  
 Varsayılan olarak, gerçek tamsayısal bir hazır değer atama işlecinin sağ tarafında olarak işlem görür `double`. Ancak, kabul edilmesi için bir tamsayı isteyip istemediğinizi `double`, sonek d veya D, örneğin kullanın:  
  
```csharp  
double x = 3D;  
```  
  
## <a name="conversions"></a>Dönüşümler  
 Sayısal tam sayı türleri ve bir ifadede kayan nokta türleri karıştırabilirsiniz. Bu durumda, tam sayı türleri için kayan nokta türleri dönüştürülür. İfade değerlendirme aşağıdaki kurallara göre gerçekleştirilir:  
  
-   Kayan nokta türlerinden birini ise `double`, için ifadeyi hesaplar `double`, veya [bool](../../../csharp/language-reference/keywords/bool.md) ilişkisel ya da Boole ifadelerde.  
  
-   Varsa hiçbir `double` türü için değerlendirir ifadesinde [float](../../../csharp/language-reference/keywords/float.md), veya [bool](../../../csharp/language-reference/keywords/bool.md) ilişkisel ya da Boole ifadelerde.  
  
 Kayan nokta ifade aşağıdaki değerleri içerebilir:  
  
-   Pozitif ve negatif sıfır.  
  
-   Pozitif ve negatif sonsuzluk.  
  
-   Değer bir sayı değil (NaN).  
  
-   Sıfır olmayan değerler sınırlı kümesi.  
  
 Bu değerler hakkında daha fazla bilgi için ikili Floating-Point aritmetik, kullanılabilir IEEE standardı bkz [IEEE](http://www.ieee.org) Web sitesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, bir [int](../../../csharp/language-reference/keywords/int.md), [kısa](../../../csharp/language-reference/keywords/short.md), [float](../../../csharp/language-reference/keywords/float.md)ve bir `double` birlikte vermiş eklenen bir `double` sonucu.  
  
 [!code-csharp[csrefKeywordsTypes#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/double_1.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Varsayılan Değerler Tablosu](../../../csharp/language-reference/keywords/default-values-table.md)  
 [Yerleşik Türler Tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Kayan Nokta Türleri Tablosu](../../../csharp/language-reference/keywords/floating-point-types-table.md)  
 [Örtük Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Açık Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
