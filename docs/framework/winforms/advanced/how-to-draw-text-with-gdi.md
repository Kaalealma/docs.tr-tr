---
title: 'Nasıl yapılır: GDI ile Metin Çizme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing with TextRenderer
- drawing [Windows Forms], text
- Windows Forms, drawing text with GDI
ms.assetid: 2a19fe5d-2ace-451c-94db-01cb1118ef7b
ms.openlocfilehash: e18ff96ea97eb636de8ab73aaa094c07b10fd456
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-draw-text-with-gdi"></a>Nasıl yapılır: GDI ile Metin Çizme
İle <xref:System.Windows.Forms.TextRenderer.DrawText%2A> yönteminde <xref:System.Windows.Forms.TextRenderer> sınıfı, erişebilir [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] bir form veya denetim metin çizme işlevi. [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] metin işleme genellikle daha iyi performans ve daha ölçmek daha doğru metin sunar [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  
  
> [!NOTE]
>  <xref:System.Windows.Forms.TextRenderer.DrawText%2A> Yöntemlerinin <xref:System.Windows.Forms.TextRenderer> sınıfı yazdırmak için desteklenmiyor. Yazdırma sırasında her zaman kullanmak <xref:System.Drawing.Graphics.DrawString%2A> yöntemlerinin <xref:System.Drawing.Graphics> sınıfı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği kullanarak bir dikdörtgen içinde birden çok satıra metin çizme gösterilmiştir <xref:System.Windows.Forms.TextRenderer.DrawText%2A> yöntemi.  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 Metinle işlemek için <xref:System.Windows.Forms.TextRenderer> ihtiyacınız sınıfı, bir <xref:System.Drawing.IDeviceContext>, gibi bir <xref:System.Drawing.Graphics> ve <xref:System.Drawing.Font>, metin ve, bunu çizilip rengi çizmek için bir konum. İsteğe bağlı olarak, metin kullanarak biçimlendirme belirtebilirsiniz <xref:System.Windows.Forms.TextFormatFlags> numaralandırması.  
  
 Edinme hakkında daha fazla bilgi için bir <xref:System.Drawing.Graphics>, bkz: [nasıl yapılır: çizim için grafik nesneleri oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md). Oluşturma hakkında daha fazla bilgi için bir <xref:System.Drawing.Font>, bkz: [nasıl yapılır: yazı tipi aileleri oluşturmak ve yazı tipleri](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md).  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki kod örneğinde Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.TextRenderer>  
 <xref:System.Drawing.Font>  
 <xref:System.Drawing.Color>  
 <xref:System.Drawing.Color>  
 [Yazı Tipleri ve Metin Kullanma](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
