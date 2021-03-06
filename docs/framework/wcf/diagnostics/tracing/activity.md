---
title: Etkinlik
ms.date: 03/30/2017
ms.assetid: 70471705-f55f-4da1-919f-4b580f172665
ms.openlocfilehash: 3100d5bb60dc1b11d23b0705f4d6f23a3675ac51
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="activity"></a>Etkinlik
Bu konu Windows Communication Foundation (WCF) izleme modelindeki etkinlik izlemeleri açıklar. Etkinlikler hata kapsamını daraltmak kullanıcı Yardımı birimleri işliyor. Aynı etkinlik içindeki oluşan hataları doğrudan ilişkilidir. Örneğin, ileti şifre çözme başarısız olduğundan bir işlem başarısız olur. Şifre çözme hatası ve istek hatası arasında doğrudan bağıntı gösteren aynı etkinliğinde izlemeleri hem işlem hem de ileti şifre çözme hatası görünür.  
  
## <a name="configuring-activity-tracing"></a>Etkinlik izlemeyi yapılandırma  
 WCF uygulamaları işlemek için önceden tanımlanmış etkinlikleri sağlar (bkz [etkinlik listesi](../../../../../docs/framework/wcf/diagnostics/tracing/activity-list.md)). Etkinlikler de program aracılığıyla ve grup kullanıcı izlemeleri tanımlayabilirsiniz. Daha fazla bilgi için bkz: [kullanıcı kodu izleri yayma](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md).  
  
 Çalışma zamanında etkinlik izlemeleri yaymak üzere kullanmak `ActivityTracing` ayarını `System.ServiceModel` izleme kaynağı veya diğer WCF veya özel izleme kaynakları, aşağıdaki yapılandırma kodda gösterildiği gibi.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
 Yapılandırma öğesi ve kullanılan öznitelikleri hakkında daha fazla bilgi için bkz: [yapılandırma izleme](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) konu.  
  
## <a name="viewing-activities"></a>Etkinlikleri görüntüleme  
 Etkinlikler ve bunların yardımcı programı görüntüleyebilirsiniz [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). ActivityTracing etkinleştirildiğinde, bu aracı izlemeleri alır ve etkinliği tabanlı sıralar. İzleme aktarımları da görebilirsiniz. Bir izleme aktarımı nasıl farklı etkinlikleri gösterir birbirleriyle ilişkilidir. Belirli bir etkinliği başlatmak başka bir nedeni görebilirsiniz. Örneğin, bir güvenli konuşma belirtecini almak için güvenlik el sıkışması iletisi İsteği başlatıldı.  
  
### <a name="correlating-activities-in-service-trace-viewer"></a>Hizmet izleme görüntüleyicisini aktivitelerde ilişkilendirme  
 Hizmet izleme Görüntüleyicisi aracı etkinliklerin iki görünümleri sağlar:  
  
-   **Liste** görünümü, burada etkinlik kimliği izlemeleri süreçler arasında doğrudan ilişkilendirmek için kullanılır. İzlemeler farklı işlemler, örneğin, istemci ve hizmet, ancak aynı etkinlik kimliği ile aynı etkinlik içindeki gruplandırılır. Bu nedenle, istemcide bir hataya neden olur hizmetine oluşan bir hata her ikisi de aynı aracı etkinlik görünümünde gösterilir.  
  
-   **Grafik** burada etkinlikleri gruplandırılır işlemler tarafından görünümü. Bu görünümde, bir istemci ve hizmet aynı etkinlik Kimliğine sahip farklı etkinlikler kendi izlemeleri sahip. Etkinlikler farklı işlemler aynı etkinlik kimliği ile ilişkilendirmek için aracı ileti akışları ilgili etkinliklerinde gösterir.  
  
 Daha fazla bilgi için ve hizmet izleme Görüntüleyicisi aracı grafik bir görünümünü görmek için bkz: [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) ve [bağıntılı izlemeleri görüntüleme için hizmet izleme görüntüleyicisini kullanma ve Sorun giderme](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
## <a name="defining-the-scope-of-an-activity"></a>Bir etkinlik kapsamını tanımlama  
 Bir etkinlik tasarım zamanında tanımlanır ve iş mantıksal birimini temsil eder. Aynı etkinlik tanımlayıcıyla verilmiş izlemeleri doğrudan ilgili, aynı etkinlik parçasıdır. Etkinlik bitiş noktası sınırları (bir istek) aşabileceğinden iki kapsamları bir etkinlik için tanımlanır.  
  
-   `Global` uygulama başına kapsamı. Bu kapsamda etkinlik 128-bit genel benzersiz etkinlik tanımlayıcısıyla, gAId tanımlanır. GAid ne uç noktalar arasında yayılır ' dir.  
  
-   `Local` uç nokta başına kapsamı. Bu kapsamda etkinliğin etkinlik izlemeleri ve işlem kimliği yayma izleme kaynağı adı yanı sıra kendi gAId tarafından tanımlanır Bu Üçlü yerleştirilmiş yerel etkinlik kimliği oluşturur. Yerleştirilmiş bir etkinlik (yerel) sınırlarını tanımlamak için kullanılır.  
  
## <a name="trace-schema"></a>Şema izleme  
 İzlemeler gösterilen herhangi bir şema kullanarak ve Microsoft platformlarda. "e2e" ("uçtan uca" için) yaygın olarak kullanılan bir şema ' dir. Bu şemayı 128 bit tanımlayıcısı (gAId), izleme kaynak adı ve işlem kimliğini içerir Yönetilen kodda <xref:System.Diagnostics.XmlWriterTraceListener> E2E şemasında izlemeleri yayar.  
  
 Geliştiriciler, bir izleme ile ayarlayarak yayılan yardımcı ayarlayabilirsiniz <xref:System.Diagnostics.CorrelationManager.ActivityId%2A> özelliği ile bir GUID üzerinde iş parçacığı yerel depolaması (TLS). Aşağıdaki örnekte bu gösterir.  
  
```  
// set the current Activity ID to a new GUID.  
CorrelationManager.ActivityId = Guid.NewGuid();  
```  
  
 İzlemeler izleme kaynağını kullanarak aşağıdaki örnekte gösterildiği gibi gösterilen sırada gAId TLS ayarı korumalı olacaktır.  
  
```  
TraceSource traceSource = new TraceSource("myTraceSource");  
traceSource.TraceEvent(TraceEventType.Warning, eventId, "Information");  
```  
  
 Gösterilen izlemede TLS, izleme kaynağının oluşturucusu ve geçerli işlemin kimliği için bir parametre olarak geçirilen izleme kaynağı adı, şu anda gAId bulunmaz.  
  
## <a name="activity-lifetime"></a>Etkinlik yaşam süresi  
 Sıkı bağlamında ilk kez etkinlik kimliği verilmiş izlemede kullanılır ve verilmiş İzlemede kullanılan son zamanı sona erer etkinliğin kanıt başlatır. Önceden tanımlanmış bir izleme türleri kümesini tarafından sağlanan <xref:System.Diagnostics>başlatma ve durdurma, etkinlik ömrü sınırları açıkça işaretlenecek dahil olmak üzere.  
  
-   Başlangıç: bir etkinlik başlangıcını gösterir. "Başlat" izleme yeni bir işleme kilometre taşı başlayan kaydını sağlar. Etkinlik Kimliği uç noktalar arasında ne zaman dağıtılacağını dışında belirli bir işlemde belirtilen izleme kaynağı için yeni bir etkinlik kimliği içerir, bu durumda biz bir "Başlat" uç nokta bakın. Yeni bir etkinlik başlangıç örnekleri işleme veya yeni bir genel yöntem girmek için yeni bir iş parçacığı oluşturma içerir.  
  
-   STOP: Etkinliğin sonunu gösterir. "Durdur" izleme varolan bir işleme kilometre taşı bitiş kaydını sağlar. Etkinlik Kimliği uç noktalar arasında ne zaman dağıtılacağını dışında belirli bir işlemde belirtilen izleme kaynağı için varolan bir etkinlik kimliği içerir, bu durumda biz bir "durak" uç nokta bakın.  İşlem iş parçacığı sonlandırma veya olan başına "Başlat" izleme ile belirtilen bir yönteminden çıkılıyor aktivite durdurulduğu örnek olarak verilebilir.  
  
-   Askıya alma: bir etkinlik işlenmesini ertelenmesi gösterir. "Askıda" izleme, işlem daha sonra devam etmek için beklenen var olan bir etkinlik kimliği içerir. Hiçbir izlemeler, geçerli izleme kaynağından askıya alma ve sürdürme olaylar arasındaki bu kimlikle yayılan. Bir etkinlik bir dış kitaplık işlevdeki çağrılırken ya da bir g/ç tamamlama bağlantı noktasını gibi bir kaynakta beklenirken duraklatma örnekler.  
  
-   RESUME: bir etkinlik işlenmesi sürdürme gösterir. "Sürdür" izleme "Askıda" izleme geçerli izleme kaynağı olan son verilmiş izlemesinde olduğu var olan bir etkinlik kimliği içerir. Dış kitaplık işlevi ya da bir g/ç tamamlama bağlantı noktasını gibi bir kaynak tarafından işlemi sürdürme işareti bir çağrısından döndürme örnekler.  
  
-   Aktarım: Bazı etkinlikler başkaları tarafından neden olduğu veya başkalarına ilişkilendirmek için etkinlikler "Transfer" izlemeleri diğer etkinlikleri ile ilgili olabilir. Başka bir etkinlik yönlendirilmiş ilişki bir aktarımı kaydeder  
  
 Başlat ve Durdur izlemeleri için bağıntı kritik değildir. Ancak, bunlar performans, profil oluşturma ve etkinlik kapsam doğrulama artırmasına yardımcı olabilir.  
  
 Bu tür kullanarak, Araçlar aynı etkinliğin hemen ilgili olayları bulmak için izleme günlükleri gezinme en iyi duruma getirebilirsiniz veya aracı aktarımı izlemeleri izliyorsa ilişkili olayları etkinlikler. Örneğin, belirli bir etkinlik için günlüklerini İzlemeyi Başlat/Durdur gördüğünüzde ayrıştırma araçları durdurur.  
  
 Bu izleme türleri profil oluşturma için de kullanılabilir. Başlatma ve durdurma işaretlerinin arasında tüketilen kaynaklarının içerdiği mantıksal etkinlikler dahil olmak üzere etkinliğe ilişkin dahil zamanı temsil eder. Askıya alma ve sürdürme izlemeleri arasındaki zaman aralığı çıkarılmasıyla gerçek etkinlik zamanı sağlar.  
  
 İzlemeyi Durdur da uygulanan etkinlikleri kapsamını doğrulamak için özellikle yararlıdır. İzlemeyi Durdur yerine belirli bir etkinlik içinde sonra bazı işleme izlemeleri görünüyorsa, bu kod hatası önerir.  
  
## <a name="guidelines-for-using-activity-tracing"></a>Etkinlik izleme kullanma için yönergeler  
 ActivityTracing izlemeleri (Başlat, Durdur, askıya alma, sürdürme ve aktarım) kullanarak bir kılavuz verilmiştir.  
  
-   İzleme yönlendirilmiş döngüsel bir grafik olan bir ağaç ' dir. Denetim bir etkinlik kökenli bir etkinliğe geri dönebilirsiniz.  
  
-   Bir etkinlik sisteminin ya da desteklenebilirlik yönetici anlamlı olabilen bir işleme sınırını gösterir.  
  
-   Her WCF yöntemi, istemci ve sunucu üzerinde yeni bir etkinlik başlayarak, sonra bir (İş tamamlandıktan sonra) sınırlıdır yeni etkinlik bitiş ve ortam etkinlik döndürüyor.  
  
-   Bağlantıları dinlemeyi veya iletileri için bekleyen gibi uzun (sürekli) çalıştıran etkinlikler tarafından karşılık gelen Başlat/Durdur işaretleyicileri gösterilir.  
  
-   Etkinlikler alınmasını tarafından tetiklenen veya bir ileti işlenmesini izleme sınırları tarafından temsil edilen.  
  
-   Etkinlikler etkinlikleri, mutlaka nesneleri gösterir. Bir etkinlik olarak yorumlanıp "Bu gerçekleştiği zaman. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır. (anlamlı izleme çıkması oluşan)."  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlemeyi Yapılandırma](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [Uçtan Uca İzleme Senaryoları](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)  
 [Kullanıcı Kodu İzlemeleri Yayma](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md)
