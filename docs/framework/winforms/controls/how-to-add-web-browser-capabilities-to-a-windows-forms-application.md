---
title: 'Nasıl yapılır: Bir Windows Forms Uygulamasına Web Tarayıcısı Yetenekleri Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- WebBrowser control [Windows Forms], adding Web browser capabilities to your application
- WebBrowser control [Windows Forms], examples
- Web browsers [.NET Framework], adding to Windows Forms
- examples [Windows Forms], WebBrowser control
- Windows Forms, adding Web browser functionality
ms.assetid: 3871f072-b57a-435b-9976-e5da28df04a7
ms.openlocfilehash: d106736a288283c58bdc8020cd54b88859454fba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-web-browser-capabilities-to-a-windows-forms-application"></a>Nasıl yapılır: Bir Windows Forms Uygulamasına Web Tarayıcısı Yetenekleri Ekleme
İle <xref:System.Windows.Forms.WebBrowser> denetim, uygulamanıza Web tarayıcısı işlevselliği ekleyebilirsiniz. Denetim varsayılan olarak bir Web tarayıcısı gibi çalışır. İlk URL ayarlayarak yükledikten sonra <xref:System.Windows.Forms.WebBrowser.Url%2A> özelliği gezinmenizi köprüleri tıklayarak veya geri taşımak ve gezinti geçmişinde iletmek için klavye kısayollarını kullanma. Varsayılan olarak, ek tarayıcısı işlevselliği sağ kısayol menüsünden erişebilirsiniz. Yeni belgeler denetimini üzerine bırakarak da açabilirsiniz. <xref:System.Windows.Forms.WebBrowser> Denetimi de sahip çeşitli özellikleri, yöntemleri ve kullanıcı arabirimi özellikleri Internet Explorer'da bulunan benzer uygulamak için kullanabileceğiniz olaylar.  
  
 Aşağıdaki kod örneğinde uygulayan bir adres çubuğuna, tipik tarayıcı düğmeleri bir **dosya** menüsü, durum çubuğu ve geçerli sayfa başlığı görüntüleyen bir başlık çubuğu.  
  
## <a name="example"></a>Örnek  
 [!code-cpp[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CPP/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Başvurular `System,``System.Drawing`, ve `System.Windows.Forms` derlemeler.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.  Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.WebBrowser>  
 [WebBrowser Denetimi](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)
