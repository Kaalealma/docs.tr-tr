---
title: DataRelation ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
ms.openlocfilehash: 451ee0eee466efca86345ea7112e9b178a2c66e2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="adding-datarelations"></a>DataRelation ekleme
İçinde bir <xref:System.Data.DataSet> birden çok <xref:System.Data.DataTable> nesneleri kullanabileceğiniz <xref:System.Data.DataRelation> diğerine tabloları gidin ve bir ilişkili tablodan alt veya üst satır dönmek için bir tablo ilişkilendirmek için nesneleri.  
  
 Oluşturmak için gerekli bağımsız bir **DataRelation** için bir adı olan **DataRelation** oluşturulmasını ve bir dizi bir veya daha fazla <xref:System.Data.DataColumn> üst ve alt sütunun başvurular İlişki sütun. Oluşturduktan sonra bir **DataRelation**, tablolar arasında gezinmek için ve değerleri almak için kullanabilirsiniz.  
  
 Ekleme bir **DataRelation** için bir <xref:System.Data.DataSet> ekler, varsayılan olarak, bir <xref:System.Data.UniqueConstraint> üst tabloya ve <xref:System.Data.ForeignKeyConstraint> alt tabloya. Bu varsayılan kısıtlamaları hakkında daha fazla bilgi için bkz: [DataTable kısıtlamalarını](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).  
  
 Aşağıdaki kod örneği oluşturur bir **DataRelation** iki kullanarak <xref:System.Data.DataTable> nesnelerini bir <xref:System.Data.DataSet>. Her <xref:System.Data.DataTable> adlı bir sütun içeren **CustId**, ikisi arasında bir bağlantı gibi hizmet <xref:System.Data.DataTable> nesneleri. Tek bir örnek ekler **DataRelation** için **ilişkileri** koleksiyonu <xref:System.Data.DataSet>. Örnekteki ilk bağımsız değişkeni adını belirtir. **DataRelation** oluşturuluyor. İkinci bağımsız değişkeni üst ayarlar **DataColumn** ve üçüncü bağımsız değişken alt ayarlar **DataColumn**.  
  
```vb  
customerOrders.Relations.Add("CustOrders", _  
  customerOrders.Tables("Customers").Columns("CustID"), _  
  customerOrders.Tables("Orders").Columns("CustID"))  
```  
  
```csharp  
customerOrders.Relations.Add("CustOrders",  
  customerOrders.Tables["Customers"].Columns["CustID"],  
  customerOrders.Tables["Orders"].Columns["CustID"]);  
```  
  
 A **DataRelation** de sahip bir **iç içe** özelliği, ayarlandığında **doğru**, üst tablo ilişkili satırdaki iç içe alt tablodan satırları neden olur kullanarak XML öğeleri yazılırken <xref:System.Data.DataSet.WriteXml%2A> . Daha fazla bilgi için bkz: [XML kullanarak bir veri kümesinde](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
