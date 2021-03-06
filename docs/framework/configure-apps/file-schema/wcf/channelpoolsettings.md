---
title: '&lt;channelPoolSettings&gt;'
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: ad722fbc34617ef7f424d5f1c4418e1e1cb45344
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltchannelpoolsettingsgt"></a>&lt;channelPoolSettings&gt;
Özel bağlama için kanal havuzu ayarlarını belirtir.  
  
 \<system.serviceModel>  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<oneWay >  
\<channelPoolSettings >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<channelPoolSettings  
    idleTimeout"TimeSpan"  
        leaseTimeout"TimeSpan"  
    maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`idleTimeout`|Bir pozitif <xref:System.TimeSpan> kanalları havuzunda boşta kalabileceği kesilmeden önce en uzun süreyi belirtir. Varsayılan değer 00:02:00 ' dir.|  
|`leaseTimeout`|A <xref:System.TimeSpan> sonra havuza geri döner olduğunda bir kanal kapalı zaman aralığını belirtir. Varsayılan değer 00:10: 00'dır.|  
|`maxOutboundChannelsPerEndpoint`|Her uzak uç nokta için havuzunda saklanan kanalları en fazla sayısını belirtir pozitif bir tamsayı. Varsayılan değer 10'dur.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<oneWay >](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)|Paket için özel bir bağlama yönlendirmesini etkinleştirir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kotalar aşırı kaynaklarının kullanımını engellemek için bir ilke mekanizması olarak kullanılır. Bunlar kötü amaçlı veya istenmeyen hizmet reddi (DOS) saldırılarını önler. Bu öğe kanal kotaları özel bir kanalda ayarlarken kullanın.  
  
 `ChannelPoolSettings` üç kotaları belirtir:  
  
-   `idleTimeout` Kota sunucusundaki kaynakları uzun bir süre için bağlamadan kullanan hizmet reddi (DOS) saldırıları azaltmak için kullanılır. İstemci üzerinde doğru değeri ayarı hizmetiyle bağlayan güvenilirliğini artırabilir. Varsayılan değer ölçülü uygun tahsis edilen kaynakların temel alır. Bir geliştirme ortamı ve küçük yükleme senaryoları için uygun olan. Hizmet yöneticileri, yüklemenin kaynakları tükendi çalıştırıyorsa veya ek kaynaklar kullanılabilirlik rağmen bağlantıları sınırlı değeri gözden geçirmelidir.  
  
-   `leaseTimeout` Kotası için kullanılan yük dengeleyici ile tümleştirme için ve güvenilirlik geliştirmek için. Varsayılan değer koruyucu tahsis edilen kaynakların temel alır. Bir geliştirme ortamı ve küçük yükleme senaryoları için uygun olan. Hizmet yöneticileri, yüklemenin kaynakları tükendi çalıştırıyorsa veya ek kaynaklar kullanılabilirlik rağmen bağlantıları sınırlı değeri gözden geçirmelidir.  
  
-   `maxOutboundChannelsPerEndpoint` Kota hem sunucu hem de istemci önbellek sınırlarını ayarlar ve güvenilirliğini artırmak için kullanılır. Varsayılan değer bir geliştirme ortamı ve küçük yükleme senaryoları için uygun bir ölçülü uygun ayırma kaynakların temel alır. Hizmet yöneticileri, yüklemenin kaynakları tükendi çalıştırıyorsa veya ek kaynaklar kullanılabilirlik rağmen bağlantıları sınırlı değeri gözden geçirmelidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>  
 <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>  
 <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [\<oneWay >](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Bağlamaları Genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Özel Bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
