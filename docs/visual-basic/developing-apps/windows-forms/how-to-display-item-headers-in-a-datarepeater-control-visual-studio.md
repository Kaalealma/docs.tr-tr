---
title: 'Nasıl Yapılır: DataRepeater Denetiminde Öğe Üstbilgilerini Görüntüleme (Visual Studio)'
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, item headers
- DataRepeater, selection indicators
ms.assetid: 37321447-0ffa-43e1-bdc9-0480e392b90f
ms.openlocfilehash: 07f6a7e06c5b1e91597ab6b6d816407a2c172278
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-display-item-headers-in-a-datarepeater-control-visual-studio"></a>Nasıl Yapılır: DataRepeater Denetiminde Öğe Üstbilgilerini Görüntüleme (Visual Studio)
Öğe üstbilgisinde bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim görsel bir gösterge sağlar, bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> seçilir. Zaman <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> özelliği ayarlanmış <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical> (varsayılan), her bir öğe sola öğesi başlığı görüntülenir. Zaman <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> özelliği ayarlanmış <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>, öğesi üstbilgisinde her öğenin üst kısmında görüntülenir.  
  
 İlk seçildiğinde, öğesi üstbilgisi tarafından belirtilen renkte görüntülenir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> özelliği ve beyaz ok simgesi görüntülenir.  
  
> [!NOTE]
>  Ayarlarsanız <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> için <xref:System.Drawing.Color.White%2A>, öğe ilk seçildiğinde seçimi simgesi görünür olmaz.  
  
 Bir alan <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> odaktaki öğeyi üstbilgi değişiklikleri rengini <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> arka plan rengi ve siyah ok simgesine yapılan değişiklikler. Veri değiştirdiyseniz, Kurşun Kalem simgesini öğesi başlığında görüntülenir.  
  
 Varsayılan genişlikteki (veya yükseklik zaman <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> özelliği ayarlanmış <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>) öğesi'nin üstbilgi 15 pikseldir. Ayarlayarak genişliğini değiştirebilirsiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> özelliği.  
  
> [!NOTE]
>  Varsa <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> özelliği 11'den küçük bir değere ayarlamak, gösterge simgeleri öğesi üstbilgisinde görüntülenmeyecek.  
  
 Öğe üstbilgilerini ayarlayarak gizleyebilirsiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> özelliğine **False**. Zaman <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> ayarlanır **False**, öğe seçildiğinde yalnızca çevresinde noktalı çizgi göstergesidir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.  
  
> [!NOTE]
>  İzleme tarafından kendi seçim göstergesini sağlayabilir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A> özelliği <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> içinde <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> olayı <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>.  
  
### <a name="to-change-the-appearance-of-item-headers"></a>Öğe üstbilgilerini görünümünü değiştirmek için  
  
1.  Windows Forms Tasarımcısı'nda alt bölgesini seçin <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.  
  
    > [!NOTE]
    >  Denetimin alt bölgeyi seçmeniz gerekir. Öğesi şablonu bölümüne seçerseniz, farklı bir özellikler kümesi Özellikler penceresinde görüntülenir.  
  
2.  Özellikler penceresini kullanın <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> öğe üstbilgilerini rengini değiştirmek için özellik.  
  
    > [!NOTE]
    >  Ayarlarsanız <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> için <xref:System.Drawing.Color.White%2A>, öğe ilk seçildiğinde seçimi simgesi görünür olmaz.  
  
3.  Kullanım <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> öğe üstbilgilerini genişliğini (veya yükseklik) değiştirmek için özellik.  
  
    > [!NOTE]
    >  Varsa <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> özelliği 11'den küçük bir değere ayarlamak, gösterge simgeleri öğesi üstbilgisinde görüntülenmeyecek.  
  
### <a name="to-hide-item-headers"></a>Öğe üstbilgilerini gizleme  
  
1.  Windows Forms Tasarımcısı'nda alt bölgesini seçin <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.  
  
    > [!NOTE]
    >  Denetimin alt bölgeyi seçmeniz gerekir. Öğesi şablonu bölümüne seçerseniz, farklı bir özellikler kümesi Özellikler penceresinde görüntülenir.  
  
2.  Özellikler penceresinde ayarlayın <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> özelliğine **False**.  
  
     Bir öğe <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> olduğundan, tek belirti çevresinde noktalı çizgi seçilir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [DataRepeater Denetimine Giriş](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Nasıl Yapılır: DataRepeater Denetiminin Görünümünü Değiştirme](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [Nasıl Yapılır: DataRepeater Denetimi Düzenini Değiştirme](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)  
 [DataRepeater Denetiminde Sorun Giderme](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
