---
title: 'Nasıl yapılır: birden çok sonuç şekiller için eşlenen saklı yordamları kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2b84dfe-7fec-489a-92de-45215cec4518
ms.openlocfilehash: 03a003bd5b09ae19b01dcc9880137661ba6fccae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-stored-procedures-mapped-for-multiple-result-shapes"></a>Nasıl yapılır: birden çok sonuç şekiller için eşlenen saklı yordamları kullanma
Saklı yordam birden çok sonuç şekil döndüğünüzde dönüş türü tek projeksiyon şekle kesin türü belirtilmiş olamaz. Ancak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tüm olası projeksiyon türlerinizi oluşturabilirsiniz, içinde bunlar döndürüleceği sipariş bilemezsiniz.  
  
 Bu senaryo birden çok sonuç şekil sırayla üretmek saklı yordamlar ile karşılaştırın. Daha fazla bilgi için bkz: [nasıl yapılır: kullanım depolanan yordamları eşlenen sıralı sonuç şekilleri](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md).  
  
 <xref:System.Data.Linq.Mapping.ResultTypeAttribute> Özniteliği yordamı dönebilirsiniz türleri kümesini belirtmek için birden çok sonuç türleri döndüren saklı yordamları uygulanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki SQL kod örneğinde, giriş, sonuç şekli bağlıdır (`shape =1` veya `shape = 2`). Hangi projeksiyon ilk döndürülecek bilmezsiniz.  
  
```  
CREATE PROCEDURE VariableResultShapes(@shape int)  
AS  
if(@shape = 1)  
    select CustomerID, ContactTitle, CompanyName from customers  
else if(@shape = 2)  
    select OrderID, ShipName from orders  
```  
  
 [!code-csharp[DLinqSprox#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#4)]
 [!code-vb[DLinqSprox#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#4)]  
  
## <a name="example"></a>Örnek  
 Bu saklı yordamı yürütmek için aşağıdakine benzer bir kod kullanırsınız.  
  
> [!NOTE]
>  Kullanmalısınız <xref:System.Data.Linq.IMultipleResults.GetResult%2A> , saklı yordam bilgisini temel alarak doğru türde bir numaralandırıcı almak için desen.  
  
 [!code-csharp[DLinqSprox#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#5)]
 [!code-vb[DLinqSprox#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Saklı Yordamlar](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
