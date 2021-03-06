---
title: '&lt;serviceDebug&gt;'
ms.date: 03/30/2017
ms.assetid: 6d7ea986-f232-49fe-842c-f934d9966889
ms.openlocfilehash: 0a0c6a45b6103d533a87a921e6e428bf30d81b20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="ltservicedebuggt"></a>&lt;serviceDebug&gt;
Windows Communication Foundation (WCF) hizmeti için hata ayıklama ve Yardım bilgileri özellikleri belirtir.  
  
 \<system.ServiceModel>  
\<davranışları >  
\<serviceBehaviors>  
\<davranışı >  
\<serviceDebug >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<serviceDebug     httpHelpPageBinding="String"    httpHelpPageBindingConfiguration="String"  
    httpHelpPageEnabled="Boolean"  
    httpHelpPageUrl="Uri"  
    httpsHelpPageBinding="String"    httpsHelpPageBindingConfiguration="String"  
    httpsHelpPageEnabled="Boolean"  
    httpsHelpPageUrl="Uri"  
    includeExceptionDetailInFaults="Boolean" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|httpHelpPageBinding|Kullanılırken HTTP hizmeti Yardım sayfası erişmek için kullanılacak bağlama türünü belirten bir dize değeri.<br /><br /> Destek iç bağlama öğeleri yalnızca bağlamalarla <xref:System.ServiceModel.Channels.IReplyChannel?displayProperty=nameWithType> desteklenecektir. Ayrıca, <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> bağlama özelliğini olmalıdır <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>.|  
|httpHelpPageBindingConfiguration|Belirtilen bağlama adını belirten dize `httpHelpPageBinding` Bu bağlama ek yapılandırma bilgilerinin başvuran özniteliği. Aynı adı tanımlanmalıdır `<bindings>` bölümü.|  
|httpHelpPageEnabled|Bir Boole değeri tarafından belirtilen adresten HTML Yardım sayfası WCF yayımlar olup olmadığını denetleyen değeri `httpHelpPageUrl` özniteliği. Varsayılan, `true` değeridir.<br /><br /> Bu özelliği ayarlamak `false` HTML tarayıcıları görünür bir HTML Yardım sayfası yayımlanmasını devre dışı bırakmak için.<br /><br /> HTML Yardımı emin olmak için sayfası tarafından denetlenen konumunda yayımlanır `httpHelpPageUrl` özniteliği bu öznitelik ayarlamalısınız `true`. Ayrıca, aşağıdaki koşullardan biri de karşılanması gerekir:<br /><br /> - `httpHelpPageUrl` Özniteliktir, HTTP protokol düzeni destekleyen mutlak bir adres.<br />-HTTP protokol düzeni destekleyen hizmet için temel bir adresi yok.<br /><br /> HTTP protokolü düzenini desteklemiyor mutlak bir adres atanırsa özel durum oluşur ancak `httpHelpPageUrl` özniteliği, hangi hiçbiri önceki ölçüt içinde olduğu herhangi bir özel durumu ve hiçbir HTML Yardım sayfası ölç sonuçlarında senaryo.|  
|httpHelpPageUrl|Göreli veya mutlak HTTP tabanlı URL'yi özel HTML belirtir bir URI yardımcı bir HTML tarayıcı kullanarak uç nokta görüntülendiğinde kullanıcı görür dosya.<br /><br /> Bu öznitelik, bir HTTP/Get isteğinden Örneğin, bir HTML tarayıcısından döndürülen özel bir HTML Yardım dosyasını kullanımını etkinleştirmek için kullanabilirsiniz. HTML Yardım dosyasının konumunu gibi çözümlenir.<br /><br /> 1.  Bu özniteliğin değeri göreli bir adres ise, HTML Yardım dosyasının konumunu HTTP isteklerini destekler hizmeti temel adresi değerinin yanı sıra, bu özellik değeri ' dir.<br />2.  Bu özniteliğin değeri mutlak bir adres ise ve HTTP isteklerini destekler, HTML Yardım dosyasını bu özelliğin değeri konumudur.<br />3.  Bu özniteliğin değeri mutlak ancak HTTP isteklerini desteklemez, özel durum oluşur.<br /><br /> Bu öznitelik yalnızca olduğunda geçerlidir olan `httpHelpPageEnabled` özniteliği `true`.|  
|httpsHelpPageBinding|Kullanılırken HTTPS hizmeti Yardım sayfası erişmek için kullanılacak bağlama türünü belirten bir dize değeri.<br /><br /> Destek iç bağlama öğeleri yalnızca bağlamalarla <xref:System.ServiceModel.Channels.IReplyChannel> desteklenecektir. Ayrıca, <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> bağlama özelliğini olmalıdır <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>.|  
|httpsHelpPageBindingConfiguration|Belirtilen bağlama adını belirten dize `httpsHelpPageBinding` Bu bağlama ek yapılandırma bilgilerinin başvuran özniteliği. Aynı adı tanımlanmalıdır `<bindings>` bölümü.|  
|httpsHelpPageEnabled|Bir Boole değeri tarafından belirtilen adresten HTML Yardım sayfası WCF yayımlar olup olmadığını denetleyen değeri `httpsHelpPageUrl` özniteliği. Varsayılan, `true` değeridir.<br /><br /> Bu özelliği ayarlamak `false` HTML tarayıcıları görünür bir HTML Yardım sayfası yayımlanmasını devre dışı bırakmak için.<br /><br /> HTML Yardımı emin olmak için sayfası tarafından denetlenen konumunda yayımlanır `httpsHelpPageUrl` özniteliği bu öznitelik ayarlamalısınız `true`. Ayrıca, aşağıdaki koşullardan biri de karşılanması gerekir:<br /><br /> - `httpsHelpPageUrl` Özniteliktir HTTPS protokolü düzenini destekler mutlak bir adres.<br />-HTTPS protokolü şeması destekleyen hizmet için temel bir adresi yok.<br /><br /> HTTPS protokolü şeması desteklemiyor mutlak bir adres atanırsa özel durum oluşur ancak `httpsHelpPageUrl` özniteliği, hangi hiçbiri önceki ölçüt içinde olduğu herhangi bir özel durumu ve hiçbir HTML Yardım sayfası ölç sonuçlarında senaryo.|  
|httpsHelpPageUrl|Göreli veya mutlak HTTPS tabanlı URL'sini özel HTML belirten bir URI yardımcı bir HTML tarayıcı kullanarak uç nokta görüntülendiğinde kullanıcı görür dosya.<br /><br /> Bu öznitelik, bir HTTPS/Get isteğinden Örneğin, bir HTML tarayıcısından döndürülen özel bir HTML Yardım dosyasını kullanımını etkinleştirmek için kullanabilirsiniz. HTML Yardım dosyasının konumunu gibi çözümlendi:<br /><br /> -Bu özelliğin değeri göreli bir adres ise, HTML Yardım dosyasının konumunu HTTPS isteklerini destekler hizmeti temel adresi değerinin yanı sıra, bu özellik değeri ' dir.<br />-Bu özelliğin değerinin mutlak bir adres ise ve HTTPS isteklerini destekler, HTML Yardım dosyasını bu özelliğin değeri konumudur.<br />-Bu özelliğin değerinin mutlak ancak HTTPS isteklerini desteklemez, özel durum oluşur.<br /><br /> Bu öznitelik yalnızca olduğunda geçerlidir olan `httpHelpPageEnabled` özniteliği `true`.|  
|IncludeExceptionDetailInFaults|Hata ayıklama amacıyla istemciye döndürülen SOAP hatalarının ayrıntılı yönetilen özel durum bilgileri dahil edilip edilmeyeceğini belirten bir değer. Varsayılan, `false` değeridir.<br /><br /> Bu öznitelik ayarlanırsa, `true`, hata ayıklama amacıyla istemciye yönetilen özel durum bilgi akışını yanı sıra, Web tarayıcıları hizmetinde atan kullanıcılar için HTML bilgi dosyaları yayımlanmasını etkinleştirebilirsiniz. **Dikkat:** döndürme istemcilere yönetilen özel durum bilgileri, bir güvenlik riski olabilir. Özel durum ayrıntıları yetkisiz istemcileri tarafından kullanılan iç hizmet uygulaması hakkında bilgi kullanıma olmasıdır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranışı >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Bir davranış öğesi belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ayarı `includeExceptionDetailInFaults` için `true` kullanarak özel durum bildirilmedi olsa bile uygulama kodu tarafından oluşturulan özel durumları döndürülecek hizmetin sağlayan <xref:System.ServiceModel.FaultContractAttribute>. Bu ayar, sunucu beklenmeyen bir özel durum burada atma durumlarda hata ayıklama sırasında yararlıdır. Bu öznitelik kullanarak bilinmeyen bir özel durum seri hale getirilmiş bir tür döndürdü ve özel durumun daha fazla ayrıntı inceleyebilirsiniz.  
  
> [!CAUTION]
>  Özel durum ayrıntıları yetkisiz istemcileri tarafından kullanılan iç hizmet uygulaması hakkında bilgi kullanıma sunmak için istemcilere döndürmeyi yönetilen özel durum bilgilerinin bir güvenlik riski olabilir. İlgili güvenlik sorunları nedeniyle yalnızca denetimli hata ayıklama senaryolarında yapmanız önerilir. Ayarlamanız gerekir `includeExceptionDetailInFaults` için `false` uygulamanızı dağıtırken.  
  
 Yönetilen özel durumu ile ilgili güvenlik konuları hakkında daha fazla ayrıntı için bkz: [belirtme ve işleme hataları sözleşme ve hizmetlerde](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md). Kod örneği için bkz: [hizmet hata ayıklama davranışı](../../../../../docs/framework/wcf/samples/service-debug-behavior.md).  
  
 Ayrıca ayarlayabilirsiniz `httpsHelpPageEnabled` ve `httpsHelpPageUrl` etkinleştirme veya devre dışı Yardım sayfası. Her hizmet, isteğe bağlı olarak hizmet için WSDL almak için uç nokta da dahil olmak üzere hizmeti hakkında bilgi içeren bir Yardım sayfası getirebilir. Bu ayarlayarak etkinleştirilebilir `httpHelpPageEnabled` için `true`. Bu hizmetin taban adresi için bir GET isteğine döndürülecek Yardım sayfası sağlar. Bu adresi ayarlayarak değiştirebileceğiniz `httpHelpPageUrl` özniteliği. Ayrıca, bu HTTP yerine HTTPS kullanarak güvenli hale getirebilir.  
  
 İsteğe bağlı `httpHelpPageBinding` ve `httpHelpPageBinding` öznitelikleri hizmet web sayfasına erişmek için kullanılan bağlamaları yapılandırma izin verir. Bunlar belirtilmezse, varsayılan bağlamaları (`HttpTransportBindingElement`, HTTP söz konusu olduğunda ve `HttpsTransportBindingElement`, HTTPS söz konusu olduğunda) uygun şekilde hizmeti Yardım sayfası erişimi için kullanılır. Bu öznitelikler yerleşik WCF bağlamalarla kullanamazsınız dikkat edin. Xref:System.ServiceModel.Channels.IReplyChannel destek iç bağlama öğeleri yalnızca bağlamalarla > desteklenecektir. Ayrıca, <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> bağlama özelliğini olmalıdır <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.ServiceDebugElement>  
 <xref:System.ServiceModel.Description.ServiceDebugBehavior>  
 [Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)  
 [Özel Durum ve Hataları İşleme](../../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)  
 [Hizmet Hata Ayıklama Davranışı](../../../../../docs/framework/wcf/samples/service-debug-behavior.md)
