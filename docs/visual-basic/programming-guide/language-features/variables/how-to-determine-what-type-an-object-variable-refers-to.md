---
title: 'Nasıl yapılır: Bir Nesne Değişkeninin Hangi Türe Başvurduğunu Belirleme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: 0dfd4ed87b65f536802ae71cbc3de41e1c4f83af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a>Nasıl yapılır: Bir Nesne Değişkeninin Hangi Türe Başvurduğunu Belirleme (Visual Basic)
Bir nesne değişkeni başka bir yerde depolanan veriler için bir işaretçi içeriyor. Bu veri türü, çalışma zamanı sırasında değiştirebilirsiniz. Herhangi bir anda kullandığınız <xref:System.Type.GetTypeCode%2A> geçerli çalışma zamanı tür belirlemek için yöntemi veya [TypeOf işleci](../../../../visual-basic/language-reference/operators/typeof-operator.md) geçerli olmadığını öğrenmek için çalışma zamanı türü belirtilen türle uyumlu değil.  
  
### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a>Tam bir nesne değişkeni şu anda türünü belirlemek için başvurur  
  
1.  Nesne değişkeni üzerinde çağrısı <xref:System.Object.GetType%2A> alma yöntemi bir <xref:System.Type?displayProperty=nameWithType> nesnesi.  
  
    ```  
    Dim myObject As Object  
    myObject.GetType()  
    ```  
  
2.  Üzerinde <xref:System.Type?displayProperty=nameWithType> sınıfı, paylaştırılmış yöntem çağrısı <xref:System.Type.GetTypeCode%2A> almak için <xref:System.TypeCode> numaralandırma değeri nesnenin türü.  
  
    ```  
    Dim myObject As Object  
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())  
    MsgBox("myObject currently has type code " & CStr(datTyp))  
    ```  
  
     Test edebilirsiniz <xref:System.TypeCode> hangi numaralandırma üyeleri, gibi ilgilendiğiniz karşı numaralandırma değeri `Double`.  
  
### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a>Bir nesne olup olmadığını belirlemek için değişkenin türü belirtilen türle uyumlu değil  
  
-   Kullanım `TypeOf` birlikte işleci [Is işlecini](../../../../visual-basic/language-reference/operators/is-operator.md) nesnesi ile test etmek için bir `TypeOf`... `Is` ifade.  
  
    ```  
    If TypeOf objA Is System.Windows.Forms.Control Then  
        MsgBox("objA is compatible with the Control class")  
    End If  
    ```  
  
     `TypeOf`... `Is` ifadesi döndürür `True` çalışma zamanında nesne türü belirtilen tür ile uyumlu ise.  
  
     Uyumluluk için ölçüt belirtilen türün bir sınıf, yapı veya arabirimi olduğuna bağlıdır. Genel olarak, nesne aynı türde ise, devraldığı veya belirtilen türe uygulayan türler uyumludur. Daha fazla bilgi için bkz: [TypeOf işleci](../../../../visual-basic/language-reference/operators/typeof-operator.md).  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Belirtilen türde bir değişken veya ifadeyi olamayacağını unutmayın. Bu sınıf, yapı veya arabirim gibi tanımlanmış bir türü adı olmalıdır. Bu gibi iç türleri içerir `Integer` ve `String`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Object.GetType%2A>  
 <xref:System.Type?displayProperty=nameWithType>  
 <xref:System.Type.GetTypeCode%2A>  
 <xref:System.TypeCode>  
 [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Nesne Değişkeni Değerleri](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [Object Veri Türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)
