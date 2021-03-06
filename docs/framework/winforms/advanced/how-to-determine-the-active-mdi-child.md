---
title: 'Nasıl yapılır: Etkin MDI Alt Öğesini Belirleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Clipboard [Windows Forms], copying data to
- MDI [Windows Forms], child windows
- child forms
- MDI [Windows Forms], activating forms
- MDI [Windows Forms], locating focus
ms.assetid: 33880ec3-0207-4c2b-a616-ff140443cc0f
ms.openlocfilehash: 0b084d204361764af1b36b154acfc5b360fc977e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-determine-the-active-mdi-child"></a>Nasıl yapılır: Etkin MDI Alt Öğesini Belirleme
Bazen, şu anda etkin alt formdaki odağa sahip denetimindeki çalışır bir komut sağlamak isteyeceksiniz. Örneğin, seçili metnin alt formun metin kutusunda panoya kopyalamak istediğinizi varsayalım. Seçili metni panoya kullanmaya kopyalar bir yordam oluşturacak <xref:System.Windows.Forms.Control.Click> Standart Düzen menüsünde kopyalama menü öğesinin olay.  
  
 MDI uygulamanın aynı alt formun sayıda örneği olduğundan yordamı kullanmak için hangi form bilmesi gerekir. Doğru biçimde belirtmek için kullanın <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> odaklı veya, en son etkin alt form döndürür özelliği.  
  
 Bir form üzerinde bazı denetimler sahip olduğunuzda, ayrıca hangi denetimi etkinse belirtmeniz gerekir. Gibi <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> özelliği, <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> özelliği etkin alt form üzerinde denetimi odağa sahip döndürür. Aşağıdaki yordamda bir alt form menüsünde MDI formu veya bir araç çubuğu düğmesi menüsünde adlı bir kopya yordam gösterilmektedir.  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a>(Metni panoya kopyalamak için) etkin MDI alt belirlemek için  
  
1.  Bir yöntem etkin denetim etkin alt biçiminde metni panoya kopyalayın.  
  
    > [!NOTE]
    >  Bu örnek bir MDI ana formu olduğunu varsayar (`Form1`) içeren bir veya daha fazla MDI alt pencereleri olan bir <xref:System.Windows.Forms.RichTextBox> denetim. Daha fazla bilgi için bkz: [MDI üst formları oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md).  
  
    ```vb  
    Public Sub mniCopy_Click(ByVal sender As Object, _  
       ByVal e As System.EventArgs) Handles mniCopy.Click  
  
       ' Determine the active child form.  
       Dim activeChild As Form = Me.ActiveMDIChild  
  
       ' If there is an active child form, find the active control, which  
       ' in this example should be a RichTextBox.  
       If (Not activeChild Is Nothing) Then  
          Dim theBox As RichTextBox = _  
            TryCast(activeChild.ActiveControl, RichTextBox)  
  
          If (Not theBox Is Nothing) Then  
             'Put selected text on Clipboard.  
             Clipboard.SetDataObject(theBox.SelectedText)  
          Else  
             MessageBox.Show("You need to select a RichTextBox.")  
          End If  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    protected void mniCopy_Click (object sender, System.EventArgs e)  
    {  
       // Determine the active child form.  
       Form activeChild = this.ActiveMdiChild;  
  
       // If there is an active child form, find the active control, which  
       // in this example should be a RichTextBox.  
       if (activeChild != null)  
       {    
          try  
          {  
             RichTextBox theBox = (RichTextBox)activeChild.ActiveControl;  
             if (theBox != null)  
             {  
                // Put the selected text on the Clipboard.  
                Clipboard.SetDataObject(theBox.SelectedText);  
  
             }  
          }  
          catch  
          {  
             MessageBox.Show("You need to select a RichTextBox.");  
          }  
       }  
    }  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çok Belgeli Arabirim (MDI) Uygulamaları](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [Nasıl yapılır: MDI Üst Formları Oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [Nasıl yapılır: MDI Alt Formları Oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [Nasıl yapılır: Etkin MDI Alt Öğesine Veri Gönderme](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 [Nasıl yapılır: MDI Alt Formlarını Düzenleme](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)
