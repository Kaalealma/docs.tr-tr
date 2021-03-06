---
title: 'Nasıl yapılır: Türetilmiş Sınıflarda Temel Sınıf Olayları Oluşturma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: e064c318f16c2fe87aa980b7dec7468b1e61ab25
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a>Nasıl yapılır: Türetilmiş Sınıflarda Temel Sınıf Olayları Oluşturma (C# Programlama Kılavuzu)
Aşağıdaki basit örnek türetilmiş sınıflarından ayrıca yükseltilebilir böylece bir temel sınıf olayları bildirme standart yolu gösterir. Bu deseni Windows Forms sınıfları yaygın olarak kullanılan [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sınıf kitaplığı.  
  
 Diğer sınıflar için temel sınıf olarak kullanılabilir bir sınıf oluşturduğunuzda, olaylar yalnızca gelen bunları bildirilen sınıfı içinde çağrılabilir temsilci özel bir tür bulunmasına düşünmelisiniz. Türetilmiş sınıflar temel sınıf içinde bildirilen olayları doğrudan çağrılamıyor. Çoğu zaman, yalnızca temel sınıfı tarafından gerçekleştirilen bir olay bazen isteyebilirsiniz karşın, temel sınıf olayları çağırmak türetilmiş sınıf etkinleştirmeniz gerekir. Bunu yapmak için olay sarmalar taban sınıf içinde korumalı bildirilecekse yöntemi oluşturabilirsiniz. Türetilen sınıflar çağrılırken veya bildirilecekse bu yöntemi geçersiz kılma, olay dolaylı olarak çağırabilirsiniz.  
  
> [!NOTE]
>  Sanal bir temel sınıf olayları bildirme değil ve türetilen bir sınıfta geçersiz. C# Derleyici doğru bu işlemez ve türetilen olaya abone gerçekte temel sınıf olaya abone olup olmadığını tahmin edilemez.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideEvents#1](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-raise-base-class-events-in-derived-classes_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Olaylar](../../../csharp/programming-guide/events/index.md)  
 [Temsilciler](../../../csharp/programming-guide/delegates/index.md)  
 [Erişim Değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [Windows Forms'ta Olay İşleyicileri Oluşturma](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)
