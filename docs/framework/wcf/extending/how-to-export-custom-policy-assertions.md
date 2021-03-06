---
title: 'Nasıl yapılır: Özel İlke Onaylamalarını Dışa Aktarma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99030386-43b0-4f7b-866d-17ea307f5cbd
ms.openlocfilehash: 4182007d32ea857aa333542b4df29da18b8062df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-export-custom-policy-assertions"></a>Nasıl yapılır: Özel İlke Onaylamalarını Dışa Aktarma
İlke onaylamalarını hizmet uç noktası gereksinimlerini ve özelliklerini açıklar. Hizmet uygulamaları özel ilke onaylamalarını hizmeti meta verilerde bitiş noktası, iletişim kurmak için kullanabileceğiniz istemci uygulamasına bağlama veya sözleşme özelleştirme bilgileri. Windows Communication Foundation (WCF) uç noktası, işlem veya özelliklerini veya iletişim kuran gereksinimleri bağlı olarak, ileti konuları WSDL bağlamalarda bağlı İlkesi ifadelerde onaylar dışarı aktarmak için kullanabilirsiniz.  
  
 Özel ilke onaylamalarını dışa aktarılır uygulayarak <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> üzerinde arabirim bir <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> ve hizmet uç noktası ya da bağlama öğesi uygulamanızda kaydetme bağlama doğrudan ya da bağlama öğesi ekleniyor yapılandırma dosyası. İlke verme uygulamanıza özel ilke değerinizi olarak eklemelisiniz bir <xref:System.Xml.XmlElement?displayProperty=nameWithType> uygun örneğine <xref:System.ServiceModel.Description.PolicyAssertionCollection?displayProperty=nameWithType> üzerinde <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> içine geçirilen <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> yöntemi.  
  
 Buna ek olarak işaretlemeniz gerekir <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> özelliği <xref:System.ServiceModel.Description.WsdlExporter> sınıfı ve iç içe geçmiş ilke ifadeleri ve ilke framework öznitelikleri doğru ad alanında belirtilen ilke sürümlerine göre dışarı aktarma.  
  
 Özel ilke onaylamalarını içe aktarmak için bkz: <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> ve [nasıl yapılır: özel ilke onaylamalarını içe](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md).  
  
### <a name="to-export-custom-policy-assertions"></a>Özel ilke onaylamalarını dışa aktarmak için  
  
1.  Uygulama <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> üzerinde arabirim bir <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>. Aşağıdaki kod örneğinde bir özel ilke onaylama bağlama düzeyinde uyarlamasını gösterir.  
  
     [!code-csharp[CustomPolicySample#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyexporter.cs#14)]
     [!code-vb[CustomPolicySample#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyexporter.vb#14)]  
  
2.  Bağlama öğesi ya da program aracılığıyla bağlama veya uygulama yapılandırma dosyası kullanarak uç nokta yerleştirin. Aşağıdaki yordamlara bakın.  
  
### <a name="to-insert-a-binding-element-using-an-application-configuration-file"></a>Uygulama yapılandırma dosyası kullanarak bir bağlama öğesi eklemek için  
  
1.  Uygulama <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType> özel ilke onaylama bağlama öğesi için.  
  
2.  Bağlama öğesi uzantısı yapılandırma dosyasını kullanarak eklemek [ \<bindingElementExtensions >](../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md) öğesi.  
  
3.  Özel bağlama kullanma yapı <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.  
  
### <a name="to-insert-a-binding-element-programmatically"></a>Program aracılığıyla bir bağlama öğesi eklemek için  
  
1.  Yeni bir <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> ve ekleyebilmek için bir <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.  
  
2.  Özel bağlama adım 1'den ekleyin. Yeni bir uç noktası için ve bu yeni hizmet uç noktasına ekleyin <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> çağırarak <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> yöntemi.  
  
3.  Açık <xref:System.ServiceModel.ServiceHost>. Aşağıdaki kod örneğinde, özel bağlama oluşturma ve bağlama öğelerinin programlama ekleme gösterir.  
  
     [!code-csharp[s_imperative#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_imperative/cs/service.cs#1)]
     [!code-vb[s_imperative#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_imperative/vb/service.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Description.IPolicyImportExtension>  
 <xref:System.ServiceModel.Description.IPolicyExportExtension>  
 [Nasıl yapılır: Özel İlke Onaylamalarını İçe Aktarma](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md)
