---
title: 'Nasıl yapılır: sorgu seçeneklerini veri hizmeti sorguya (WCF Veri Hizmetleri) ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- querying the data service [WCF Data Services]
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: e4258526-557e-4e96-91e1-2175400c7c8f
ms.openlocfilehash: 330581c699ca4beede3333315844af084f27e672
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-query-options-to-a-data-service-query-wcf-data-services"></a>Nasıl yapılır: sorgu seçeneklerini veri hizmeti sorguya (WCF Veri Hizmetleri) ekleme
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Veri Hizmeti .NET Framework tabanlı istemci uygulamasından oluşturulan istemci veri hizmeti sınıflarını kullanarak sorgulama olanak tanır. İstenen sorgu seçeneklerini içeren bir dilde tümleşik sorgu (LINQ) sorgu ifadesi oluşturmak için bunu yapmanın en kolay yoludur. LINQ Sorgu yöntemleri eşdeğer bir sorgu oluşturmak için bir dizi ayrıca çağırabilirsiniz. Son olarak, kullanabileceğiniz <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> yöntemi sorgu seçeneklerini bir sorguya ekleyin. Her durumda, istemci tarafından oluşturulan URI uygulanan seçili sorgu seçenekleriyle istenen varlık kümesini içerir. Daha fazla bilgi için bkz: [veri hizmeti sorgulanırken](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 Bu konudaki örnek Northwind örnek veri hizmeti ve otomatik olarak oluşturulur istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları tamamladığınızda oluşturduğunuz [WCF Veri Hizmetleri quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, yalnızca birden fazla $30 nakliye maliyetini siparişler ve o siparişler sonuçları Sevk tarihine göre azalan sırada döndürür. bir LINQ sorgu ifadesi oluşturma gösterilmektedir.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinq](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionslinq)]
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinq](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionslinq)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, önceki sorgu eşdeğerdir LINQ Sorgu yöntemleri kullanarak LINQ sorgusu oluşturmak nasıl gösterir.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqExpression](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionslinqexpression)]
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinqExpression](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionslinqexpression)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek için nasıl kullanılacağını gösterir <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> yöntemi oluşturmak için bir <xref:System.Data.Services.Client.DataServiceQuery%601> yani önceki örneklerde eşdeğerdir.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptions)]
 [!code-vb[Astoria Northwind Client#AddQueryOptions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptions)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl kullanılacağını gösterir `$orderby` sorgu seçeneğine filtrelerin ve order nakliye özelliği tarafından siparişleri nesneleri döndürdü.  
  
 [!code-csharp[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#orderwithfilter)]
 [!code-vb[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#orderwithfilter)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Hizmetini Sorgulama](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
 [Nasıl Yapılır: Sorgu Sonuçlarını Yansıtma](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md)
