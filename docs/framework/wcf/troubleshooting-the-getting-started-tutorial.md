---
title: Başlarken Öğreticisi Sorun Giderme
ms.date: 03/30/2017
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
ms.openlocfilehash: 12812bd1ef88eab14a8defed0b71657b0d33c618
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="troubleshooting-the-getting-started-tutorial"></a>Başlarken Öğreticisi Sorun Giderme
Bu konuda başlangıç Öğreticisi ve bunların nasıl çözüleceği ile çalışırken en sık karşılaşılan sorunlar listelenmiştir.  
  
1.  [I sabit Sürücümün proje dosyalarını bulamıyor.](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q1)  
  
2.  [Hizmet uygulaması çalıştırma denemesi: HTTP URL kaydedemedi http://+:8000/ServiceModelSamples/Service/. İşleminizi bu ad alanına erişim hakları yok.](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q2)  
  
3.  [Svcutil.exe aracını kullanmaya çalışıyor: 'svcutil' iç ya da dış komut, çalıştırılabilir program ya da toplu iş dosyası tanınmıyor.](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q3)  
  
4.  [Svcutil.exe tarafından oluşturulan App.config dosyası bulunamıyor.](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q4)  
  
5.  [İstemci uygulaması derleme: 'CalculatorClient' için tanım içermiyor '&lt;yöntem adı&gt;'ve hiçbir uzantı metodu'&lt;yöntem adı&gt;' ilk bağımsız değişken türü 'CalculatorClient' kabul etme bulunamadı (kullanarak bir eksik yönergesi veya bir derleme başvurusu?)](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q5)  
  
6.  [İstemci uygulaması derleme: 'CalculatorClient' bulunamadı türü veya ad alanı adı (kullanarak bir eksik yönergesi veya bir derleme başvurusu?)](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q6)  
  
7.  [İstemcisi çalıştıran: işlenmeyen özel durum: System.ServiceModel.EndpointNotFoundException: bağlanılamadı http://localhost:8000/ServiceModelSamples/Service/CalculatorService. TCP hata kodu 10061: hedef makine etkin olarak reddettiğinden bağlantı kurulamadı.](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q7)  
  
<a name="BKMK_q1"></a>   
## <a name="i-am-unable-to-find-the-project-files-on-my-hard-drive"></a>I sabit Sürücümün proje dosyalarını bulamıyor.  
 Visual Studio proje dosyalarını c:\users içinde kaydeder\\< kullanıcı name\Documents\\< Visual Studio sürümü\>içinde \Projects [!INCLUDE[wv](../../../includes/wv-md.md)] ve [!INCLUDE[win7_client_secondref](../../../includes/win7-client-secondref-md.md)], c:\Documents ve ayarlarını\\< kullanıcı adı \>\My belgeleri\\< Visual Studio sürümü\>\Projects önceki Windows sürümlerinde.  
  
<a name="BKMK_q2"></a>   
## <a name="attempting-to-run-the-service-application-http-could-not-register-url-http8000servicemodelsamplesservice-your-process-does-not-have-access-rights-to-this-namespace"></a>Hizmet uygulaması çalıştırma denemesi: HTTP URL kaydedemedi http://+:8000/ServiceModelSamples/Service/. İşleminizi bu ad alanına erişim hakları yok.  
 Bir WCF hizmetini barındıran işlemin yönetici ayrıcalıklarıyla çalıştırılmalıdır. İçinde hizmetinden çalıştırıyorsanız [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] çalıştırmalısınız [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] yönetici olarak. Bunu yapmak için **Başlat**, sağ [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] seçip **yönetici olarak çalıştır**. Bir komut satırı isteminde Hizmeti çalışıyorsa komut satırı istemi benzer şekilde bir yönetici olarak başlatmanız gerekir. Tıklatın **Başlat**, sağ **komut istemi** seçip **yönetici olarak çalıştır**.  
  
<a name="BKMK_q3"></a>   
## <a name="attempting-to-use-the-svcutilexe-tool-svcutil-is-not-recognized-as-an-internal-or-external-command-operable-program-or-batch-file"></a>Svcutil.exe aracını kullanmaya çalışıyor: 'svcutil' iç ya da dış komut, çalıştırılabilir program ya da toplu iş dosyası tanınmıyor.  
 Svcutil.exe sistem yolunda olması gerekir. En kolay çözüm komut istemi kullanmaktır. Tıklatın **Başlat**seçin **tüm programlar**, [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], **Visual Studio Araçları**, ve [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] **komut istemi**. Bu komut istemini bir parçası olarak gönderilen tüm araçlar için doğru konuma sistem yolunu ayarlar [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].  
  
<a name="BKMK_q4"></a>   
## <a name="unable-to-find-the-appconfig-file-generated-by-svcutilexe"></a>Svcutil.exe tarafından oluşturulan App.config dosyası bulunamıyor.  
 **Varolan öğeyi Ekle** iletişim varsayılan olarak yalnızca şu uzantılara sahip dosyaları görüntüler: .cs, .resx, .settings, .xsd, .wsdl. Tüm dosya türlerini seçerek görmek istediğinizi belirtebilirsiniz **tüm dosyalar (\*.\*)**  liste kutusunda sağ alt köşesindeki açılır **varolan öğeyi Ekle** iletişim kutusu.  
  
<a name="BKMK_q5"></a>   
## <a name="compiling-the-client-application-calculatorclient-does-not-contain-a-definition-for-method-name-and-no-extension-method-method-name-accepting-a-first-argument-of-type-calculatorclient-could-be-found-are-you-missing-a-using-directive-or-an-assembly-reference"></a>İstemci uygulaması derleme: 'CalculatorClient' için tanım içermiyor '\<yöntem adı >' ve hiçbir uzantı metodu '\<yöntem adı >' ilk bağımsız değişken türü 'CalculatorClient' kabul bulunamadı (olduğunuz kullanarak bir eksik yönergesi veya bir derleme başvurusu?)  
 İle işaretlenen yöntemleri `ServiceOperationAttribute` dış dünya sunulur. Atlanırsa `ServiceOperationAttribute` yöntemlerden birini özniteliğinden `ICalculator` arabirimi özniteliği eksik işlemi çağrıda bir istemci uygulaması derleme sırasında bu hata iletisini alırsınız.  
  
<a name="BKMK_q6"></a>   
## <a name="compiling-the-client-application-the-type-or-namespace-name-calculatorclient-could-not-be-found-are-you-missing-a-using-directive-or-an-assembly-reference"></a>İstemci uygulaması derleme: 'CalculatorClient' bulunamadı türü veya ad alanı adı (kullanarak bir eksik yönergesi veya bir derleme başvurusu?)  
 İstemci projeniz Proxy.cs veya Proxy.vb dosyası eklemezseniz bu hatayı alırsınız.  
  
<a name="BKMK_q7"></a>   
## <a name="running-the-client-unhandled-exception-systemservicemodelendpointnotfoundexception-could-not-connect-to-httplocalhost8000servicemodelsamplesservicecalculatorservice-tcp-error-code-10061-no-connection-could-be-made-because-the-target-machine-actively-refused-it"></a>İstemcisi çalıştıran: işlenmeyen özel durum: System.ServiceModel.EndpointNotFoundException: bağlanılamadı http://localhost:8000/ServiceModelSamples/Service/CalculatorService. TCP hata kodu 10061: hedef makine etkin olarak reddettiğinden bağlantı kurulamadı.  
 Hizmet çalıştırmadan istemci uygulaması değilse bu hata oluşur.  
  
<a name="BKMK_q8"></a>   
## <a name="unhandled-exception-systemservicemodelsecuritysecuritynegotiationexception-soap-security-negotiation-with-httplocalhost8000servicemodelsamplesservicecalculatorservice-for-target-httplocalhost8000servicemodelsamplesservicecalculatorservice-failed"></a>İşlenmeyen özel durum: System.ServiceModel.Security.SecurityNegotiationException: SOAP güvenlik anlaşması 'http://localhost:8000/ServiceModelSamples/Service/CalculatorService'için hedef'http://localhost:8000/ServiceModelSamples/Service/CalculatorService' başarısız oldu  
 Bu hata, ağ bağlantısı yok etki alanına katılmış bir bilgisayarda oluşur. Bilgisayarınız ağa bağlanın ya da hem istemci hem de hizmet için güvenlik devre dışı bırakma. Hizmet için şu WSHttpBinding oluşturan kodu değiştirin.  
  
```  
// Step 3 of the hosting procedure: Add a service endpoint  
selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
```  
  
 İstemci için değiştirme  **\<Güvenlik >** öğesinin altında  **\<bağlama >** aşağıdaki gibi öğe:  
  
```xml  
<security mode="Node" />  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlangıç Öğreticisi](../../../docs/framework/wcf/getting-started-tutorial.md)  
 [WCF Sorun Giderme Hızlı Başlangıcı](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md)  
 [Kurulum Sorunlarını Giderme](../../../docs/framework/wcf/troubleshooting-setup-issues.md)
