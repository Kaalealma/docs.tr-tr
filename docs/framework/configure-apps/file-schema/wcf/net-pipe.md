---
title: '&lt;NET.pipe&gt;'
ms.date: 03/30/2017
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
ms.openlocfilehash: 71291b1163ffb4e5fe13ff18d88d47f7d2193497
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="ltnetpipegt"></a>&lt;NET.pipe&gt;
Adlandırılmış kanal etkinleştirme adlandırılmış kanal bağlantısı ömrü yöneten ve Adlandırılmış Kanallar üzerinden gelmesini etkinleştirme isteklerini yürüten hizmeti, yapılandırma ayarlarını belirtir.  
  
 \<system.serviceModel.activation>  
\<NET.pipe >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.pipe maxPendingAccepts="Integer"  
                    maxPendingConnections="Integer"  
          receiveTimeout="TimeSpan">  
          <allowAccounts>  
             // LocalSystem account  
             <add securityIdentifier="S-1-5-18"/>  
             // LocalService account  
             <add securityIdentifier="S-1-5-19"/>  
             // Administrators account  
             <add securityIdentifier="S-1-5-20"/>  
             // Network Service account  
             <add securityIdentifier="S-1-5-32-544" />  
             // IIS_IUSRS account (Vista only)  
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.pipe>  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="type"></a>Tür  
 `Type`  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`maxPendingAccepts`|Dinleme bitiş Paylaşım Hizmeti için en çok bekleyen eşzamanlı kabul iş parçacığı belirten bir tamsayı. Varsayılan değer 2'dir.|  
|`maxPendingConnections`|En fazla gönderim için bekleyebilirsiniz bağlantı sayısını belirten bir tamsayı. Varsayılan değer 100'dür.|  
|`receiveTimeout`|A `TimeSpan` çerçeveleme veri okumak ve altı çizili bağlantılarından bağlantı gönderme gerçekleştirmek için zaman aşımını belirtir. Varsayılan değer "00: 00:10"|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<allowAccounts >](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|Bir koleksiyon içeren yapılandırma öğelerinin bir `securityIdentifier` özniteliği barındıran WCF hizmetleri ve Paylaşım Hizmeti bağlantı erişim izni verilen işlemler için kullanıcı hesaplarını belirtin.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|Dinleyici işlem SMSvcHost.exe için yapılandırma ayarlarını içerir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>
