---
title: İstemci Uygulama Hizmetleri
ms.date: 03/30/2017
helpviewer_keywords:
- role-based security [.NET Framework], client application services
- client application services
- credentials [.NET Framework]
- Windows-based applications, client application services
- application settings, client application services
- profiles [ASP.NET], client application services
- logins [client application services]
- sharing information and functionality [client application services]
- Web settings [client application services]
- authentication [ASP.NET], client application services
- ASP.NET services, client application services
- client applications, ASP.NET services
- roles [.NET Framework], client application services
- client application services, about client application services
ms.assetid: 1487d8df-089e-4f21-abfb-a791a652b58e
ms.openlocfilehash: d67b7467bdacdfca054d0ecd11a81c7d25b158f7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="client-application-services"></a>İstemci Uygulama Hizmetleri
İstemci uygulama hizmetleri kullanan Windows tabanlı uygulamalar oluşturmanızı kolaylaştırır [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] oturum açma, roller ve Microsoft ASP.NET 2.0 AJAX uzantılarında dahil profili uygulama hizmetleri. Bu hizmetler, birden çok Web ve Windows tabanlı uygulamalar kullanıcı bilgileri ve kullanıcı yönetimi işlevleri tek bir sunucudan paylaşmak için etkinleştirin. Örneğin, aşağıdaki görevleri gerçekleştirmek için bu hizmetleri kullanabilirsiniz:  
  
-   Bir kullanıcı kimlik doğrulaması. Kimlik doğrulama hizmeti, bir kullanıcının kimliğini doğrulamak için kullanabilirsiniz.  
  
-   Rol veya kimliği doğrulanmış bir kullanıcı rolleri belirleyin. Rol hizmeti, kullanıcı rolüne bağlı olarak, uygulamanızın kullanıcı arabirimi değiştirmek için kullanabilirsiniz. Örneğin, bir yönetici rolü olan kullanıcılar için ek özellikler sağlar.  
  
-   Sunucuda bulunan depolama ve erişim kullanıcı başına uygulama ayarları. Ayarları birden çok uygulama ve konumları arasında paylaşmak için Web ayarları hizmeti (Profil Hizmeti olarak da bilinir) kullanabilirsiniz.  
  
 İstemci uygulama hizmetleri, uygulama yapılandırma dosyaları belirtebilirsiniz istemci hizmet sağlayıcıları üzerinden Web Hizmetleri genişletilebilirlik modeli yararlanın. Bu hizmet sağlayıcıları bir ağ bağlantısı kullanılabilir olmadığında kimlik doğrulama, rolleri ve ayar verileri için yerel önbelleği kullanan çevrimdışı işlevleri içerir.  
  
 Hakkında daha fazla bilgi için [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] uygulama bkz [ASP.NET uygulama hizmetleri genel bakış](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [İstemci Uygulama Servislerine Genel Bakış](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 İstemci uygulama hizmet sağlayıcıları kullanılabilen özellikleri açıklar.  
  
 [Nasıl Yapılır: İstemci Uygulama Servislerini Yapılandırma](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 Etkinleştirmek için Visual Studio Proje Tasarımcısı ve yapılandırma uygulama hizmetleri nasıl kullanılacağını açıklar. Ayrıca, App.config dosyasına karşılık gelen değişiklikleri açıklar.  
  
 [Nasıl Yapılır: İstemci Uygulama Servisleri ile Kullanıcı Oturum Açma Adını Uygulama](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md)  
 Uygulamanızı bir istemci kimlik doğrulama hizmeti sağlayıcısı kullanacak şekilde yapılandırıldığında, bir kullanıcıyı doğrulamak açıklar.  
  
 [İzlenecek Yol: İstemci Uygulama Servislerini Kullanma](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 Tek bir uygulama içinde tüm istemci uygulama hizmetleri özellikleri birleştirmek açıklar. Bu kılavuz, uçtan uca yönergeler sağlar. Örneğin, istemci uygulama hizmetleri test etmek için kullanabileceğiniz bir ASP.NET Web hizmeti uygulama oluşturmak yönergeler içerir.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Web.ClientServices.ClientFormsIdentity>  
 <xref:System.Web.ClientServices.ClientRolePrincipal>  
 <xref:System.Web.ClientServices.ConnectivityStatus>  
 <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials>  
 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider>  
 <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider>  
 <xref:System.Web.ClientServices.Providers.ClientWindowsAuthenticationMembershipProvider>  
 <xref:System.Web.ClientServices.Providers.ClientRoleProvider>  
 <xref:System.Web.ClientServices.Providers.ClientSettingsProvider>  
 <xref:System.Web.ClientServices.Providers.SettingsSavedEventArgs>  
 <xref:System.Web.ClientServices.Providers.UserValidatedEventArgs>  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ASP.NET uygulama hizmetleri genel bakış](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013)  
 [Microsoft Ajax ile form kimlik doğrulaması kullanma](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)  
 [Microsoft Ajax ile rolleri bilgileri kullanarak](http://msdn.microsoft.com/library/280f6ad9-ba1a-4fc9-b0cc-22e39e54a82d)  
 [Microsoft Ajax ile profil bilgilerini kullanma](http://msdn.microsoft.com/library/91239ae6-d01c-4f4e-a433-eb9040dbed61)  
 [ASP.NET kimlik doğrulaması](http://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1)  
 [Yetkilendirme rollerini kullanarak yönetme](http://msdn.microsoft.com/library/01954ce4-39a2-487f-8153-a69f6f6f3195)    
 [Uygulama Ayarlarına Genel Bakış](../../../docs/framework/winforms/advanced/application-settings-overview.md)
