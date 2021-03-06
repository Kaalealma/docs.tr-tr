---
title: LINQ to SQL sorguları
ms.date: 03/30/2017
ms.assetid: f4897aaa-7f44-4c20-a471-b948c2971aae
ms.openlocfilehash: ef761f696eaefd6daef9a32892e4c5356a178418
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="linq-to-sql-queries"></a>LINQ to SQL sorguları
Tanımladığınız [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yaptığınız gibi aynı sözdizimini kullanarak sorguları [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]. Tek fark, sorguda başvurulan nesneler bir veritabanında öğelerine eşlenir olmasıdır. Daha fazla bilgi için bkz: [LINQ sorgularını (C#) giriş](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] eşdeğer SQL sorguları yazma sorguları çevirir ve işlem sunucusuna gönderir. Daha açık belirtmek gerekirse, uygulamanızın kullandığı [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] API isteği sorgu yürütme için. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Sağlayıcısı sonra sorguyu SQL metne dönüştürür ve ADO sağlayıcısına yürütme atar. Sorgu sonuçları olarak ADO sağlayıcının döndürdüğü bir `DataReader`. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Sağlayıcı çevirir ADO sonuçları bir <xref:System.Linq.IQueryable> kullanıcı nesneleri topluluğu.  
  
> [!NOTE]
>  Birçok yöntem ve işleçlerini [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] yerleşik türleri SQL doğrudan çevirileri sahiptir. Bu, [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] çeviremez çalışma zamanı özel durumları oluşturur. Daha fazla bilgi için bkz: [SQL CLR türü eşleme](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
 Aşağıdaki tabloda benzerlik gösterir ve arasındaki farklar [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgu öğeleri.  
  
|Öğe|LINQ sorgusu|[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Sorgu|  
|----------|----------------|----------------------------------------------------------------------|  
|Sorgu (için dizileri döndüren sorgular) tutan yerel değişken dönüş türü|Genel `IEnumerable`|Genel `IQueryable`|  
|Veri kaynağını belirtme|Kullanan `From` (Visual Basic) veya `from` yan tümcesi (C#)|Aynı|  
|Filtreleme|Kullanan `Where` / `where` yan tümcesi|Aynı|  
|Gruplandırma|Kullanan `Group…By` / `groupby` yan tümcesi|Aynı|  
|(Yansıtma) seçme|Kullanan `Select` / `select` yan tümcesi|Aynı|  
|Hemen bir yürütme karşı ertelenmiş|Bkz: [giriş LINQ sorgularını (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)|Aynı|  
|Birleştirmeler uygulama|Kullanan `Join` / `join` yan tümcesi|Kullanabileceğiniz `Join` / `join` yan tümcesi, ancak daha etkili bir şekilde kullanır <xref:System.Data.Linq.Mapping.AssociationAttribute> özniteliği. Daha fazla bilgi için bkz: [sorgulama arasında ilişkiler](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md).|  
|Uzaktan yerel yürütme karşılaştırması||Daha fazla bilgi için bkz: [uzak vs. Yerel yürütme](../../../../../../docs/framework/data/adonet/sql/linq/remote-vs-local-execution.md).|  
|Önbelleğe alınan sorgulama karşı akış|Bir yerel bellek senaryosunda geçerli değil||  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Giriş LINQ sorgularını (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 [Temel LINQ Sorgu İşlemleri](~/docs/csharp/programming-guide/concepts/linq/basic-linq-query-operations.md)  
 [LINQ Sorgu İşlemlerinde Tür İlişkileri](~/docs/csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)  
 [Sorgu Kavramları](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
