---
title: Sorgu Sonuçları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bcd7b699-4e50-4523-8c33-2f54a103d94e
ms.openlocfilehash: 70aa2ad6385ec4791b05b202dc5dc6d4fe9e57b9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="query-results"></a>Sorgu Sonuçları
Sonra bir [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorgu komut ağaçlarını dönüştürülür ve yürütülen, sorgu sonuçları genellikle aşağıdakilerden biri olarak döndürülür:  
  
-   Sıfır veya daha fazla belirtilmiş varlık nesnesi ya da projeksiyon, kavramsal modelde karmaşık türler koleksiyonu.  
  
-   Kavramsal model tarafından desteklenen CLR türleri.  
  
-   Satır içi koleksiyonları.  
  
-   Anonim türler.  
  
 Veri kaynağına karşı sorgu yürütüldü, sonuçları CLR türlerine gerçekleştirilip ve istemciye döndürülen. Tüm nesne materialization tarafından gerçekleştirilen [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Eşleştirilemez arasında kaynaklanan hataları [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] ve CLR nesnesi materialization sırasında durum için özel durumlar neden olur.  
  
 Sorgu yürütme ilkel kavramsal model türü döndürürse, tek başına ve kesilir CLR Türleri sonuçları oluşur [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Sorgu yazılan varlığın nesneler koleksiyonunu döndürürse, ancak tarafından temsil edilen <xref:System.Data.Objects.ObjectQuery%601>, bu türlerde nesne bağlamı tarafından izlenir. Tüm nesne davranışı (örneğin, alt/üst koleksiyonları, değişiklik izleme, çok biçimlilik ve benzeri) olan tanımlandığı şekilde [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Bu işlevsellik, kapasite tanımlandığı gibi kullanılabilir [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Daha fazla bilgi için bkz: [nesneleriyle çalışma](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md).  
  
 Struct türleri (örneğin, anonim türler ve null olabilir karmaşık türler) sorgularından döndürülen kullanılabilir `null` değeri. Bir <xref:System.Data.Objects.DataClasses.EntityCollection%601> döndürülen varlığı özelliği de kullanılabilir `null` değeri. Bu koleksiyon özelliği değil bir varlığın yansıtma sonuçlanabilir `null` arama gibi değeri <xref:System.Linq.Queryable.FirstOrDefault%2A> üzerinde bir <xref:System.Data.Objects.ObjectQuery%601> öğe sahip.  
  
 Bazı durumlarda, bir sorgu yürütmesi sırasında gerçekleştirilmiş sonucu oluşturmak için görünebilir ancak sorgu sunucuda yürütülür ve varlık nesnesi hiçbir zaman CLR gerçekleştirilip. Nesne materialization üzerinde yan etkileri bağlı olarak, bu sorunlara neden olabilir.  
  
 Aşağıdaki örnek, özel bir sınıf içerir `MyContact`, ile bir `LastName` özelliği. Zaman `LastName` özelliği ayarlanmış bir `count` değişkeni artar. İki aşağıdaki sorguları yürütün, ilk sorguyu artırır `count` ikinci sorguyu almayacak sırada. Bunun nedeni, ikinci sorgusunda `LastName` özelliği sonuçlarından öngörülen ve `MyContact` sınıfı hiçbir zaman oluşturulur, mağaza'sorguyu yürütmek için gerekli olmadığından.  
  
 [!code-csharp[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#materializationsideeffects)]
 [!code-vb[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#materializationsideeffects)]  
  
 [!code-csharp[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#mycontactclass)]
 [!code-vb[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#mycontactclass)]
