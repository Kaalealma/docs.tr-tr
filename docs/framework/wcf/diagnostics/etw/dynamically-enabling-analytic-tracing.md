---
title: Analitik İzlemeyi Dinamik Olarak Etkinleştirme
ms.date: 03/30/2017
ms.assetid: 58b63cfc-307a-427d-b69d-9917ff9f44ac
ms.openlocfilehash: 68152741541fdbc048ba290cfb956babaed2e0d7
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="dynamically-enabling-analytic-tracing"></a>Analitik İzlemeyi Dinamik Olarak Etkinleştirme
Windows işletim sistemiyle birlikte araçlarını kullanarak etkinleştirin veya olay izleme için Windows (ETW) kullanarak dinamik olarak izlemeyi devre dışı. Tüm [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] Windows Communication Foundation (WCF) hizmetlerini, çözümleme izleme etkin ve devre dışı dinamik olarak olmadan uygulamanın Web.config dosyasını değiştirme veya hizmeti yeniden başlatılıyor olabilir. Bu izleme olaylarını bozulmadan kalmasını yayar uygulama sağlar.  
  
 WCF izleme seçenekleri benzer şekilde yapılandırılabilir. Örneğin, önem derecesi düzeyini değiştirebilirsiniz **hata** için **bilgi** olmadan uygulamayı açın. Bu yapılabilir aşağıdaki araçları kullanarak:  
  
-   **Logman** – yapılandırma, denetleme ve izleme veri sorgulama için bir komut satırı aracı. Daha fazla bilgi için bkz: [Logman oluşturmak izleme](http://go.microsoft.com/fwlink/?LinkId=165426) ve [Logman güncelleştirme izleme](http://go.microsoft.com/fwlink/?LinkId=165427).  
  
-   **Olay Görüntüleyicisini gözden** -izleme sonuçlarını görüntülemek için Windows grafik yönetim aracıdır. Daha fazla bilgi için bkz: [WCF hizmetleri ve Windows için olay izleme](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md) ve [Olay Görüntüleyicisi'ni](http://go.microsoft.com/fwlink/?LinkId=165428).  
  
-   **Perfmon** – performans sayaçları İzleyicisi izleme sayaçları ve izleme etkilerini kullanan Windows grafik yönetim aracıdır. Daha fazla bilgi için bkz: [bir veri toplayıcı kümesi el ile oluşturmanız](http://go.microsoft.com/fwlink/?LinkId=165429).  
  
### <a name="keywords"></a>Anahtar Sözcükler  
 Kullanırken <xref:System.ServiceModel.Activation.Configuration.ServiceModelActivationSectionGroup.Diagnostics%2A> sınıfı, .NET Framework izleme iletilerini önem düzeyi (örneğin, hata, uyarı ve bilgi) genellikle filtrelenir. ETW önem düzeyi kavramını destekler, ancak anahtar sözcüklerini kullanarak bir yeni, esnek filtre mekanizması sunar. Anahtar sözcükler olay ne anlama geldiği hakkında ek bağlam sağlamak izleme olaylarını olanak tanıyan rastgele metinsel değerlerdir.  
  
 WCF analiz izleme her izleme olayı anahtar sözcükleri iki tür vardır. İlk olarak, her olay bir veya daha fazla senaryo anahtar vardır. Bu anahtar sözcükler senaryoları belirtmek, bu olay desteklemek üzere tasarlanmıştır. Üç senaryo anahtar sözcükler, her aşağıdaki tabloda gösterildiği gibi belirli bir amaç için tasarlanmıştır. Anahtar sözcükler kullanarak filtreleme WCF Hizmeti etkilemeden dinamik olarak değiştirilebilir. Dinamik olarak geçerli izleme senaryonuza ve izleme bilgi toplamanız miktarını değiştirebilirsiniz, anlamına gelir. Örneğin, değiştirebileceğiniz `HealthMonitoring` için `Troubleshooting` ve olay izleme ayrıntı düzeyi artar.  
  
|Anahtar sözcüğü|Açıklama|  
|-------------|-----------------|  
|`HealthMonitoring`|Çok basit, en az, izleme hizmetinizin etkinlikleri izlemenize olanak sağlar.|  
|`EndToEndMonitoring`|İleti akışı izlemeyi desteklemek için kullanılan olayları.|  
|`Troubleshooting`|Daha ayrıntılı olaylar WCF genişletilebilirlik noktaları etrafında.|  
  
 Anahtar sözcükler ikinci grup tanımlayın hangi bileşeninin [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] olay yayılan.  
  
|Anahtar sözcüğü|Açıklama|  
|-------------|-----------------|  
|`UserEvents`|Kullanıcı kodu tarafından gösterilen olayları ve [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].|  
|`ServiceModel`|WCF çalışma zamanı tarafından oluşturulan olaylar.|  
|`ServiceHost`|Hizmet ana bilgisayar tarafından oluşturulan olaylar.|  
|`WCFMessageLogging`|WCF ileti günlüğe kaydetme olaylar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Hizmetleri ve Windows için Olay İzleme](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)
