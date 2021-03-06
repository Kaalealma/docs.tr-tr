---
title: Oturumda Kuyruğa Alınmış İletileri Gruplandırma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- queues [WCF]. grouping messages
ms.assetid: 63b23b36-261f-4c37-99a2-cc323cd72a1a
ms.openlocfilehash: 62aa269d138d436824d3c825de9f722490d3b5bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="grouping-queued-messages-in-a-session"></a>Oturumda Kuyruğa Alınmış İletileri Gruplandırma
Windows Communication Foundation (WCF) tek bir alıcı uygulama tarafından bir dizi ilgili ileti işleme için bir arada gruplandırmak izin veren bir oturum sağlar. Oturumun bir parçası olan iletiler aynı işlemin parçası olmalıdır. Tüm oturum işlenmek üzere bir ileti başarısız olursa tüm iletileri aynı işlemin bir parçası olduğundan geri alınır. Oturumu sıralarındaki ve zararlı sıraları açısından benzer davranışları yok. Oturumları için yapılandırılmış bir sıralı bağlama üzerinde ayarlanan yaşam süresi (TTL) özelliği için zaman oturum bir bütün olarak uygulanır. Yalnızca TTL süresi dolmadan önce bazı iletiler oturumunda gönderilen tüm oturum sahipsiz sıraya konur. Benzer şekilde, bir uygulama için uygulama sırasından gönderilmek üzere bir oturumdaki iletilerin başarısız olduğunda, tüm oturum zararlı sırasına (varsa) yerleştirilir.  
  
## <a name="message-grouping-example"></a>İleti gruplama örneği  
 İletileri gruplandırma yararlı olduğu bir sipariş işleme uygulamanın bir WCF hizmeti olarak uygularken örnektir. Örneğin, bir istemci bir öğe sayısı içeren bu uygulamaya yönelik bir sipariş gönderir. Her öğe için istemci gönderilmekte olan ayrı bir iletide sonuçları hizmetine yapılan bir çağrı yapar. Hizmet vermemesini A ilk öğe ve ikinci öğe almak için Sunucu B almaya mümkündür. Uygun sırayla bulmak ve kendisine, öğeyi eklemek bu öğeyi işleyen sunucu sahip bir öğe eklenir her zaman son derece verimsiz olduğu. Hala sunucu şu anda işlenmekte olan tüm siparişleri izlemek ve yeni öğe ait hangisinin belirlemek için tüm istekleri işleme yalnızca tek bir sunucuyla böyle verimsiz çalıştırın. Tüm istekler için tek bir sıralamayı büyük ölçüde gruplandırma bu tür bir uygulama, uygulanmasını basitleştirir. İstemci uygulaması için tek bir sıralamayı tüm öğeleri bir oturumda gönderir hizmet sırası işlediğinde, tek seferde tüm oturum işler şekilde. \  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-set-up-a-service-contract-to-use-sessions"></a>Oturumları kullanmak için bir hizmet sözleşmesini ayarlamak için  
  
1.  Bir oturum gerektiren bir hizmet sözleşmesini tanımlama. Bunu yapmak <xref:System.ServiceModel.OperationContractAttribute> özniteliği ve belirterek:  
  
    ```  
    SessionMode=SessionMode.Required  
    ```  
  
2.  Bu yöntemlerin herhangi bir şey döndürmeyen çünkü tek yönlü olarak sözleşme işlemlerinde işaretleyin. Bu gerçekleştirilir <xref:System.ServiceModel.OperationContractAttribute> özniteliği ve belirterek:  
  
    ```  
    [OperationContract(IsOneWay = true)]  
    ```  
  
3.  Hizmet sözleşmesini uygulama ve belirtin bir `InstanceContextMode` , `PerSession`. Bu hizmet yalnızca bir kez her oturum başlatır.  
  
    ```  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    ```  
  
4.  Her hizmet işlemi, bir işlem gerekiyor. Bu konuda belirtin <xref:System.ServiceModel.OperationBehaviorAttribute> özniteliği. İşlem tamamlandığında işlemi de ayarlamalısınız `TransactionAutoComplete` için `true`.  
  
    ```  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]   
    ```  
  
5.  Sistem tarafından sağlanan kullanan bir uç nokta yapılandırma `NetMsmqBinding` bağlama.  
  
6.  Kullanarak bir işlem sırası oluşturmak <xref:System.Messaging>. Sıranın Message Queuing (MSMQ) veya MMC kullanarak da oluşturabilirsiniz. Bunu yaparsanız, bir işlem sırası oluşturun.  
  
7.  Kullanarak bir hizmet ana bilgisayar hizmeti oluşturma <xref:System.ServiceModel.ServiceHost>.  
  
8.  Hizmetin kullanılabilmesi için hizmet ana bilgisayarı açın.  
  
9. Hizmet ana bilgisayarını kapatın.  
  
#### <a name="to-set-up-a-client"></a>Bir istemcinin ayarlamak için  
  
1.  İşlem sırası yazmak için bir işlem kapsamı oluşturun.  
  
2.  Kullanarak WCF istemcisi oluşturma [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) aracı.  
  
3.  Sipariş verin.  
  
4.  WCF istemcisini kapatın.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek kodunu sağlar `IProcessOrder` hizmet ve bir istemci için bu hizmeti kullanır. Bu, sıraya alınan oturumları WCF gruplandırma davranışını sağlamak için nasıl kullandığını gösterir.  
  
### <a name="code-for-the-service"></a>Hizmet için kodu  
 [!code-csharp[S_Msmq_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/service.cs#1)]
 [!code-vb[S_Msmq_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/service.vb#1)]  
  
  
  
### <a name="code-for-the-client"></a>İstemci kodu  
 [!code-csharp[S_Msmq_Session#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/client.cs#3)]
 [!code-vb[S_Msmq_Session#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/client.vb#3)]  
  
  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Oturumlar ve Kuyruklar](../../../../docs/framework/wcf/samples/sessions-and-queues.md)  
 [Kuyruklara Genel Bakış](../../../../docs/framework/wcf/feature-details/queues-overview.md)
