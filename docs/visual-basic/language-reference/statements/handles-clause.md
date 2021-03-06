---
title: Handles Tümcesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords:
- Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
ms.openlocfilehash: 15ce6a25aa5f403a2e55beb57b3693095743e52f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="handles-clause-visual-basic"></a>Handles Tümcesi (Visual Basic)
Bir yordam belirtilen bir olay işleme bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a>Bölümler  
 `proceduredeclaration`  
 `Sub` Yordamı bildirimi olayı işleyecek bir yordam.  
  
 `eventlist`  
 Olayları listesi `proceduredeclaration` işlemek için virgülle ayrılmış. Olayları ya da taban sınıfı için geçerli sınıf veya kullanılarak bildirilen bir nesne tarafından oluşturulması `WithEvents` anahtar sözcüğü.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım `Handles` anahtar sözcüğü bir nesne değişkeni tarafından başlatılan olayları işlemek için neden bir yordam bildiriminin sonundaki kullanarak bildirilen `WithEvents` anahtar sözcüğü. `Handles` Anahtar sözcüğü de türetilen bir sınıfta bir temel sınıf olayları işlemek için kullanılabilir.  
  
 `Handles` Anahtar sözcüğü ve `AddHandler` deyimi hem belirli yordamları belirli olayları işleme, ancak bazı farklılıklar vardır belirtmenize olanak tanır. Kullanım `Handles` , belirli bir olay işleme belirtmek için bir yordam tanımlarken anahtar sözcüğü. `AddHandler` Deyimi olaylarına yordamlar çalışma zamanında bağlanır. Daha fazla bilgi için bkz: [AddHandler deyimi](../../../visual-basic/language-reference/statements/addhandler-statement.md).  
  
 Özel olaylar için uygulama olay çağırır `AddHandler` olay işleyici yordamı eklediğinde erişimcisi. Özel olaylar hakkında daha fazla bilgi için bkz: [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbalrEvents#2](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_1.vb)]  
  
 Aşağıdaki örnek, türetilmiş bir sınıf nasıl kullanabileceğinizi gösterir `Handles` temel sınıfından bir olayını işlemek için deyimi.  
  
 [!code-vb[VbVbalrEvents#3](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_2.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte iki düğmesi olay işleyicilerini içeren bir **WPF uygulaması** projesi.  
  
 [!code-vb[VbVbalrEvents#41](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_3.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek önceki örneğe eşdeğerdir. `eventlist` İçinde `Handles` yan tümcesi hem düğmelerinin olaylarını içerir.  
  
 [!code-vb[VbVbalrEvents#42](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_4.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)  
 [AddHandler Deyimi](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [RemoveHandler Deyimi](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)  
 [RaiseEvent Deyimi](../../../visual-basic/language-reference/statements/raiseevent-statement.md)  
 [Olaylar](../../../visual-basic/programming-guide/language-features/events/index.md)
