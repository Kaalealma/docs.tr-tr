---
title: Taşıma Güvenliği Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 00959326-aa9d-44d0-af61-54933d4adc7f
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 12b491971a9f3faa57edb1ccf9fb59351ed45f3b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="transport-security-overview"></a>Taşıma Güvenliği Genel Bakış
Bağlama ve kullanılan taşıma taşıma güvenlik mekanizmaları Windows Communication Foundation (WCF) bağlıdır. Örneğin, kullanırken <xref:System.ServiceModel.WSHttpBinding> sınıfı, aktarım HTTP ve taşıma güvenliğini sağlamak için birincil mekanizmayı Güvenli Yuva Katmanı (SSL) genellikle HTTPS adlı HTTP üzerinden şeklindedir. Bu konuda, WCF sistem tarafından sağlanan bağlamalar kullanılan ana Aktarım güvenlik mekanizmaları anlatılmaktadır.  
  
> [!NOTE]
>  SSL güvenlik .NET Framework 3.5 ve sonraki sürümleriyle birlikte kullanıldığında bir WCF istemcisi hem ara sertifika, sertifika deposunda kullanır ve hizmetin üzerinde sertifika zinciri doğrulaması gerçekleştirmek için SSL anlaşması sırasında Ara sertifikaların alınan Sertifika. .NET framework 3.0 yalnızca yerel sertifika deposunda yüklü Ara sertifikaları kullanır.  
  
> [!WARNING]
>  Taşıma güvenliği kullanıldığında, <!--zz <xref:System.Treading.Thread.CurrentPrincipal%2A> --> `CurrentPrincipal` özellik üzerine yazılır. Bunun gerçekleşmesini kümesinden önlemek için <!--zz <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermission%2A> --> `PrincipalPermission` yok. <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> Hizmet açıklaması ayarlanabilir bir hizmet davranıştır.  
  
## <a name="basichttpbinding"></a>BasicHttpBinding  
 Varsayılan olarak, <xref:System.ServiceModel.BasicHttpBinding> sınıfı güvenlik sağlamaz. Bu bağlama güvenlik kullanılmaz Web hizmeti sağlayıcıları ile birlikte çalışabilirlik için tasarlanmıştır. Ancak, ayarlayarak güvenliği geçiş yapabilirsiniz <xref:System.ServiceModel.BasicHttpSecurity.Mode%2A> dışındaki herhangi bir değer özelliğine <xref:System.ServiceModel.BasicHttpSecurityMode.None>. Taşıma güvenliği etkinleştirmek için özellik ayarlamak <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.  
  
### <a name="interoperation-with-iis"></a>IIS ile birlikte çalışma  
 <xref:System.ServiceModel.BasicHttpBinding> Sınıfı varolan Web Hizmetleri ile birlikte çalışmak için öncelikle kullanılır ve birçok hizmetlerin Internet Information Services (IIS) tarafından barındırılır. Sonuç olarak, bu bağlama için taşıma güvenliği IIS siteleri ile sorunsuz birlikte çalışma için tasarlanmıştır. Bu güvenlik modunu ayarlayarak yapılır <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> ve ardından istemci ayar kimlik bilgisi türü. Kimlik bilgisi türü değerleri IIS dizin güvenlik mekanizmalarına karşılık gelir. Aşağıdaki kod ayarlanan modunu gösterir ve Windows kimlik bilgisi türünü ayarlayın. İstemci ve sunucu aynı Windows etki alanında olduğunda, bu yapılandırmayı kullanabilirsiniz.  
  
 [!code-csharp[c_ProgrammingSecurity#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#10)] 
 [!code-vb[c_ProgrammingSecurity#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#10)]  
  
 Veya yapılandırma:  
  
```xml  
<bindings>  
  <basicHttpBinding>  
    <binding name="SecurityByTransport">  
      <security mode="Transport">  
        <transport clientCredentialType="Windows" />  
       </security>  
     </binding>  
  </basicHttpBinding>  
</bindings>  
```  
  
 Aşağıdaki bölümlerde, diğer istemci kimlik bilgisi türleri açıklanmaktadır.  
  
#### <a name="basic"></a>Temel  
 Bu IIS temel kimlik doğrulama yöntemi karşılık gelir. Bu modu kullanırken, IIS sunucusu Windows kullanıcı hesapları ve uygun NTFS dosya sistemi izinleri ile yapılandırılması gerekir. Hakkında daha fazla bilgi için [!INCLUDE[iis601](../../../../includes/iis601-md.md)], bkz: [temel kimlik doğrulamasını etkinleştirme ve bölge adını yapılandırma](http://go.microsoft.com/fwlink/?LinkId=88592). Hakkında daha fazla bilgi için [!INCLUDE[iisver](../../../../includes/iisver-md.md)], bkz: [IIS 7.0 Beta: temel kimlik doğrulaması yapılandırma](http://go.microsoft.com/fwlink/?LinkId=88593).  
  
#### <a name="certificate"></a>Sertifika  
 IIS, istemcilerin bir sertifika ile oturum açmalarını gerektirme seçeneği vardır. Bu özellik ayrıca bir Windows hesabı için bir istemci sertifikası eşleme sağlar. Hakkında daha fazla bilgi için [!INCLUDE[iis601](../../../../includes/iis601-md.md)], bkz: [istemci sertifikalarını etkinleştirme IIS 6.0](http://go.microsoft.com/fwlink/?LinkId=88594). Hakkında daha fazla bilgi için [!INCLUDE[iisver](../../../../includes/iisver-md.md)], bkz: [IIS 7.0 Beta: IIS 7.0 sunucu sertifikalarını yapılandırma](http://go.microsoft.com/fwlink/?LinkId=88595).  
  
#### <a name="digest"></a>Özet  
 Özet kimlik doğrulaması için temel kimlik doğrulaması benzer, ancak kimlik bilgileri gönderme düz metin olarak karması olarak yerine avantajı sağlar. Hakkında daha fazla bilgi için [!INCLUDE[iis601](../../../../includes/iis601-md.md)], bkz: [IIS 6.0 Özet kimlik doğrulaması](http://go.microsoft.com/fwlink/?LinkID=88443). Hakkında daha fazla bilgi için [!INCLUDE[iisver](../../../../includes/iisver-md.md)], bkz: [IIS 7.0 Beta: Özet kimlik doğrulaması yapılandırma](http://go.microsoft.com/fwlink/?LinkId=88596).  
  
#### <a name="windows"></a>Windows  
 Bu Tümleşik Windows kimlik doğrulaması IIS'de karşılık gelir. Bu değer ayarlandığında, sunucunun kendi etki alanı denetleyicisi olarak Kerberos protokolünü kullanan bir Windows etki alanı mevcut ayrıca beklenir. Sunucu, Kerberos tarafından desteklenen bir etki alanı üzerinde değil ya da Kerberos sistem başarısız olursa, sonraki bölümde açıklanan NT LAN Yöneticisi (NTLM) değeri kullanabilirsiniz. Hakkında daha fazla bilgi için [!INCLUDE[iis601](../../../../includes/iis601-md.md)], bkz: [IIS 6.0, tümleşik Windows kimlik doğrulaması](http://go.microsoft.com/fwlink/?LinkId=88597). Hakkında daha fazla bilgi için [!INCLUDE[iisver](../../../../includes/iisver-md.md)], bkz: [IIS 7.0 Beta: IIS 7.0 sunucu sertifikalarını yapılandırma](http://go.microsoft.com/fwlink/?LinkId=88595).  
  
#### <a name="ntlm"></a>NTLM  
 Bu, Kerberos protokolü başarısız olursa NTLM kimlik doğrulaması için kullanılacak sunucuyu sağlar. IIS yapılandırma hakkında daha fazla bilgi için [!INCLUDE[iis601](../../../../includes/iis601-md.md)], bkz: [zorlama NTLM kimlik doğrulaması](http://go.microsoft.com/fwlink/?LinkId=88598). İçin [!INCLUDE[iisver](../../../../includes/iisver-md.md)], NTLM kimlik doğrulaması Windows kimlik doğrulaması içerir. Daha fazla bilgi için bkz: [IIS 7.0 Beta: IIS 7.0 sunucu sertifikalarını yapılandırma](http://go.microsoft.com/fwlink/?LinkID=88595).  
  
## <a name="wshttpbinding"></a>WsHttpBinding  
 <xref:System.ServiceModel.WSHttpBinding> Sınıfı, WS - uygulama hizmetleri ile birlikte çalışma için tasarlanmıştır * belirtimleri. Bu bağlama için taşıma güvenliği, HTTP veya HTTPS üzerinden Güvenli Yuva Katmanı (SSL) vardır. SSL kullanan bir WCF uygulaması oluşturmak için uygulamayı barındırmak için IIS kullanın. Alternatif olarak, bir kendi kendini barındıran uygulaması oluşturuyorsanız, bir bilgisayardaki belirli bir bağlantı noktası bir X.509 sertifikası bağlamak için HttpCfg.exe aracını kullanın. Bağlantı noktası numarası, uç nokta adresi olarak WCF uygulaması bir parçası olarak belirtilir. Aktarım modu kullanırken, uç nokta adresi HTTPS protokolünü içermelidir veya çalışma zamanında bir özel durum oluşturulur. Daha fazla bilgi için bkz: [HTTP taşıma güvenliği](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 İstemci kimlik doğrulaması için ayarlanmış <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> özelliği <xref:System.ServiceModel.HttpTransportSecurity> birine sınıfı <xref:System.ServiceModel.HttpClientCredentialType> numaralandırma değerleri. Numaralandırma değerleri için istemci kimlik bilgisi türlerinin aynıdır <xref:System.ServiceModel.BasicHttpBinding> ve IIS hizmetleri ile barındırılacak şekilde tasarlanmıştır.  
  
 Aşağıdaki örnek, bir Windows istemcisi kimlik bilgisi türüyle kullanılan bağlamasını gösterir.  
  
 [!code-csharp[c_ProgrammingSecurity#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#11)]
 [!code-vb[c_ProgrammingSecurity#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#11)]  
  
## <a name="wsdualhttpbinding"></a>WSDualHttpBinding  
 Bu bağlama, yalnızca ileti düzeyi güvenlik, aktarım düzeyinde güvenlik sağlar.  
  
## <a name="nettcpbinding"></a>NetTcpBinding  
 <xref:System.ServiceModel.NetTcpBinding> Sınıfı için ileti aktarımını TCP kullanır. Aktarım modu için güvenlik, TCP üzerinden Aktarım Katmanı Güvenliği (TLS) uygulama tarafından sağlanır. TLS uygulama işletim sistemi tarafından sağlanır.  
  
 Ayarlayarak istemcinin kimlik bilgisi türü belirtebilirsiniz <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> özelliği <xref:System.ServiceModel.TcpTransportSecurity> birine sınıfı <xref:System.ServiceModel.TcpClientCredentialType> aşağıdaki kodda gösterildiği gibi değerler.  
  
 [!code-csharp[c_ProgrammingSecurity#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#12)]
 [!code-vb[c_ProgrammingSecurity#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#12)]  
  
#### <a name="client"></a>İstemci  
 İstemcide, bir sertifika kullanarak belirtmelisiniz <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> yöntemi <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> sınıfı.  
  
> [!NOTE]
>  Windows güvenliği kullanıyorsanız, bir sertifika gerekli değildir.  
  
 Aşağıdaki kod benzersiz olarak tanımlayan sertifikanın parmak izini kullanır. Sertifikalar hakkında daha fazla bilgi için bkz: [sertifikalarla çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 [!code-csharp[c_ProgrammingSecurity#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#13)]
 [!code-vb[c_ProgrammingSecurity#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#13)]  
  
 Alternatif olarak, sertifika istemci yapılandırmasında belirtin kullanarak bir [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) davranışları bölümünde öğesi.  
  
```xml  
<behaviors>  
  <behavior>  
   <clientCredentials>  
     <clientCertificate findValue= "101010101010101010101010101010000000000"   
      storeLocation="LocalMachine" storeName="My"   
      X509FindType="FindByThumbPrint"/>  
     </clientCertificate>  
   </clientCredentials>  
 </behavior>  
</behaviors>    
```  
  
## <a name="netnamedpipebinding"></a>NetNamedPipeBinding  
 <xref:System.ServiceModel.NetNamedPipeBinding> Sınıfı verimli içi makine iletişimi için tasarlanmıştır; diğer bir deyişle, işlemler için kanal kanalları adlı olsa da aynı bilgisayarda çalışan aynı ağda iki bilgisayar arasında oluşturulabilir. Bu bağlama yalnızca aktarım düzeyinde güvenlik sağlar. Bu bağlamayı kullanan uygulamaları oluştururken, uç nokta adresleri "net.pipe" uç nokta adresi protokol olarak eklemeniz gerekir.  
  
## <a name="wsfederationhttpbinding"></a>WSFederationHttpBinding  
 Taşıma güvenliği kullanırken bu bağlama ile verilen bir belirteç HTTPS bilinen HTTP üzerinden SSL kullanır (<xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential>). Federasyon uygulamaları hakkında daha fazla bilgi için bkz: [Federasyon ve verilen belirteçleri](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## <a name="netpeertcpbinding"></a>NetPeerTcpBinding  
 <xref:System.ServiceModel.NetPeerTcpBinding> Eşler arası ağ özelliğini kullanarak verimli iletişimi için tasarlanmış güvenli bir taşıma bir sınıftır. Bağlama ve sınıf adını yazarak gösterildiği gibi TCP protokolüdür. Güvenlik modu için taşıma olarak ayarlandığında bağlama TLS üzerinden TCP uygular. Eşler arası özelliği hakkında daha fazla bilgi için bkz: [eşler arası ağ](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
## <a name="msmqintegrationbinding-and-netmsmqbinding"></a>MsmqIntegrationBinding ve NetMsmqBinding  
 Tam bir aktarım tartışma için bkz: (daha önce MSMQ olarak da adlandırılır) Message Queuing ile güvenlik [taşıma güvenliği kullanarak iletileri güvenli hale getirme](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Güvenliğini Programlama](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
