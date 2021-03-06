---
title: Güvenlik Etkinliklerini Denetleme
ms.date: 03/30/2017
helpviewer_keywords:
- auditing security events [WCF]
ms.assetid: 5633f61c-a3c9-40dd-8070-1c373b66a716
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: e4219553f97f272577e8efdeb106b43e5f76ee59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="auditing-security-events"></a>Güvenlik Etkinliklerini Denetleme
Windows Communication Foundation (WCF) ile oluşturulan uygulamaların (başarı, hata veya her ikisi de) güvenlik olaylarını denetleme özelliği ile oturum açabilir. Olaylar için Windows sistem olay günlüğüne yazılır ve Olay Görüntüleyicisi'ni kullanarak incelenebilir.  
  
 Denetim bir yöneticinin zaten oluştu veya devam ediyor saldırının algılamak bir yol sağlar. Buna ek olarak, Denetim güvenlikle ilgili sorunların hatalarını ayıklamak için bir geliştirici yardımcı olabilir. Örneğin, yetkilendirme veya denetimi İlkesi yapılandırmasında bir hata için yetkili bir kullanıcı yanlışlıkla erişimini engellediği, bir geliştirici hızlı bir şekilde bulmak ve olay günlüğünü inceleyerek bu hatanın nedenini ortadan kaldırmak.  
  
 WCF güvenlik hakkında daha fazla bilgi için bkz: [güvenliğine genel bakış](../../../../docs/framework/wcf/feature-details/security-overview.md). Programlama WCF hakkında daha fazla bilgi için bkz: [temel WCF programlama](../../../../docs/framework/wcf/basic-wcf-programming.md).  
  
## <a name="audit-level-and-behavior"></a>Denetim düzeyi ve davranışı  
 İki düzeyde güvenlik denetimleri mevcuttur:  
  
-   Çağıran yetkili hizmet kimlik doğrulama düzeyi.  
  
-   İleti düzeyi, WCF ileti geçerliliğini denetler ve arayanın kimliğini doğrular.  
  
 Her ikisi de denetim başarılı veya başarısız olarak bilinen düzeyleri denetleyebilirsiniz *denetleme davranışı*.  
  
## <a name="audit-log-location"></a>Denetim günlüğü konumu  
 Bir denetim düzeyi ve davranış belirledikten sonra siz (veya yönetici) denetim günlüğü için bir konum belirtebilirsiniz. Üç Seçenekler şunlardır: varsayılan, uygulama ve güvenlik. Varsayılan belirttiğinizde, sistem güvenlik günlüğüne yazma destekleyip desteklemediğini ve hangi sistemde kullandığınız gerçek günlük bağlıdır. Daha fazla bilgi için bu konunun devamındaki "İşletim sistemi" bölümüne bakın.  
  
 Güvenlik günlüğü'ne yazmaya gerektirir `SeAuditPrivilege`. Varsayılan olarak, yalnızca yerel sistem ve ağ hizmet hesaplarını bu ayrıcalığına sahip. Güvenlik günlüğü işlevlerini yönetmek için `read` ve `delete` gerektirir `SeSecurityPrivilege`. Varsayılan olarak, yalnızca Yöneticiler bu ayrıcalığına sahip.  
  
 Buna karşılık, kimliği doğrulanmış kullanıcılara Okuma ve uygulama günlüğüne yazma. [!INCLUDE[wxp](../../../../includes/wxp-md.md)] varsayılan denetim olayları uygulama günlüğüne yazar. Günlük, tüm kimliği doğrulanmış kullanıcılar tarafından görülemez kişisel bilgilerini de içerebilir.  
  
## <a name="suppressing-audit-failures"></a>Denetim hataları gizleme  
 Denetim sırasında başka hiçbir denetim hatası engellenip engellenmeyeceğini seçenektir. Varsayılan olarak, bir uygulama bir denetim hatası etkilemez. Gerekirse, ancak seçeneği ayarlayabileceğiniz `false`, bir özel durum oluşturulmasına neden olur.  
  
## <a name="programming-auditing"></a>Programlama denetleme  
 Program aracılığıyla veya yapılandırma yoluyla denetim davranış belirtebilirsiniz.  
  
### <a name="auditing-classes"></a>Denetim sınıfları  
 Aşağıdaki tabloda, sınıflar ve denetim davranışı programlamak için kullanılan özellikleri açıklar.  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>|Ayar hizmet davranışını denetlemek için seçenekleri sağlar.|  
|<xref:System.ServiceModel.AuditLogLocation>|Hangi yazmak için oturum belirtmek için numaralandırması. Olası değerler şunlardır: varsayılan, uygulama ve güvenlik. Varsayılan seçtiğinizde, işletim sistemi gerçek günlük konumunu belirler. Bu konunun devamındaki "Uygulama veya güvenlik olay günlüğü seçim" bölümüne bakın.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A>|İleti kimlik doğrulama olayları hangi tür ileti düzeyinde denetleneceğini belirtir. Seçimleri `None`, `Failure`, `Success`, ve `SuccessOrFailure`.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A>|Hangi tür hizmeti yetkilendirme olayları hizmet düzeyinde denetleneceğini belirtir. Seçimleri `None`, `Failure`, `Success`, ve `SuccessOrFailure`.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A>|İstemci isteği başarısız denetlerken olacağını belirtir. Örneğin, ne zaman hizmeti güvenlik günlüğüne yazma girişiminde, ancak sahip olmadığı `SeAuditPrivilege`. Varsayılan değer olan `true` hataları dikkate alınmaz ve istemci isteği normalde işlendiğini gösterir.|  
  
 Bir uygulama denetim olaylarını günlüğe kaydedecek şekilde ayarlama örneği için bkz: [nasıl yapılır: güvenlik olaylarını denetleme](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).  
  
### <a name="configuration"></a>Yapılandırma  
 Yapılandırması ekleyerek Denetim davranışını belirtmek için de kullanabilirsiniz bir [ \<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) altında [ \<davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md). Öğesinin altında eklemelisiniz bir [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) aşağıdaki kodda gösterildiği gibi.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <behavior>  
        <!— auditLogLocation="Application" or "Security" -—>  
        <serviceSecurityAudit  
                  auditLogLocation="Application"  
                  suppressAuditFailure="true"  
                  serviceAuthorizationAuditLevel="Failure"  
                  messageAuthenticationAuditLevel="SuccessOrFailure" />   
      </behavior>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 Denetim etkin olduğunda ve bir `auditLogLocation` değil belirtilmezse, varsayılan günlük güvenlik günlüğüne yazma destekleyen bir platform için "Güvenlik" günlük adıdır; Aksi takdirde, "Uygulama" günlüğü olur. Yalnızca [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wv](../../../../includes/wv-md.md)] işletim sistemleri için destek güvenlik günlüğüne yazma. Daha fazla bilgi için bu konunun devamındaki "İşletim sistemi" bölümüne bakın.  
  
## <a name="security-considerations"></a>Güvenlik Değerlendirmeleri  
 Kötü niyetli bir kullanıcı denetiminin etkin olduğunu biliyorsa, bu saldırgan denetim girişlerini yazılmasına neden geçersiz iletileri gönderebilir. Bu şekilde denetim günlüğü dolu denetim sistemi başarısız olur. Bu durumu iyileştirmek için ayarlanmış <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> özelliğine `true` ve Denetim davranışını denetlemek için Olay Görüntüleyicisi'ni özelliklerini kullanın. Görüntüleme ve Windows XP'de adresinde Olay Görüntüleyicisi'ni kullanarak olay günlüklerini yönetme hakkında daha fazla bilgi için Microsoft Support makalesini bkz [görüntülemek ve Windows XP'de Olay Görüntüleyicisi'nde olay günlüklerini yönetmek nasıl](http://go.microsoft.com/fwlink/?LinkId=89150).  
  
 Üzerinde uygulama günlüğüne yazılan olaylarını denetleme [!INCLUDE[wxp](../../../../includes/wxp-md.md)] tüm kimliği doğrulanmış kullanıcılar tarafından görülebilir.  
  
## <a name="choosing-between-application-and-security-event-logs"></a>Uygulama ve güvenlik olay günlüklerini arasında seçim yapma  
 Aşağıdaki tablolar, uygulama veya güvenlik olay günlüğü oturum isteyip istemediğinizi seçin yardımcı olacak bilgiler sağlar.  
  
#### <a name="operating-system"></a>İşletim sistemi  
  
|Sistem|Uygulama günlüğü|Güvenlik günlüğü|  
|------------|---------------------|------------------|  
|[!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] veya üzeri|Desteklenir|Desteklenmez|  
|[!INCLUDE[ws2003sp1](../../../../includes/ws2003sp1-md.md)] Ve [!INCLUDE[wv](../../../../includes/wv-md.md)]|Desteklenir|İş parçacığı içeriği sahip olması gerekir `SeAuditPrivilege`|  
  
#### <a name="other-factors"></a>Diğer etkenlere bağlı  
 İşletim sistemi ek olarak, aşağıdaki tabloda günlük kaydını etkinleştirme denetleyen diğer ayarların açıklar.  
  
|Faktörü|Uygulama günlüğü|Güvenlik günlüğü|  
|------------|---------------------|------------------|  
|Denetim İlkesi Yönetimi|Yok.|Yapılandırma ile birlikte güvenlik günlüğünü de yerel güvenlik yetkilisi (LSA) ilkesi tarafından kontrol edilir. "Nesne erişimini denetle" kategorisi de etkinleştirilmesi gerekir.|  
|Varsayılan kullanıcı deneyimi|Hiçbir ek açıklama adım uygulama işlemleri için gerektiği şekilde tüm kimliği doğrulanmış kullanıcılar uygulama günlüğüne yazabilirsiniz.|Uygulama işlem (içerik) sahip olmalıdır `SeAuditPrivilege`.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>  
 <xref:System.ServiceModel.AuditLogLocation>  
 [Güvenliğe Genel Bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Temel WCF Programlama](../../../../docs/framework/wcf/basic-wcf-programming.md)  
 [Nasıl yapılır: Güvenlik Olaylarını Denetleme](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)  
 [\<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md)  
 [\<davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
 [Windows Server App Fabric için güvenlik modeli](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
