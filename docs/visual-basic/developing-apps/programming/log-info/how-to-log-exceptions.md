---
title: "Nasıl Yapılır: Visual Basic'te Günlük Özel Durumları"
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, logging
- exceptions, tracking
ms.assetid: a26c60e2-ae39-444a-aebb-33eccadc0eeb
ms.openlocfilehash: b8ec45f43438f8181d9e045cdf43c81db34e4242
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-log-exceptions-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Günlük Özel Durumları
Kullanabileceğiniz `My.Application.Log` ve `My.Log` oluşan özel durumlar hakkında bilgi, uygulamanızda oturum nesneleri. Bu örnekler nasıl kullanılacağını `My.Application.Log.WriteException` açıkça catch özel durumları ve işlenmeyen özel durumları günlüğe kaydetmek için yöntem.  
  
 İzleme bilgilerini günlüğe kaydetme için kullanmak `My.Application.Log.WriteEntry` yöntemi. Daha fazla bilgi için bkz: <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
  
### <a name="to-log-a-handled-exception"></a>İşlenmiş özel durumu günlüğe kaydetmek için  
  
1.  Özel durum bilgilerini oluşturur yöntemi oluşturun.  
  
     [!code-vb[VbVbalrMyApplicationLog#9](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_1.vb)]  
  
2.  Kullanım bir `Try...Catch` Özel catch bloğu.  
  
     [!code-vb[VbVbalrMyApplicationLog#6](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_2.vb)]  
  
3.  Bir özel durum üretebilir kod put `Try` bloğu.  
  
     Açıklamadan çıkarın `Dim` ve `MsgBox` neden satırları bir <xref:System.NullReferenceException> özel durum.  
  
     [!code-vb[VbVbalrMyApplicationLog#7](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_3.vb)]  
  
4.  İçinde `Catch` engellemek, kullanın `My.Application.Log.WriteException` yöntemi özel durum bilgilerini yazar.  
  
     [!code-vb[VbVbalrMyApplicationLog#8](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_4.vb)]  
  
     Aşağıdaki örnekte bir özel durumu günlüğe kaydetme için tam kod gösterilir.  
  
     [!code-vb[VbVbalrMyApplicationLog#10](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_5.vb)]  
  
### <a name="to-log-an-unhandled-exception"></a>İşlenmeyen bir özel durum günlüğe kaydetmek için  
  
1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünde seçin **özellikleri**.  
  
2.  Tıklatın **uygulama** sekmesi.  
  
3.  Tıklatın **uygulama olaylarını görüntüle** düğmesi kod düzenleyicisini açın.  
  
     Bu ApplicationEvents.vb dosyasını açar.  
  
4.  Kod düzenleyicisinde açın ApplicationEvents.vb dosyası vardır. Üzerinde **genel** menüsünde seçin **MyApplication olayları**.  
  
5.  Üzerinde **bildirimleri** menüsünde seçin **UnhandledException**.  
  
     Uygulama başlatır <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> ana uygulama çalıştırılmadan önce olay.  
  
6.  Ekleme `My.Application.Log.WriteException` yönteme `UnhandledException` olay işleyicisi.  
  
     [!code-vb[VbVbalrMyApplicationLog#4](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_6.vb)]  
  
     Aşağıdaki örnek, işlenmeyen bir özel durum günlüğe kaydetme için tam kod gösterilir.  
  
     [!code-vb[VbVbalrMyApplicationLog#5](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_7.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [Nasıl Yapılır: Günlük İletileri Yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)  
 [İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)  
 [İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
