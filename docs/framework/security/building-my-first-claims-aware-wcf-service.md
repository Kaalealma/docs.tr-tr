---
title: My ilk talep kullanan WCF hizmeti oluşturma
ms.date: 03/30/2017
ms.assetid: e0e6d091-9a97-4888-8f2c-cbcee42d90ee
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 3b88835cc7836d9d6c323de3c0386b3f4c7c3078
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="building-my-first-claims-aware-wcf-service"></a>My ilk talep kullanan WCF hizmeti oluşturma
## <a name="applies-to"></a>Uygulandığı öğe:  
  
-   Windows Identity Foundation (WIF)  
  
-   Windows Communication Foundation (WCF)  
  
## <a name="overview"></a>Genel Bakış  
 Bu konuda, WIF kullanarak talep kullanan WCF hizmetleri oluşturma senaryosu açıklanmaktadır. Talep kullanan web hizmeti senaryosunda genellikle üç katılımcı vardır: web hizmetinin kendisi, son kullanıcı ve Güvenlik Belirteci Hizmeti (STS). Aşağıdaki şekilde bu senaryo anlatılmaktadır:  
  
 ![WIF Basic talep kullanan WCF Hizmeti](../../../docs/framework/security/media/wifbasicclaimsawarewcfservice.gif "WIFBasicClaimsAwareWCFService")  
  
1.  WCF hizmeti istemcisi (bazen aracı olarak adlandırılır), STS'ye kimlik bilgilerini göndermek için WIF'yi kullanır ve başarılı bir kimlik doğrulamadan sonra aracıya STS tarafından bir belirteç verilir.  
  
2.  Aracı, bu STS tarafından verilen belirteci WCF hizmetine gönderir.  
  
3.  Talep kullanan WCF hizmeti, STS'ye ve verdiği belirteçlere güvenecek şekilde yapılandırılmıştır. Talep kullanan WCF hizmeti, belirteci uygulamak ve ayrıştırmak için WIF kullanır. Geliştiriciler kullanın uygun WIF API ve türler, örneğin, **ClaimsPrincipal** yetkilendirme için bu uygulama gibi uygulamanın gerekir.  
  
 .NET 4. 5 ' başlayarak, WIF .NET Framework paketi parçasıdır. Framework'te doğrudan kullanılabilen WIF sınıfları çok derin tümleştirme talep tabanlı kimlik talepleri kullanan kolaylaştırma .NET içinde sağlar. WIF 4.5 ile, talep kullanan web uygulamaları geliştirmeye başlamak için bant dışı bileşenler yüklemenize gerek yoktur. WIF sınıfları artık çeşitli derlemeler arasında yayılmaktadır. Temel sınıflar System.Security.Claims, System.IdentityModel ve System.IdentityModel.Services'dır.  
  
 STS, başarılı kimlik doğrulamadan sonra belirteçler veren bir hizmettir. Microsoft, iki sektör standardı STS sunar:  
  
-   [Active Directory Federasyon Hizmetleri (AD FS) 2.0](http://go.microsoft.com/fwlink/?LinkID=247516) ()http://go.microsoft.com/fwlink/?LinkID=247516)  
  
-   [Windows Azure erişim denetimi hizmeti (ACS)](http://go.microsoft.com/fwlink/?LinkID=247517) (http://go.microsoft.com/fwlink/?LinkID=247517).  
  
 AD FS 2.0, Windows Server R2'nin bir parçasıdır ve şirket içi senaryolar için STS olarak kullanılabilir. Azure Active Directory erişim denetimi (erişim denetimi hizmeti veya ACS olarak da bilinir), Microsoft Azure bir parçası olarak sunulan bulut hizmetidir. Test ve eğitim amaçları için talep kullanan uygulamalar oluşturmak üzere başka STS'ler de kullanabilirsiniz. Örneğin, bir parçası olan yerel geliştirme STS kullanabilirsiniz [kimlik ve erişim aracı Visual Studio için](http://go.microsoft.com/fwlink/?LinkID=245849) (http://go.microsoft.com/fwlink/?LinkID=245849) olduğu ücretsiz çevrimiçi.  
  
 WIF kullanan, ilk talep kullanan WCF hizmeti oluşturmak için bkz: [nasıl yapılır: bir WCF Web hizmeti uygulama için etkinleştir WIF](../../../docs/framework/security/how-to-enable-wif-for-a-wcf-web-service-application.md).
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WIF Kullanmaya Başlama](../../../docs/framework/security/getting-started-with-wif.md)
