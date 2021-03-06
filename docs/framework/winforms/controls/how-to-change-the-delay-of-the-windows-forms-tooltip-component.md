---
title: 'Nasıl yapılır: Windows Forms ToolTip Bileşeninin Gecikmesini Değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolTip component [Windows Forms], delay values
- tooltips [Windows Forms], delay values
- examples [Windows Forms], tooltips
ms.assetid: 08979ba7-dd84-477b-ab17-8d06e759be99
ms.openlocfilehash: 20dcd941b142daa672312edb618a1c3e4597442d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-change-the-delay-of-the-windows-forms-tooltip-component"></a>Nasıl yapılır: Windows Forms ToolTip Bileşeninin Gecikmesini Değiştirme
Windows Forms için ayarlayabileceğiniz birden çok gecikme değerler <xref:System.Windows.Forms.ToolTip> bileşeni. Bu özellikleri milisaniye ölçü birimidir. <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> Özelliği belirler ne kadar süreyle kullanıcı için görüntülenecek araç ipucu dize ilişkili denetim noktasına gerekir. <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> Özelliği ayarlar geçen bir araç ipucu ilişkili denetimden fareyi hareket ederken görünmesi sonraki araç ipucu dizeleri için milisaniye sayısı. <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> Özelliği, araç ipucu dize gösterilir süreyi belirler. Ayrı ayrı veya değerini ayarlayarak bu değerleri ayarlayabileceğiniz <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> özellik; özellikler ayarlandığında tabanlı atanan değer diğer gecikme <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> özelliği. Örneğin, <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> N değerine ayarlayın <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> N olarak ayarlanmışsa <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> değerine ayarlanmış <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> beş tarafından bölünmüş (veya N/5), ve <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> beş kez değeri olan bir değer ayarlamak <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> özelliği (veya 5N).  
  
### <a name="to-set-the-delay"></a>Gecikme ayarlamak için  
  
1.  Bu örnekte gösterildiği gibi aşağıdaki özellikleri ayarlayın.  
  
    ```vb  
    ToolTip1.InitialDelay = 500  
    ToolTip1.ReshowDelay = 100  
    ToolTip1.AutoPopDelay = 5000  
    ```  
  
    ```csharp  
    ToolTip1.InitialDelay = 500;  
    ToolTip1.ReshowDelay = 100;  
    ToolTip1.AutoPopDelay = 5000;  
    ```  
  
    ```cpp  
    toolTip1->InitialDelay = 500;  
    toolTip1->ReshowDelay = 100;  
    toolTip1->AutoPopDelay = 5000;  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ToolTip Bileşenine Genel Bakış](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)  
 [Nasıl yapılır: Tasarım Zamanında Windows Formundaki Denetimler için ToolTips Ayarlama](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)  
 [ToolTip Bileşeni](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)
