---
title: Çekme etkinliğini kullanma
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: 9617949d72fb1489f66fec205b260b807d011177
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="using-the-pick-activity"></a>Çekme etkinliğini kullanma
Bu örnek nasıl kullanılacağı ortaya <xref:System.Activities.Statements.Pick> etkinlik.  
  
 <xref:System.Activities.Statements.Pick> Etkinlik olay tabanlı denetim modelleme sağlar. C# benzer şekilde davranır `switch` dallarda yalnızca biri yürütür deyimi `switch` deyimi. Farklı `switch` bir dal yürütüldüğünde deyimi dayalı olarak bir değer üzerinde <xref:System.Activities.Statements.Pick> etkinlik nasıl bir etkinlik tamamlandıktan sonra dayalı bir dal yürütür.  
  
 Bu örnek adlarının konsolunda belirli bir süre içinde yazmak için bir kullanıcıya sorar. <xref:System.Activities.Statements.Pick> Örnek etkinlik sahip olup olmadığını kullanıcı adında 5 saniye içinde veya türleri üzerinde temel yürütülen iki dalı. Kullanıcı adında 5 saniye içinde yazdığında ilk dal, özel bir içeren yürütülür `ReadLine` etkinlik; Aksi takdirde diğer dal, içeren yürütülür bir <xref:System.Activities.Statements.Delay> etkinlik. Bir kullanıcının adını konsolda yazılmış sonra kullanıcı adını konsola yazdırılır. Giriş 5 saniye içinde girilmezse, işlemi zaman aşımına.  
  
## <a name="demonstrates"></a>Gösteriler  
 <xref:System.Activities.Statements.Pick> Etkinlik.  
  
## <a name="discussion"></a>Tartışma  
 Örnek İş Akışı Tasarımcısı ve kodlanmış iş akışı içerir.  
  
 İş Akışı Tasarımcısı  
 Örnek Tasarımcısı sürümü, bir iş akışı Tasarımcısı'nda oluşturma gösterilmiştir. Aşağıdaki dosyalar eklenmiştir:  
  
-   Program.cs: İçerir `Main` örnek iş akışı yürüten işlev.  
  
-   ReadString.cs: bazı giriş konsoldan okuyan bir özel etkinlik.  
  
-   Sequence1.XAML: kullanır çekme Tasarımcı kullanarak bir iş akışı oluşturuldu.  
  
 Kodlanmış iş akışı  
 Örnek kodlanmış sürümü, bir iş akışı Tasarımcısı'nda oluşturma gösterilmiştir. Aşağıdaki dosyalar eklenmiştir:  
  
-   Program.cs: İçerir `Main` örnek iş akışı yürüten işlev.  
  
-   ReadString.cs: bazı giriş konsoldan okuyan bir özel etkinlik.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], Pick.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Çözümü çalıştırmak için F5 tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`