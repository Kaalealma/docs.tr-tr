---
title: Yapılandırma Olmadan AJAX Hizmeti
ms.date: 03/30/2017
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
ms.openlocfilehash: 53a0de88d08fbc12cb8861042a50da6503fa5def
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="ajax-service-without-configuration"></a>Yapılandırma Olmadan AJAX Hizmeti
Bu örnek Windows Communication Foundation (WCF) herhangi bir yapılandırma kullanmadan bir temel ASP.NET zaman uyumsuz JavaScript ve XML (AJAX) hizmeti (bir Web tarayıcısı istemciden JavaScript kodu kullanarak erişebilirsiniz hizmeti) oluşturmak için nasıl kullanılacağı gösterilmektedir Ayarlar. Hizmet otomatik olarak bir AJAX uç noktayı etkinleştirme .svc dosyasında özel sözdizimini kullanır.  
  
 WCF AJAX desteği ASP.NET AJAX ile kullanmak için en iyisi olan `ScriptManager` denetim. WCF ile ASP.NET AJAX kullanılarak bir örnek için bkz: [Ajax örnekleri](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Bu örnek AJAX hizmeti kullanarak HTTP POST oluşturur. Bölümünde açıklandığı gibi [temel AJAX hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örnek, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> hizmet barındırmak için kullanılır.  

```svc
<%ServiceHost  
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CalculatorService  
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"  
%>  
```

 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> otomatik olarak ekler bir <xref:System.ServiceModel.Description.WebScriptEndpoint> hizmet. Hiçbir yapılandırma değişikliği uç noktasına yapılması gerekiyorsa `<system.ServiceModel>` bölüm tamamen kaldırılabilir hizmeti için Web.config dosyasından. Web.config dosyası ConfigFreeClientPage.aspx tarafından kullanılan bazı ASP.NET ayarları içerir. Durum değildi, tüm Web.config dosyası kaldırılamadı.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Kurulum yönergeleri gerçekleştirdiğinizden emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm ConfigFreeAjaxService.sln açıklandığı gibi yapı [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Gidin http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx (ConfigFreeClientPage.aspx tarayıcıda proje dizininde açık değil).  
  
> [!NOTE]
>  Lütfen bu örnek çalıştırırken, anonim kimlik doğrulaması ve Windows kimlik doğrulaması aynı anda IIS ServiceModelSamples klasörü için etkin olmadığını emin olun. Lütfen bu durumda, Windows kimlik doğrulamasını devre dışı bırakın. Örnek çalıştırdıktan sonra Windows kimlik doğrulamasını etkinleştirmek ve "iisreset" çalıştırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temel AJAX Hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
