---
title: 'Nasıl yapılır: Tıklamalar ve Çift Tıklamaları Birbirinden Ayırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- mouse [Windows Forms], click
- mouse [Windows Forms], double-click
- mouse clicks [Windows Forms], single versus double
ms.assetid: d836ac8c-85bc-4f3a-a761-8aee03dc682c
ms.openlocfilehash: 6c8603df5a844fb93db0555b605f16235b9dff54
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-distinguish-between-clicks-and-double-clicks"></a>Nasıl yapılır: Tıklamalar ve Çift Tıklamaları Birbirinden Ayırma
Genellikle, bir tek *tıklatın* bir kullanıcı arabirimi (UI) eylemi başlatır ve *çift tıklatın* eylemi genişletir. Örneğin, tek bir tıklatmayla genellikle bir öğe seçer ve seçilen öğeyi çift tıklatma düzenler. Ancak, Windows Forms tıklama olayları bir eylem bağlı olduğundan kolayca burada bir tıklatma ve çift tıklatma gerçekleştirmek uyumsuz Eylemler, bir senaryoda çalışmak değil <xref:System.Windows.Forms.Control.Click> veya <xref:System.Windows.Forms.Control.MouseClick> olay, eyleminden önce bağlıgerçekleştirilir<xref:System.Windows.Forms.Control.DoubleClick>veya <xref:System.Windows.Forms.Control.MouseDoubleClick> olay. Bu konuda bu sorunun iki çözümü gösterilir. Bir çözüm, çift tıklatma olayını işlemek ve eylemleri click olayını işlemede geri almaktır. Nadir durumlarda, davranış işleyerek çift tıklayın ve tıklatın benzetimini gerekebilir <xref:System.Windows.Forms.Control.MouseDown> olay ve kullanarak <xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A> ve <xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A> özelliklerini <xref:System.Windows.Forms.SystemInformation> sınıfı. Tıklama ve ikinci bir tıklatma değeri önce oluşursa arasındaki süreyi ölçmek <xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A> ulaşıldığında ve tıklatın tarafından tanımlanan bir dikdörtgen içinde <xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A>, çift tıklatma eylemi gerçekleştirir; Aksi halde, tıklatma eylemi gerçekleştirin.  
  
### <a name="to-roll-back-a-click-action"></a>Bir tıklatma eylemi geri almak için  
  
-   Çalıştığınız denetim standart sahip olduğundan emin olun davranışı çift tıklayın. Değilse, denetimle etkinleştirmek <xref:System.Windows.Forms.Control.SetStyle%2A> yöntemi. Çift tıklatma olayını işlemek ve çift tıklatma eylemi yanı sıra tıklatma eylemi geri alma. Aşağıdaki kod örneği gösterilmiştir çift tıklatma eylemi çift olay kod işleme geri almak nasıl yanı sıra etkin ile özel bir düğme oluşturmak için.  
  
     [!code-csharp[System.Windows.Forms.ButtonDoubleClick#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ButtonDoubleClick/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ButtonDoubleClick#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ButtonDoubleClick/VB/Form1.vb#1)]  
  
### <a name="to-distinguish-between-clicks-in-the-mousedown-event"></a>MouseDown olayı tıklama ayırt etmek için  
  
-   İşleme <xref:System.Windows.Forms.Control.MouseDown> olay ve saat ve konum span uygun kullanarak tıklamaları belirlemek <xref:System.Windows.Forms.SystemInformation> özellikleri ve bir <xref:System.Windows.Forms.Timer> bileşeni. Olup tıklatın ya da çift gerçekleşir bağlı olarak uygun eylemi gerçekleştirin. Aşağıdaki kod örneği, bu nasıl yapılabilir gösterir.  
  
     [!code-cpp[System.Windows.Forms.SingleVersusDoubleClick#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/cpp/form1.cpp#0)]
     [!code-csharp[System.Windows.Forms.SingleVersusDoubleClick#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/CS/form1.cs#0)]
     [!code-vb[System.Windows.Forms.SingleVersusDoubleClick#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnekler gerektirir:  
  
-   Sistem, System.Drawing ve System.Windows.Forms derlemelerine başvurular.  
  
 Visual Basic veya Visual C# için bu örnekler komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Yeni projelere kodu yapıştırılarak Visual Studio'da bu örnekler de oluşturabilirsiniz.  Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir Windows Forms Uygulamasında Fare Girdisi](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
