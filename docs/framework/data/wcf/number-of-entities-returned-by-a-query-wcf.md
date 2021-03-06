---
title: 'Nasıl yapılır: sorgu (WCF Veri Hizmetleri) tarafından döndürülen varlıkları sayısını belirlemek'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, row count
ms.assetid: 03d41a82-df95-40ac-8439-a6c327d37ba8
ms.openlocfilehash: 183fed2d267fc16767c902cdd69513aa9986ff78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-determine-the-number-of-entities-returned-by-a-query-wcf-data-services"></a>Nasıl yapılır: sorgu (WCF Veri Hizmetleri) tarafından döndürülen varlıkları sayısını belirlemek
İle [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], varlık kümesi URI sorgu tarafından belirtilen bulunan varlıkların sayısını belirleyebilirsiniz. Bu sayı, sorgu sonucu birlikte ya da bir tamsayı değeri olarak eklenebilir. Daha fazla bilgi için bkz: [veri hizmeti sorgulanırken](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 Bu konudaki örnek Northwind örnek veri hizmeti ve otomatik olarak oluşturulur istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları tamamladığınızda oluşturduğunuz [WCF Veri Hizmetleri quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Örnek  
 Bu örnek bir sorgu çağrıldıktan sonra yürütür <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> yöntemi. <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> Özelliği döndürür içindeki varlıkların sayısı `Customers` varlık kümesi.  
  
 [!code-csharp[Astoria Northwind Client#CountAllCustomers](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#countallcustomers)]
 [!code-vb[Astoria Northwind Client#CountAllCustomers](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#countallcustomers)]  
  
## <a name="example"></a>Örnek  
 Bu örnek çağırır <xref:System.Linq.Enumerable.Count%2A> yöntemi yalnızca bir tamsayı döndürülmesini değeri içindeki varlıkların sayısı `Customers` varlık kümesi.  
  
 [!code-csharp[Astoria Northwind Client#CountAllCustomersValueOnly](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#countallcustomersvalueonly)]
 [!code-vb[Astoria Northwind Client#CountAllCustomersValueOnly](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#countallcustomersvalueonly)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Hizmetini Sorgulama](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
