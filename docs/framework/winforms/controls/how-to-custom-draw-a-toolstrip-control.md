---
title: 'Nasıl yapılır: Bir ToolStrip Denetimini Özel Olarak Çizme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms], custom drawing
- drawing [Windows Forms], owner
- ProfessionalColorTable class [Windows Forms], overriding
- examples [Windows Forms], toolbars
- drawing [Windows Forms], custom
- toolbars [Windows Forms], changing colors
- ToolStrip control [Windows Forms], drawing
- ToolStrip control [Windows Forms], changing colors
- custom drawing
- owner drawing
ms.assetid: 94e7d7bd-a752-441c-b5b3-7acf98881163
ms.openlocfilehash: 09d9654bf1a2670c77a4a3db2eae2ed7ab6dbfec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-custom-draw-a-toolstrip-control"></a>Nasıl yapılır: Bir ToolStrip Denetimini Özel Olarak Çizme
<xref:System.Windows.Forms.ToolStrip> Denetimleriniz aşağıdaki sınıfları (boyama) işleme ilişkili:  
  
-   <xref:System.Windows.Forms.ToolStripSystemRenderer> işletim sisteminizi stili ve görünümünü sağlar.  
  
-   <xref:System.Windows.Forms.ToolStripProfessionalRenderer> Microsoft Office stili ve görünümünü sağlar.  
  
-   <xref:System.Windows.Forms.ToolStripRenderer> diğer iki işleme sınıfları için Özet temel sınıftır.  
  
 Özel çizim (sahibi çizim da bilinir) için bir <xref:System.Windows.Forms.ToolStrip>, oluşturucu sınıflarından biri geçersiz kılma ve bir işleme mantığı yönünü değiştirin.  
  
 Aşağıdaki yordamlar, özel çizim çeşitli yönlerini açıklar.  
  
### <a name="to-switch-between-the-provided-renderers"></a>Sağlanan Oluşturucu arasında geçiş yapmak için  
  
-   Ayarlama <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> özelliğine <xref:System.Windows.Forms.ToolStripRenderMode> istediğiniz değer.  
  
     İle <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>, statik <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> uygulamanız için oluşturucu belirler. Diğer değerlerini <xref:System.Windows.Forms.ToolStripRenderMode> olan <xref:System.Windows.Forms.ToolStripRenderMode.Custom>, <xref:System.Windows.Forms.ToolStripRenderMode.Professional>, ve <xref:System.Windows.Forms.ToolStripRenderMode.System>.  
  
### <a name="to-change-the-microsoft-officestyle-borders-to-straight"></a>Microsoft Office – stil kenarlıkları doğrudan değiştirmek için  
  
-   Geçersiz kılma <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType>, ancak temel sınıfı çağırmayın.  
  
> [!NOTE]
>  Bu yöntem için sürümü <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripSystemRenderer>, ve <xref:System.Windows.Forms.ToolStripProfessionalRenderer>.  
  
### <a name="to-change-the-professionalcolortable"></a>ProfessionalColorTable değiştirmek için  
  
-   Geçersiz kılma <xref:System.Windows.Forms.ProfessionalColorTable> ve istediğiniz renkleri değiştirin.  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As _  
    System.EventArgs) Handles Me.Load  
        Dim t As MyColorTable = New MyColorTable  
        ToolStrip1.Renderer = New ToolStripProfessionalRenderer(t)  
    End Sub  
  
    Class MyColorTable   
    Inherits ProfessionalColorTable  
  
    Public Overrides ReadOnly Property ButtonPressedGradientBegin() As Color  
        Get  
            Return Color.Red  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonPressedGradientMiddle() _  
    As System.Drawing.Color  
        Get  
            Return Color.Blue  
        End Get  
            End Property  
  
    Public Overrides ReadOnly Property ButtonPressedGradientEnd() _  
    As System.Drawing.Color  
        Get  
            Return Color.Green  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonSelectedGradientBegin() _  
    As Color  
        Get  
            Return Color.Yellow  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonSelectedGradientMiddle() As System.Drawing.Color  
        Get  
            Return Color.Orange  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonSelectedGradientEnd() _  
    As System.Drawing.Color  
        Get  
            Return Color.Violet  
        End Get  
    End Property  
    End Class  
    ```  
  
### <a name="to-change-the-rendering-for-all-toolstrip-controls-in-your-application"></a>İşleme, uygulamanızdaki tüm ToolStrip denetimleri için değiştirmek için  
  
1.  Kullanım <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> özelliği sağlanan Oluşturucu birini seçin.  
  
2.  Kullanım <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> özel Oluşturucu atamak için.  
  
3.  Emin <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> varsayılan değer olarak ayarlı <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-the-entire-application"></a>Microsoft Office renkleri tüm uygulama için devre dışı bırakmak için  
  
-   Ayarlama <xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType> için `false`.  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-one-toolstrip-control"></a>Microsoft Office renklerini bir ToolStrip denetimi için devre dışı bırakmak için  
  
-   Aşağıdaki kod örneğine benzer bir kod kullanın.  
  
    ```vb  
    Dim colorTable As ProfessionalColorTable()  
    colorTable.UseSystemColors = True  
    Dim toolStrip.Renderer As ToolStripProfessionalRenderer(colorTable)  
    ```  
  
    ```csharp  
    ProfessionalColorTable colorTable = new ProfessionalColorTable();  
    colorTable.UseSystemColors = true;  
    toolStrip.Renderer = new ToolStripProfessionalRenderer(colorTable);  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ToolStripSystemRenderer>  
 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>  
 <xref:System.Windows.Forms.ToolStripRenderer>  
 [Yerleşik Sahip Çizimi Destekli Denetimler](../../../../docs/framework/winforms/controls/controls-with-built-in-owner-drawing-support.md)  
 [Nasıl yapılır: Windows Forms'da ToolStrip Denetimi için Özel Oluşturucu Oluşturma ve Ayarlama](../../../../docs/framework/winforms/controls/create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
 [ToolStrip Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
