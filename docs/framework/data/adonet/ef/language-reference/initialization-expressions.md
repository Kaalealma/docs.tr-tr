---
title: Başlatma ifadeleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98daef1f-15d4-483e-985c-d78ea3abe8c8
ms.openlocfilehash: 352bda826c3b872d06252e168abfb1129f178bf8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="initialization-expressions"></a>Başlatma ifadeleri
Başlatma ifade yeni bir nesne başlatır. Çoğu yeni C# 3.0 ve Visual Basic 9.0 başlatma ifadeleri de dahil olmak üzere çoğu başlatma ifadeleri desteklenir. Aşağıdaki türler başlatıldı ve varlıkları sorgu için bir LINQ tarafından döndürülen:  
  
-   Sıfır veya daha fazla belirtilmiş varlık nesnesi ya da projeksiyon, kavramsal modelde tanımlanan karmaşık türler koleksiyonu.  
  
-   CLR türleri tarafından desteklenen [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].  
  
-   Satır içi koleksiyonları.  
  
-   Anonim türler.  
  
 Anonim tür başlatma sorgu ifade sözdizimi aşağıdaki örnekte gösterilmiştir:  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization)]  
  
 Yöntem temelli sorgu söz dizimi aşağıdaki örnekte anonim tür başlatma gösterir:  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization_mq)]  
  
 Kullanıcı tanımlı sınıfı başlatma de desteklenir. C# 3.0 ve Visual Basic 9.0 başlatma düzeni desteklenir ve özellik Set'yordamı simetrik olduğunu varsayar. Sorgu ifade sözdizimi aşağıdaki örnekte sorguda başlatılmakta özel bir sınıf gösterir:  
  
 [!code-csharp[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myorder)]
 [!code-vb[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myorder)]  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization)]  
  
 Yöntem temelli sorgu söz dizimi aşağıdaki örnekte sorguda başlatılmakta özel bir sınıf gösterir:  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization_mq)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to Entities Sorgu İfadeleri](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
