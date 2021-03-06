---
title: NoPersistScope etkinliği
ms.date: 03/30/2017
ms.assetid: 9a0baeb7-a05c-4fac-b905-252758cb71bb
ms.openlocfilehash: e4779bf28fc2fc1341cce5134a872b108278611c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="nopersistscope-activity"></a>NoPersistScope etkinliği
Bu örnek, bir iş akışındaki serileştirilebilir olmayan ve tek kullanımlık bir durumu işlemek gösterilmiştir. Seri hale getirilemeyen durumu devam ettirmek iş akışları çalışmayın ve ayrıca atılabilir nesnelerinin iş akışında kullanıldıktan sonra Temizlenen önemli olduğunu önemlidir.  
  
## <a name="demonstrates"></a>Gösteriler  
 `NoPersistScope` Özel Etkinlik ve Tasarımcısı.  
  
## <a name="using-the-nopersistzone-activity"></a>NoPersistZone etkinliğini kullanma  
 Örnek iş akışı çalıştığında, özel bir aktivite olarak adlandırılan `CreateTextWriter` türünde bir nesne oluşturur <xref:System.IO.TextWriter> ve bir iş akışı değişkenine kaydeder. <xref:System.IO.TextWriter> olan bir <xref:System.IDisposable> nesnesi. Bu <xref:System.IO.TextWriter>, örnek çalıştığı, dizindeki ' out.txt' adlı bir dosyaya yazmak için yapılandırıldığı tarafından kullanılıyor bir <xref:System.Activities.Statements.WriteLine> etkinlik olarak yazdığınız içinde konsolunda herhangi bir metin görüntülemektedir.  
  
 Echo mantığı içinde çalışan bir `NoPersistScope` iş akışı kalıcı olmasını önler (kodu hangi Ayrıca bu örnek bir parçası) etkinlik. Yazarsanız `unload` konsolunda ana iş akışı örneği kalıcı dener ancak iş akışı içinde kaldığından bu işlem zaman aşımına uğradı bir `NoPersistScope`. İş akışı da adlı özel bir aktivite kullanır `Dispose` silmek için <xref:System.IO.TextWriter> nesne iş akışı tamamlandığında kullanıyor. `Dispose` Etkinlik içinde yerleştirilir <xref:System.Activities.Statements.TryCatch.Finally%2A> , engellemek <xref:System.Activities.Statements.TryCatch> , etkinlik <xref:System.IO.TextWriter> değişkeni bildirilen, bir özel durum Try bloğunun yürütülmesi sırasında gerçekleşeceğini olsa bile bu çalıştığından emin olmak için.  
  
 Yazabilirsiniz `exit` iş akışı örneği tamamlamak ve programdan çıkın.  
  
#### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1.  NoPersistZone.sln çözümde açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın veya seçin **yapı çözümü** gelen **yapı** menüsü.  
  
3.  Derleme başarılı olduktan sonra F5 tuşuna basın veya seçin **hata ayıklamayı Başlat** gelen **hata ayıklama** menü alternatif olarak, CTRL + F5 tuşuna basın veya seçin **hata ayıklama olmadan Başlat** gelen **Hata ayıklama** menü hata ayıklama olmadan çalıştırma.  
  
#### <a name="to-cleanup-optional"></a>Temizleme (isteğe bağlı)  
  
1.  SQL örneği deposuna kaldırmak için Cleanup.cmd çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NoPersistScope`