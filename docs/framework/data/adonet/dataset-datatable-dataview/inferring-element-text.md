---
title: Öğe metni çıkarımını yapma
ms.date: 03/30/2017
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
ms.openlocfilehash: b32d8f3f89a16166ffc0e903ef1f63c3b97a249c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="inferring-element-text"></a>Öğe metni çıkarımını yapma
Bir öğenin metni içeren ve (öznitelikleri öğeleriyle) veya yinelenen öğeleri gibi yeni bir sütun adıyla tabloları gibi olayla için alt öğe varsa **TableName_Text** öğe için olayla tablosuna eklenir. Öğesinde bulunan metin tablosunda bir satırı eklenir ve yeni bir sütun depolanır. **ColumnMapping** yeni bir sütun özelliği, ayarlanacak **MappingType.SimpleContent**.  
  
 Örneğin, aşağıdaki XML göz önünde bulundurun.  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 Çıkarma işlemi adlı bir tablo oluşturur **Element1** iki sütunlarla: **attr1** ve **Element1_Text**. **ColumnMapping** özelliği **attr1** sütun ayarlanacak **MappingType.Attribute**. **ColumnMapping** özelliği **Element1_Text** sütun ayarlanacak **MappingType.SimpleContent**.  
  
 **Veri kümesi:** DocumentElement  
  
 **Tablo:** Element1  
  
|attr1|Element1_Text|  
|-----------|--------------------|  
|Değer1|Metin1|  
  
 Bir öğenin metni içeren, ancak Ayrıca metin içeren alt öğeleri varsa, bir sütun öğesinde yer metin depolamak için tabloya eklenmez. Alt öğeler metinde tablosunda bir satırı dahil ederken öğesinde yer metin yoksayılacak. Örneğin, aşağıdaki XML göz önünde bulundurun.  
  
```xml  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 Çıkarma işlemi adlı bir tablo oluşturur **Element1** adlı bir sütunu ile **ChildElement1**. Metni **ChildElement1** öğesi dahil edilir tabloda satırda. Başka bir metin göz ardı edilir. **ColumnMapping** özelliği **ChildElement1** sütun ayarlanacak **MappingType.Element**.  
  
 **Veri kümesi:** DocumentElement  
  
 **Tablo:** Element1  
  
|ChildElement1|  
|-------------------|  
|Metin2|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML’den DataSet İlişkisel Yapısını Çıkarma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [XML’den DataSet Yükleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [XML’den DataSet Schema Bilgilerini Yükleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [DataSet içinde XML kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
