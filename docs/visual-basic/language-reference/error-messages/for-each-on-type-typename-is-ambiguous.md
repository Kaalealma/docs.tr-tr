---
title: '&#39;Her&#39; türündeki &#39; &lt;typename&gt; &#39; türü birden çok işlemlerinden uyguladığından belirsiz &#39;System.Collections.Generic.IEnumerable (Of T)&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
ms.openlocfilehash: 8c48a7134eb8da83fb418b9aa91d55dcbe8e8bcb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="39for-each39-on-type-39lttypenamegt39-is-ambiguous-because-the-type-implements-multiple-instantiations-of-39systemcollectionsgenericienumerableof-t39"></a>&#39;Her&#39; türündeki &#39; &lt;typename&gt; &#39; türü birden çok işlemlerinden uyguladığından belirsiz &#39;System.Collections.Generic.IEnumerable (Of T)&#39;
A `For Each` deyimi birden fazla sahip bir yineleyici değişkeni belirtir <xref:System.Collections.IEnumerable.GetEnumerator%2A> yöntemi.  
  
 Yineleyici değişken uygulayan bir tür olmalıdır <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> birini arabiriminde `Collections` isim [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Her bir yapı için farklı tür bağımsız değişkeni kullanarak birden fazla oluşturulan genel arabirimi uygulamak için bir sınıf mümkündür. Bu sınıf yineleyici değişken için kullanılırsa, bu değişken birden fazla sahip <xref:System.Collections.IEnumerable.GetEnumerator%2A> yöntemi. Böyle bir durumda, Visual Basic çağrı yönetimini seçemezsiniz.  
  
 **Hata Kimliği:** BC32096  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Kullanmak [DirectCast işleci](../../../visual-basic/language-reference/operators/directcast-operator.md) veya [TryCast işleci](../../../visual-basic/language-reference/operators/trycast-operator.md) yineleyici değişken türünü arabirim tanımlama yayınlanamıyor <xref:System.Collections.IEnumerable.GetEnumerator%2A> kullanmak istediğiniz yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [For Each...Next Deyimi](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [Arabirimler](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
