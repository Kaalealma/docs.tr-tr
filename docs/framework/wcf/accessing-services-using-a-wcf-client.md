---
title: WCF İstemcisi Kullanarak Hizmetlere Erişme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], consuming services
ms.assetid: d780af9f-73c5-42db-9e52-077a5e4de7fe
ms.openlocfilehash: b0bde07dbeb70eaafbde4d90627d245554ad7ca6
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="accessing-services-using-a-wcf-client"></a>WCF İstemcisi Kullanarak Hizmetlere Erişme
Bir hizmeti oluşturduktan sonra sonraki adım bir WCF istemcisi proxy oluşturmaktır. Bir istemci uygulaması WCF istemci proxy hizmeti ile iletişim kurmak için kullanır. İstemci uygulamaları genellikle hizmetini çağırmak için kullanılan WCF istemci kodu oluşturmak üzere bir hizmetin meta veri içeri aktarın.  
  
 Bir WCF istemcisi oluşturmak için temel adımlar şunlardır:  
  
1.  Hizmet koduna derleyin.  
  
2.  WCF istemci proxy oluşturur.  
  
3.  WCF istemci proxy örneği oluşturur.  
  
 WCF istemci proxy daha fazla bilgi için bkz: hizmet Model meta veri yardımcı Programracı (SvcUtil.exe) kullanarak el ile oluşturulabilir [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). WCF istemci proxy ayrıca Visual Studio'da hizmet Başvurusu Ekle özelliği kullanılarak oluşturulabilir. Hizmet yöntemlerden birini kullanarak WCF istemci proxy oluşturmak için çalıştırması gerekir. Hizmet kendiliğinden barındırılır varsa, ana bilgisayar çalıştırmanız gerekir. Hizmet IIS'de barındırılıyorsa / olan başka bir şey yapmanız gerekmez.  
  
## <a name="servicemodel-metadata-utility-tool"></a>ServiceModel meta veri yardımcı Programracı  
 [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) meta verilerini kodu oluşturmak için bir komut satırı aracıdır. Bir temel Svcutil.exe komutu örneği kullanılmasıdır.  
  
```  
Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
```  
  
 Alternatif olarak, Web Hizmetleri Açıklama Dili (WSDL) ve XML Şeması Tanım Dili (XSD) dosyaları dosya sisteminde ile Svcutil.exe kullanabilirsiniz.  
  
```  
Svcutil.exe <list of WSDL and XSD files on file system>  
```  
  
 Sonuç istemci uygulamanın hizmetini çağırmak için kullanabileceği WCF istemci kodu içeren bir kod dosyasıdır.  
  
 Aracı, yapılandırma dosyaları oluşturmak için de kullanabilirsiniz.  
  
```  
Svcutil.exe <file1 [,file2]>  
```  
  
 Yalnızca bir dosya adı verilen, çıktı dosyası adını olmasıdır. İki dosya adları verilirse, ilk dosya içerikleri oluşturulan yapılandırmayla birleştirilmiş ve ikinci dosyaya yazılan bir giriş yapılandırma dosyası ise. Yapılandırma hakkında daha fazla bilgi için bkz: [hizmetler için bağlamaları yapılandırma](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).  
  
> [!IMPORTANT]
>  Güvenli olmayan meta veri isteklerine yönelik bazı riskleri herhangi güvenli ağ isteği yapan aynı şekilde:, kurduğunuz endpoint kimin olduğu yazacaktır olduğundan emin değilseniz, aldığınız bilgiler kötü amaçlı bir hizmete meta verileri olabilir.  
  
## <a name="add-service-reference-in-visual-studio"></a>Visual Studio'da hizmet Başvurusu Ekle  
 Hizmetin çalışmasını ile WCF istemci proxy içerir ve seçin projeye sağ tıklayın **hizmet Başvurusu Ekle**. İçinde **hizmeti başvuru iletişim kutusu ekleme** çağrısı tıklatıp istediğiniz hizmeti URL'sini yazın **Git** düğmesi. İletişim kutusunda belirttiğiniz adresinde kullanılabilir hizmetlerin listesini görüntüler. Sözleşmeler ve kullanılabilir işlemleri görmek, üretilen kod için bir ad belirtin ve hizmeti çift tıklatın **Tamam** düğmesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği bir hizmet için oluşturulan bir hizmet sözleşmesini gösterir.  
  
```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    // Other methods are not shown here.
}
```
  
```vb
' Define a service contract.
<ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
Public Interface ICalculator
    <OperationContract()>  _
    Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
    ' Other methods are not shown here.
End Interface
```
  
 Visual Studio'da hizmet Başvurusu Ekle ve ServiceModel meta veri yardımcı programı aracı aşağıdaki WCF istemci sınıfı oluşturur. Genel sınıf devralır <xref:System.ServiceModel.ClientBase%601> sınıfı ve uygulayan `ICalculator` arabirimi. Araç ayrıca oluşturur `ICalculator` arabirimi (burada gösterilmiyor).  
  
```csharp
public partial class CalculatorClient : System.ServiceModel.ClientBase<ICalculator>, ICalculator
{
    public CalculatorClient()
    {}

    public CalculatorClient(string endpointConfigurationName) :
            base(endpointConfigurationName)
    {}

    public CalculatorClient(string endpointConfigurationName, string remoteAddress) :
            base(endpointConfigurationName, remoteAddress)
    {}

    public CalculatorClient(string endpointConfigurationName,
        System.ServiceModel.EndpointAddress remoteAddress) :
            base(endpointConfigurationName, remoteAddress)
    {}

    public CalculatorClient(System.ServiceModel.Channels.Binding binding,
        System.ServiceModel.EndpointAddress remoteAddress) :
            base(binding, remoteAddress)
    {}

    public double Add(double n1, double n2)
    {
        return base.Channel.Add(n1, n2);
    }
}
```  
  
```vb  
Partial Public Class CalculatorClient
    Inherits System.ServiceModel.ClientBase(Of ICalculator)
    Implements ICalculator

    Public Sub New()
        MyBase.New
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String)
        MyBase.New(endpointConfigurationName)
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String, ByVal remoteAddress As String)
        MyBase.New(endpointConfigurationName, remoteAddress)
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String,
        ByVal remoteAddress As System.ServiceModel.EndpointAddress)
        MyBase.New(endpointConfigurationName, remoteAddress)
    End Sub

    Public Sub New(ByVal binding As System.ServiceModel.Channels.Binding,
        ByVal remoteAddress As System.ServiceModel.EndpointAddress)
        MyBase.New(binding, remoteAddress)
    End Sub

    Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
        Implements ICalculator.Add
        Return MyBase.Channel.Add(n1, n2)
    End Function
End Class
```
  
## <a name="using-the-wcf-client"></a>WCF istemcisi kullanarak  
 WCF istemcisini kullanmak için bir WCF istemcisi örneği oluşturun ve sonra aşağıdaki kodda gösterildiği gibi kendi yöntemlerini çağırın.  
  
```csharp
// Create a client object with the given client endpoint configuration.
CalculatorClient calcClient = new CalculatorClient("CalculatorEndpoint"));
// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = calcClient.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
```
  
```vb
' Create a client object with the given client endpoint configuration.
Dim calcClient As CalculatorClient = _
New CalculatorClient("CalculatorEndpoint")

' Call the Add service operation.
Dim value1 As Double = 100.00D
Dim value2 As Double = 15.99D
Dim result As Double = calcClient.Add(value1, value2)
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)
```
  
## <a name="debugging-exceptions-thrown-by-a-client"></a>Bir istemci tarafından oluşturulan özel durumları hata ayıklama  
 Bir WCF istemcisi tarafından oluşturulan birçok özel durumları hizmetteki bir özel durum nedeniyle. Bu, bazı örnekler şunlardır:  
  
-   <xref:System.Net.Sockets.SocketException>: Varolan bir bağlantıyı zorla uzak ana bilgisayar tarafından kapatıldı.  
  
-   <xref:System.ServiceModel.CommunicationException>: Arka plandaki bağlantı beklenmedik şekilde kesildi.  
  
-   <xref:System.ServiceModel.CommunicationObjectAbortedException>: Yuva bağlantısı iptal edildi. Bu uzak ana bilgisayara veya bir arka plandaki ağ kaynağı sorunu aşılması alma zaman aşımı iletinizi işlenirken bir hata kaynaklanabilir.  
  
 Bu tür özel durumlar ortaya çıktığında, sorunu çözmek için en iyi hizmet tarafı izlemeyi etkinleştirmek ve hangi özel durumu var. oluştu belirlemek için yoludur. İzleme hakkında daha fazla bilgi için bkz: [izleme](../../../docs/framework/wcf/diagnostics/tracing/index.md) ve [uygulamanız sorun giderme kullanarak izlemeyi](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: İstemci Oluşturma](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [Nasıl yapılır: Çift Yönlü Sözleşme ile Hizmetlere Erişme](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)  
 [Nasıl yapılır: Hizmet İşlemlerini Zaman Uyumsuz Olarak Çağırma](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)  
 [Nasıl yapılır: Tek Yönlü ve İstek-Yanıt Sözleşmeleriyle Hizmetlere Erişme](../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)  
 [Nasıl yapılır: WSE 3.0 Hizmetine Erişme](../../../docs/framework/wcf/feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)  
 [Oluşturulmuş İstemci Kodlarını Anlama](../../../docs/framework/wcf/feature-details/understanding-generated-client-code.md)  
 [Nasıl yapılır: XmlSerializer Kullanarak WCF İstemci Uygulamalarının Başlangıç Zamanlarını İyileştirme](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)  
 [İstemci Çalışma Zamanı Davranışını Belirtme](../../../docs/framework/wcf/specifying-client-run-time-behavior.md)  
 [İstemci Davranışlarını Yapılandırma](../../../docs/framework/wcf/configuring-client-behaviors.md)
