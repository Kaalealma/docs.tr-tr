---
title: yabancı anahtar özelliği
ms.date: 03/30/2017
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
ms.openlocfilehash: 5a00c4d4cc469f5c816b8173843d283d63ccf308
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="foreign-key-property"></a>yabancı anahtar özelliği
A *yabancı anahtar özellik* varlık veri modeli (EDM) basit tür olan [özelliği](../../../../docs/framework/data/adonet/property.md) (veya ilkel tür özellikleri kümesi) üzerinde bir [varlık türü](../../../../docs/framework/data/adonet/entity-type.md) içeren[Varlık anahtarı](../../../../docs/framework/data/adonet/entity-key.md) başka bir varlık türü.  
  
 Bir yabancı anahtar özellik, ilişkisel bir veritabanındaki yabancı anahtar sütununa benzer. Yabancı anahtar sütunları ilişkisel bir veritabanında tablolarda satırları arasındaki ilişkileri oluşturmak için kullanılır aynı şekilde kavramsal model yabancı anahtar özellikleri oluşturmak için kullanılan [ilişkilendirmeleri](../../../../docs/framework/data/adonet/association-type.md) varlık türleri arasındaki. A [başvuru bütünlüğü kısıtlaması](../../../../docs/framework/data/adonet/referential-integrity-constraint.md) türlerinden birini yabancı anahtar özelliğine sahip iki varlık türleri arasındaki ilişkiyi tanımlamak için kullanılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki diyagram üç varlık türleriyle kavramsal model gösterir: `Book`, `Publisher`, ve `Author`. `Book` Varlık türüne sahip bir özellik `PublisherId`, varlık anahtarı başvuran `Publisher` bir başvuru bütünlüğü kısıtlaması tanımlarken varlık türü `PublishedBy` ilişkilendirme.  
  
 ![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Yabancı anahtar özelliği aşağıdaki CSDL kullanan `PublisherId` bir başvuru bütünlüğü kısıtlaması tanımlamak için `PublishedBy` yukarıda gösterilen kavramsal modelde gösterilen ilişkilendirme.  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
