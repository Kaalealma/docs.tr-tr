---
title: 'Varlık veri modeli: devralma'
ms.date: 03/30/2017
ms.assetid: 42c7ef24-710a-4af9-8493-cd41c399ecb0
ms.openlocfilehash: c5c1b385ea72e48fd70ed5ec0cf8d1c42c1284e4
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="entity-data-model-inheritance"></a>Varlık veri modeli: devralma
Varlık veri modeli (EDM) için devralma destekleyen [varlık türleri](../../../../docs/framework/data/adonet/entity-type.md). EDM devralma nesne odaklı programlama dillerinde sınıfları için devralma benzer. Nesne odaklı dillerde sınıflarıyla kavramsal modelde bir varlık türü tanımlayabilirsiniz gibi (bir *türetilen türün*) başka bir varlık türünden devralan ( *temel türü*). Ancak, nesne odaklı programlama sınıflarında, kavramsal modelde türetilmiş bir tür her zaman tüm devralır [özellikleri](../../../../docs/framework/data/adonet/property.md) ve [Gezinti özellikleri](../../../../docs/framework/data/adonet/navigation-property.md) temel türü. Türetilmiş bir tür devralınan özelliklerinde geçersiz kılamaz.  
  
 Kavramsal modelde devralma Hiyerarşiler türetilmiş bir tür başka bir türetilmiş türden devralan oluşturabilirsiniz. (Türetilmiş bir tür değil hiyerarşideki bir türü) hiyerarşinin üstündeki türü olarak adlandırılır *kök türü*. Bir devralma hiyerarşisinde [Varlık anahtarı](../../../../docs/framework/data/adonet/entity-key.md) kök türünde tanımlanmış olması gerekir.  
  
 Devralma Hiyerarşiler türetilmiş bir tür birden fazla türünden devralan oluşturamaz. Örneğin, bir modeldeki kavramsal ile bir `Book` varlık türü, türetilmiş türler tanımlayabilirsiniz `FictionBook` ve `NonFictionBook` her öğesinden devralmalı `Book`. Ancak, daha sonra hem de devralan bir tür tanımlayabilirsiniz değil `FictionBook` ve `NonFictionBook` türleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki çizimde dört varlık türleriyle kavramsal model gösterir: `Book`, `FictionBook`, `Publisher`, ve `Author`. `FictionBook` Varlık türü olduğu kaynağından türetilmiş bir tür `Book` varlık türü. `FictionBook` Türü devralır `ISBN (Key)`, `Title`, ve `Revision` özelliklerini ve adlı bir ek özellik tanımlar `Genre`.  
  
 ![Devralma](../../../../docs/framework/data/adonet/media/inheritanceexample.gif "InheritanceExample")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için. Bir varlık türü aşağıdaki CSDL tanımlar `FictionBook`, devraldığı `Book` türü (örneğin, yukarıdaki diyagramda):  
  
 [!code-xml[EDM_Example_Model#DerivedType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books5.edmx#derivedtype)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
