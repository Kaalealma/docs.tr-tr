---
title: NetHttpBinding Kullanma
ms.date: 03/30/2017
ms.assetid: fe134acf-ceca-49de-84a9-05a37e3841f1
ms.openlocfilehash: a753cca008c7eb9b500afa7f3f3b55b5410522a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="using-the-nethttpbinding"></a>NetHttpBinding Kullanma
<xref:System.ServiceModel.NetHttpBinding> HTTP veya WebSocket Hizmetleri kullanma için tasarlanmış bir bağlama ve ikili kodlama varsayılan olarak kullanır. <xref:System.ServiceModel.NetHttpBinding> İstek-yanıt sözleşmesi ya da çift yönlü sözleşme ile kullanılan olup olmadığını algılar ve eşleşecek şekilde davranışını değiştirme - Bunu HTTP istek-yanıt sözleşmeleri ve WebSockets için çift yönlü sözleşmeler için kullanır. Bu davranış kullanılarak geçersiz kılınabilir <!--zz <xref:System.ServiceModel.NetHttpBinding.WebSocketTransportUsage%2A> --> `WebSocketTransportUsage` ayarı:  
  
1.  Her zaman - bu bile istek-yanıt sözleşmeleri için kullanılacak WebSockets zorlar.  
  
2.  Hiçbir zaman - bu WebSockets kullanılmasını engeller. Çift yönlü sözleşme ile bu ayarı kullanın çalışılırken bir özel durum neden olur.  
  
3.  WhenDuplex - bu varsayılan değerdir ve yukarıda açıklandığı gibi davranır.  
  
 <xref:System.ServiceModel.NetHttpBinding> güvenilir oturumlar, hem HTTP modu hem de WebSocket modu destekler. WebSocket içinde modu oturumları taşıma tarafından sağlanır.  
  
> [!WARNING]
>  Kullanırken <xref:System.ServiceModel.NetHttpBinding> ve bağlamanın TransferMode TransferMode.Streamed için ayarlandığında, kilitlenme ve çağrı zaman aşımı geniş akışlar neden olabilir. Bu sorunu gönderme küçük ileti çalışma veya TransferMode.Buffered kullanmak için.  
  
## <a name="configuring-a-service-to-use-nethttpbinding"></a>NetHttpBinding kullanmak için bir hizmet yapılandırma  
 <xref:System.ServiceModel.NetHttpBinding> Olabilir aynı yapılandırılmış başka herhangi bir bağlama. Bir WCF Hizmeti ile yapılandırma aşağıdaki yapılandırma parçacığını gösterilmektedir <xref:System.ServiceModel.NetHttpBinding>.  
  
```xml  
<system.serviceModel>  
    <services>  
      <service name="WcfService1.Service1">  
        <endpoint address=""  
                  binding="netHttpBinding"  
                  contract="WcfService1.IService1"/>  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange"/>  
      </service>  
    </services>  
    <bindings>  
      <netHttpBinding>  
        <binding name="My_NetHttpBindingConfig">  
          <webSocketSettings transportUsage="WhenDuplex"/>  
        </binding>  
      </netHttpBinding>  
    </bindings>  
    <!- ... -->   
  </system.serviceModel>  
```  
  
 Aşağıdaki kod parçacığını nasıl ekleneceğini gösterir <xref:System.ServiceModel.NetHttpBinding> kod.  
  
```csharp  
ServiceHost svchost = new ServiceHost(typeof(Service1), baseAddress);  
            NetHttpBinding binding = new NetHttpBinding();  
            svchost.AddServiceEndpoint(typeof(IService1), binding, address);   
        }  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hizmetler için Bağlamaları Yapılandırma](../../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)  
 [Bağlamalar](../../../../docs/framework/wcf/feature-details/bindings.md)  
 [Sistem Tarafından Sağlanan Bağlamalar](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [Çift Yönlü Hizmetler](../../../../docs/framework/wcf/feature-details/duplex-services.md)
