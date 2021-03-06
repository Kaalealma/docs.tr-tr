---
title: Windows Forms DataGridView Denetimindeki Veri Biçimleri
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in grids
- data grids [Windows Forms], formatting data
ms.assetid: 07bf558d-3748-42ba-8ba0-37fdef924081
ms.openlocfilehash: ae1947cf7c3825553837fa5f1ee288114988d28f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="data-formatting-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetimindeki Veri Biçimleri
<xref:System.Windows.Forms.DataGridView> Denetimi hücre değerlerini ve üst sütunlarını görüntüleme veri türleri arasında otomatik dönüşüm sağlar. Metin kutusu sütunları, örneğin, tarih, saat, sayı ve numaralandırma değerlerinin dize gösterimlerini görüntüle ve veri deposu tarafından gereken türleri için kullanıcı tarafından girilen dize değerlerini Dönüştür.  
  
## <a name="formatting-with-the-datagridviewcellstyle-class"></a>DataGridViewCellStyle sınıfıyla biçimlendirme  
 <xref:System.Windows.Forms.DataGridView> Denetimi sağlar hücre değerlerini temel veri biçimlendirmesini <xref:System.Windows.Forms.DataGridViewCellStyle> sınıfı. Kullanabileceğiniz <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> açıklanan biçim belirticilerini kullanma geçerli varsayılan kültür için tarih, saat, sayı ve numaralandırma değerlerini biçimlendirmek için özellik [biçimlendirme türleri](../../../../docs/standard/base-types/formatting-types.md). Ayrıca bu değerleri kullanarak belirli kültürler için biçimlendirebilirsiniz <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A> özelliği. Belirtilen biçim verileri görüntüleyen ve belirtilen biçimde kullanıcının girdiği verileri ayrıştırmak için kullanılır.  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle> Sınıfı wordwrap, metin hizalamasını ve null veritabanı değerlerini özel görüntüsünü için ek biçimlendirme özellikleri sağlar. Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms DataGridView denetiminde veri biçimlendirme](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md).  
  
## <a name="formatting-with-the-cellformatting-event"></a>CellFormatting olayla biçimlendirme  
 Temel biçimlendirme ihtiyaçlarınızı karşılamıyorsa, özel veri için bir işleyici biçimlendirme sağlayabilir <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> olay. <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> İşleyiciye sahip bir <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> başlangıçta hücre değeri içeren özellik. Normalde, bu değeri otomatik olarak görüntü türünü dönüştürülür. Değeri kendiniz dönüştürmek için ayarlanmış <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> görüntü türünde bir değer özelliği.  
  
> [!NOTE]
>  Bir biçim dizesi hücre için etkinse, değişikliği geçersiz kılar <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> özellik değerini ayarladığınız sürece <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.FormattingApplied%2A> özelliğine `true`.  
  
 <xref:System.Windows.Forms.DataGridView.CellFormatting> Olay olduğunda da yararlı ayarlamak istediğiniz <xref:System.Windows.Forms.DataGridViewCellStyle> özelliklerini tek tek hücreler için temel değerlerine göre. Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms DataGridView denetiminde veri biçimlendirmeyi özelleştirme](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
 Varsayılan kullanıcı tarafından belirtilen değerlerinin ayrıştırılmasını ihtiyaçlarınızı karşılamıyorsa işleyebilir <xref:System.Windows.Forms.DataGridView.CellParsing> olayı <xref:System.Windows.Forms.DataGridView> özel ayrıştırma sağlamak üzere Denetim.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 [Windows Forms DataGridView Denetiminde Verileri Görüntüleme](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView Denetimindeki Hücre Stilleri](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Nasıl yapılır: Windows Forms DataGridView Denetiminde Verileri Biçimlendirme](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md)  
 [Nasıl yapılır: Windows Forms DataGridView Denetiminde Veri Biçimlendirmeyi Özelleştirme](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
