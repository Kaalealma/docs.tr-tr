---
title: 'Nasıl yapılır: Oturum Gerektiren Bir Hizmet Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
ms.openlocfilehash: c7bcd0c08d00122df86d6682888907712f224a30
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-service-that-requires-sessions"></a>Nasıl yapılır: Oturum Gerektiren Bir Hizmet Oluşturma
Oturumları geri aramalar, çoklu atlamalı güvenlik ve istemciler ve hizmet örnekleri arasındaki ilişkileri gibi yararlı özellikleri etkinleştirir iki veya daha fazla uç noktalar arasında paylaşılan bir durum oluşturun. Windows Communication Foundation (WCF) uygulamaları oturumlarında hakkında daha fazla bilgi için bkz: [kullanarak oturumları](../../../../docs/framework/wcf/using-sessions.md).  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a>Bir sözleşme bağlamasına oturumları desteklemek gerekli olduğunu belirtmek için  
  
1.  Hizmet sözleşmesi en az bir işlem ile oluşturun. Hizmet sözleşmesi oluşturma örneği için bkz: [nasıl yapılır: bir hizmet sözleşmesini tanımlama](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).  
  
2.  Değiştirme <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> ayarlayarak sözleşme bildiren <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> ya da özellik:  
  
    -   <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> Bu sözleşme bir oturumunda çalıştırmanız gerekir  
  
    -   <xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType> Bu sözleşme bir oturumda çalıştırabilirsiniz  
  
    -   <xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType> Bu sözleşme bir oturumda çalıştırılmamalıdır durumunda.  
  
3.  Oturumları destekleyen bir bağlama kullanmak için hizmet uç noktası yapılandırın. Aşağıdaki yapılandırma örneği kullanımı gösterilmiştir <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, bir WS destekleyen`-`ReliableMessaging oturumu.  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]   
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir sözleşme düzeyi oturum gereksinimi belirtmek ve bu gereksinimi desteklemek için bir yapılandırma dosyası kullanmak gösterilmiştir <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> bağlama.  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)] 
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]      
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]     
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>  
 <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
