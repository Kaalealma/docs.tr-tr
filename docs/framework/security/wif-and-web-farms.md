---
title: WIF ve Web grupları
ms.date: 03/30/2017
ms.assetid: fc3cd7fa-2b45-4614-a44f-8fa9b9d15284
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ed6a7fbe550dad85cf505eaf20a446803b84c96f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="wif-and-web-farms"></a>WIF ve Web grupları
Bir web grubu içinde dağıtılan bir bağlı olan taraf (RP) uygulama kaynaklarını güvenli hale getirmek için Windows Identity Foundation (WIF) kullandığınızda, WIF farklı çalıştırma RP uygulamasının örneklerini belirteçlerinden işleyebilir emin olmak için belirli adımlar uygulamanız gerekir gruptaki bilgisayarların. Bu işlem şifreleme Oturum belirteci imzaları doğrulamak içerir ve oturum belirteç şifre çözme, oturum belirteçleri önbelleğe alma ve algılama güvenlik belirteçleri yeniden.  
  
 RP tek bir bilgisayara veya bir web grubundaki--çalışıp çalışmadığını WIF RP uygulamanın – kaynakları güvenli hale getirmek için kullanılırken tipik bir durumunda güvenlik belirteci hizmeti (STS) edinilen güvenlik belirtecine göre istemci ile bir oturum oluşturulur. Bu WIF kullanarak güvenliği her uygulama kaynağı STS doğrulamasında zorunda istemciye zorlama önlemek için yapılır. WIF oturumları nasıl işlediği hakkında daha fazla bilgi için bkz: [WIF oturum yönetimi](../../../docs/framework/security/wif-session-management.md).  
  
 Varsayılan ayarlar kullanıldığında, WIF şunları yapar:  
  
-   Bir örneğini kullanan <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> Oturum belirteci okumasına ve yazmasına sınıfı (örneği <xref:System.IdentityModel.Tokens.SessionSecurityToken> sınıfı) talepler ve kimlik doğrulaması için kullanılan güvenlik belirteci hakkında diğer bilgi bilgilerinin yanı sıra oturum izleme kendisi. Oturum belirteci paketlenmiş ve oturum tanımlama bilgisinde depolanır. Varsayılan olarak, <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> kullanan <xref:System.IdentityModel.ProtectedDataCookieTransform> Oturum belirteci korumak için veri koruma API'si (DPAPI) kullanır, sınıf. DPAPI kullanıcı veya makine kimlik bilgilerini kullanarak koruma sağlar ve kullanıcı profilinde anahtar verilerini depolar.  
  
-   Varsayılan, bellek içi uyarlamasını kullandığı <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> depolamak ve oturum belirteci işlemek için sınıf.  
  
 Bu varsayılan ayarları tek bir bilgisayarda RP uygulamanın dağıtıldığı senaryolar çalışır; Ancak, bir web grubunda dağıtıldığında, her HTTP isteği gönderilen ve farklı bir bilgisayarda çalışan RP uygulama farklı bir örneğine tarafından işlenebilir. Belirteç koruma ve belirteç önbelleğe alma belirli bir bilgisayarda bağımlı olduğu için bu senaryoda, yukarıda açıklanan varsayılan WIF ayarları çalışmaz.  
  
 Bir web grubundaki RP uygulama dağıtmak için işleme oturumu belirteçlerin (yanı sıra yeniden yürütülmüş belirteçlerin) belirli bir bilgisayarda çalışan uygulama bağımlı değil emin olmalısınız. Yapmanın bir yolu, ASP.NET tarafından sağlanan işlevleri kullanmayacağından RP uygulamanızı uygulamak için budur `<machineKey>` yapılandırma öğesi ve oturum belirteçleri işlemek için Dağıtılmış önbelleğe alma sağlar ve belirteçlerin yeniden. `<machineKey>` Öğesi doğrulamak için şifrelemek ve web grubunda farklı bilgisayarlarda aynı anahtarlar belirtmenize olanak tanıyan bir yapılandırma dosyasına belirteçlerin şifresini çözmek için gereken anahtarını belirtmenize olanak sağlar. WIF sağlayan bir özel oturum belirteci işleyicisi <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>, korur belirteçleri belirtilen anahtarları kullanılarak `<machineKey>` öğesi. Bu strateji uygulamak için bu yönergeleri izleyin:  
  
-   ASP.NET kullanan `<machineKey>` gruptaki bilgisayarların genelinde kullanılan imzalama ve şifreleme anahtarlarını açıkça belirtmek için yapılandırma öğesi. Aşağıdaki XML belirtimi gösterir `<machineKey>` öğesinin altında `<system.web>` öğesi bir yapılandırma dosyası.  
  
    ```xml  
    <machineKey compatibilityMode="Framework45" decryptionKey="CC510D … 8925E6" validationKey="BEAC8 … 6A4B1DE" />  
    ```  
  
-   Kullanmak için uygulamayı yapılandırma <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> belirteci işleyicisi koleksiyon ekleyerek. Önce kaldırmalısınız <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> (veya herhangi bir işleyicisini türetilmiş <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> sınıfı) bu tür bir işleyici varsa, belirteci işleyicisi koleksiyondan. <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> Kullanan <xref:System.IdentityModel.Services.MachineKeyTransform> belirtilen şifreleme malzeme kullanarak oturum tanımlama bilgisi verileri korur sınıfı `<machineKey>` öğesi. Aşağıdaki XML nasıl ekleneceğini gösterir <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> belirteci işleyicisi koleksiyonuna.  
  
    ```xml  
    <securityTokenHandlers>  
      <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
      <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </securityTokenHandlers>  
    ```  
  
-   Öğesinden türetilen <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> ve uygulama dağıtılmış, diğer bir deyişle, RP çalıştırabilirsiniz gruptaki tüm bilgisayarların erişilebilir bir önbellek önbelleğe alma. RP belirterek, dağıtılmış önbellek kullanacak şekilde yapılandırma [ \<sessionSecurityTokenCache >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) yapılandırma dosyası öğesi. Geçersiz kılabilirsiniz <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A?displayProperty=nameWithType> alt öğelerinin uygulamak için türetilmiş sınıf yönteminde `<sessionSecurityTokenCache>` gerekli iseler öğesi.  
  
    ```xml  
    <caches>  
      <sessionSecurityTokenCache type="MyCacheLibrary.MySharedSessionSecurityTokenCache, MyCacheLibrary">  
        <!—optional child configuration elements, if implemented by the derived class -->  
      </sessionSecurityTokenCache>  
    </caches>  
    ```  
  
     Dağıtılmış önbelleğe alma uygulamak için bir yolu, özel önbelleğiniz için WCF ön uç sağlamaktır. Bir WCF hizmeti önbelleği uygulama hakkında daha fazla bilgi için bkz: [önbelleğe alma WCF Hizmeti](#BKMK_TheWCFCachingService). RP uygulamanın önbelleğe alma hizmetini çağırmak için kullanabileceği bir WCF istemcisi uygulama hakkında daha fazla bilgi için bkz: [önbelleğe alma WCF istemci](#BKMK_TheWCFClient).  
  
-   Uygulamanızı yeniden yürütülmüş belirteçleri algılarsa, benzer bir strateji belirteç yeniden yürütme önbelleği için türetme tarafından önbelleğe alma dağıtılmış izlemeniz gereken <xref:System.IdentityModel.Tokens.TokenReplayCache> ve hizmetinde önbelleğe alma, belirteç yeniden yürütme işaret [ \< tokenReplayCache >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) yapılandırma öğesi.  
  
> [!IMPORTANT]
>  Tüm örnek XML ve bu konudaki kod gelen alınır [ClaimsAwareWebFarm](http://go.microsoft.com/fwlink/?LinkID=248408) (http://go.microsoft.com/fwlink/?LinkID=248408) örnek.  
  
> [!IMPORTANT]
>  Bu konudaki örnekler olarak sağlanan-olduğunu ve üretim kodunda değişiklik yapmadan kullanılmak üzere tasarlanmamıştır.  
  
<a name="BKMK_TheWCFCachingService"></a>   
## <a name="the-wcf-caching-service"></a>Önbelleğe alma WCF Hizmeti  
 Aşağıdaki arabirimi WCF önbelleğe alma hizmeti ile iletişim kurmak için bağlı olan taraf uygulaması tarafından kullanılan WCF istemcisi arasındaki sözleşme tanımlar. Temelde yöntemleri gösteren <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> sınıf hizmet işlemleri olarak.  
  
```  
[ServiceContract()]  
public interface ISessionSecurityTokenCacheService  
{  
    [OperationContract]  
    void AddOrUpdate(string endpointId, string contextId, string keyGeneration, SessionSecurityToken value, DateTime expiryTime);  
  
    [OperationContract]  
    IEnumerable<SessionSecurityToken> GetAll(string endpointId, string contextId);  
  
    [OperationContract]  
    SessionSecurityToken Get(string endpointId, string contextId, string keyGeneration);  
  
    [OperationContract(Name = "RemoveAll")]  
    void RemoveAll(string endpointId, string contextId);  
  
    [OperationContract(Name = "RemoveAllByEndpointId")]  
    void RemoveAll(string endpointId);  
  
    [OperationContract]  
    void Remove(string endpointId, string contextId, string keyGeneration);  
}  
```  
  
 Aşağıdaki kod, hizmet önbelleğe alma WCF uygulaması gösterir. Bu örnekte, varsayılan olarak, bellek içi Oturum belirteci önbelleğini WIF tarafından uygulanan kullanılır. Alternatif olarak, bir veritabanıyla desteklenen sağlam bir önbellek uygulamanız. `ISessionSecurityTokenCacheService` Yukarıda gösterilen arabirimi tanımlar. Bu örnekte, tüm arabirimi uygulamak için gereken yöntemleri okumanızdır gösterilir.  
  
```  
using System;  
using System.Collections.Generic;  
using System.IdentityModel.Configuration;  
using System.IdentityModel.Tokens;  
using System.ServiceModel;  
using System.Xml;  
  
namespace WcfSessionSecurityTokenCacheService  
{  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
    public class SessionSecurityTokenCacheService : ISessionSecurityTokenCacheService  
    {  
        SessionSecurityTokenCache internalCache;  
  
        // sets the internal cache used by the service to the default WIF in-memory cache.  
        public SessionSecurityTokenCacheService()  
        {  
            internalCache = new IdentityModelCaches().SessionSecurityTokenCache;  
        }  
  
        ...  
  
        public SessionSecurityToken Get(string endpointId, string contextId, string keyGeneration)  
        {  
            // Delegates to the default, in-memory MruSessionSecurityTokenCache used by WIF  
            SessionSecurityToken token = internalCache.Get(new SessionSecurityTokenCacheKey(endpointId, GetContextId(contextId), GetKeyGeneration(keyGeneration)));  
            return token;  
        }  
  
        ...  
  
        private static UniqueId GetContextId(string contextIdString)  
        {  
            return contextIdString == null ? null : new UniqueId(contextIdString);  
        }  
  
        private static UniqueId GetKeyGeneration(string keyGenerationString)  
        {  
            return keyGenerationString == null ? null : new UniqueId(keyGenerationString);  
        }  
    }  
}  
```  
  
<a name="BKMK_TheWCFClient"></a>   
## <a name="the-wcf-caching-client"></a>Önbelleğe alma WCF istemcisi  
 Bu bölümde türetilen bir sınıfta gösterir <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> ve temsilciler önbelleğe alma hizmete çağırır. Bu sınıf üzerinden kullanılacak RP uygulamasını yapılandırma [ \<sessionSecurityTokenCache >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) olduğu gibi aşağıdaki XML öğesi  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
 Sınıf geçersiz kılmaları <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A> özel hizmet uç noktası almak için yöntemi `<cacheServiceAddress>` alt öğesi olan `<sessionSecurityTokenCache>` öğesi. Bu uç noktayı başlatmak için kullandığı bir `ISessionSecurityTokenCacheService` kanal üzerinden, iletişim hizmeti ile.  Bu örnekte, tüm yöntemleri uygulamak için gereken <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> sınıfı okumanızdır gösterilir.  
  
```  
using System;  
using System.Configuration;  
using System.IdentityModel.Configuration;  
using System.IdentityModel.Tokens;  
using System.ServiceModel;  
using System.Xml;  
  
namespace CacheLibrary  
{  
    /// <summary>  
    /// This class acts as a proxy to the WcfSessionSecurityTokenCacheService.  
    /// </summary>  
    public class SharedSessionSecurityTokenCache : SessionSecurityTokenCache, ICustomIdentityConfiguration  
    {  
        private ISessionSecurityTokenCacheService WcfSessionSecurityTokenCacheServiceClient;  
  
        internal SharedSessionSecurityTokenCache()  
        {  
        }  
  
        /// <summary>  
        /// Creates a client channel to call the service host.  
        /// </summary>  
        protected void Initialize(string cacheServiceAddress)  
        {  
            if (this.WcfSessionSecurityTokenCacheServiceClient != null)  
            {  
                return;  
            }  
  
            ChannelFactory<ISessionSecurityTokenCacheService> cf = new ChannelFactory<ISessionSecurityTokenCacheService>(  
                new WS2007HttpBinding(SecurityMode.None),  
                new EndpointAddress(cacheServiceAddress));  
            this.WcfSessionSecurityTokenCacheServiceClient = cf.CreateChannel();  
        }  
  
        #region SessionSecurityTokenCache Members  
        // Delegates the following operations to the centralized session security token cache service in the web farm.  
  
        ...  
  
        public override SessionSecurityToken Get(SessionSecurityTokenCacheKey key)  
        {  
            return this.WcfSessionSecurityTokenCacheServiceClient.Get(key.EndpointId, GetContextIdString(key), GetKeyGenerationString(key));  
        }  
  
        ...  
  
        #endregion  
  
        #region ICustomIdentityConfiguration Members  
        // Called from configuration infrastructure to load custom elements  
        public void LoadCustomConfiguration(XmlNodeList nodeList)  
        {  
            // Retrieve the endpoint address of the centralized session security token cache service running in the web farm  
            if (nodeList.Count == 0)  
            {  
                throw new ConfigurationException("No child config element found under <sessionSecurityTokenCache>.");  
            }  
  
            XmlElement cacheServiceAddressElement = nodeList.Item(0) as XmlElement;  
            if (cacheServiceAddressElement.LocalName != "cacheServiceAddress")  
            {  
                throw new ConfigurationException("First child config element under <sessionSecurityTokenCache> is expected to be <cacheServiceAddress>.");  
            }  
  
            string cacheServiceAddress = null;  
            if (cacheServiceAddressElement.Attributes["url"] != null)  
            {  
                cacheServiceAddress = cacheServiceAddressElement.Attributes["url"].Value;  
            }  
            else  
            {  
                throw new ConfigurationException("<cacheServiceAddress> is expected to contain a 'url' attribute.");  
            }  
  
            // Initialize the proxy to the WebFarmSessionSecurityTokenCacheService  
            this.Initialize(cacheServiceAddress);  
        }  
        #endregion  
  
        private static string GetKeyGenerationString(SessionSecurityTokenCacheKey key)  
        {  
            return key.KeyGeneration == null ? null : key.KeyGeneration.ToString();  
        }  
  
        private static string GetContextIdString(SessionSecurityTokenCacheKey key)  
        {  
            return GetContextIdString(key.ContextId);  
        }  
  
        private static string GetContextIdString(UniqueId contextId)  
        {  
            return contextId == null ? null : contextId.ToString();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>  
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
 <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>  
 [WIF Oturum Yönetimi](../../../docs/framework/security/wif-session-management.md)
