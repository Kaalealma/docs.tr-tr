---
title: 'Nasıl yapılır: ilgili varlıklar (WCF Veri Hizmetleri) yükleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: 6f143d30-d997-4e6b-bcf0-d5c394ecb108
ms.openlocfilehash: f7aa13ac217d86be23d0957ddb6c069831cacd2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-load-related-entities-wcf-data-services"></a>Nasıl yapılır: ilgili varlıklar (WCF Veri Hizmetleri) yükleme
İlişkili varlıklarda yüklemek gerektiğinde [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], kullanabileceğiniz <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> yöntemi <xref:System.Data.Services.Client.DataServiceContext> sınıfı. Aynı zamanda <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> yöntemi <xref:System.Data.Services.Client.DataServiceQuery%601> ilgili varlıklar aynı sorgu yanıtında isteğini önleyebiliriz yüklenmesi gerektirecek şekilde.  
  
 Bu konudaki örnek Northwind örnek veri hizmeti ve otomatik olarak oluşturulur istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları tamamladığınızda oluşturduğunuz [WCF Veri Hizmetleri quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, açıkça yüklemek gösterilmiştir `Customer` , ilgili döndürülen her `Orders` örneği.  
  
 [!code-csharp[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#loadrelatedordercustomer)]
 [!code-vb[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#loadrelatedordercustomer)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl kullanılacağını gösterir <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> döndürülecek yöntemi `Order Details` , ait `Orders` sorgu tarafından döndürülen.  
  
 [!code-csharp[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#expandorderdetails)]
 [!code-vb[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#expandorderdetails)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Hizmetini Sorgulama](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
