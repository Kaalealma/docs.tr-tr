---
title: Veri tanımlama dili ile çalışma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec50083d-44f4-4093-9b23-5eacd601f96e
ms.openlocfilehash: c6b3151a95f949100e10e630da848e34ebbf1187
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="working-with-data-definition-language"></a>Veri tanımlama dili ile çalışma
İle başlayarak [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] sürüm 4, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] veri tanımlama dili (DDL) destekler. Bu, oluşturmak veya bağlantı dizesi ve depolama (SSDL) model meta verileri temel alan bir veritabanı örneği silmek sağlar.  
  
 Aşağıdaki yöntemlerden <xref:System.Data.Objects.ObjectContext> aşağıdakileri gerçekleştirmek için bağlantı dizesini ve SSDL içeriği kullanın: oluşturmak veya veritabanını silin, veritabanı var ve oluşturulan DDL komut görüntülemek olup olmadığını denetleyin:  
  
-   <xref:System.Data.Objects.ObjectContext.CreateDatabase%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.CreateDatabaseScript%2A>  
  
> [!NOTE]
>  DDL komutları yürütülürken yeterli izinlere varsayar.  
  
 Daha önce listelenen yöntemleri işlerin çoğunu alttaki ADO.NET veri sağlayıcı için temsilci. Veritabanı nesneleri oluşturmak için kullanılan adlandırma kuralı sorgulamak için kullanılan kuralları ile tutarlı olduğundan emin olmak için sağlayıcının sorumluluğundadır ve güncelleştirir.  
  
 Aşağıdaki örnek varolan modelini temel alan veritabanı oluşturmak nasıl gösterir. Ayrıca nesne bağlamı için yeni bir varlık nesnesi ekler ve veritabanına kaydeder.  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-define-a-database-based-on-the-existing-model"></a>Varolan modelini temel alan bir veritabanı tanımlamak için  
  
1.  Bir konsol uygulaması oluşturun.  
  
2.  Var olan bir model uygulamanıza ekleyin.  
  
    1.  Adlı boş bir model eklemek `SchoolModel`. Boş bir model oluşturmak için bkz: [nasıl yapılır: yeni .edmx dosyasının oluşturma](http://msdn.microsoft.com/library/beb8189e-e51c-4051-839c-9902c224abf2) konu.  
  
     SchoolModel.edmx dosyası projenize eklenir.  
  
    1.  Kavramsal, depolama kopyalayın ve içerik Okul modeli eşleme [Okul modeli](http://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac) konu.  
  
    2.  SchoolModel.edmx dosyasını açın ve içeriği içinde `edmx:Runtime` etiketler.  
  
3.  Ana işlevinizi aşağıdaki kodu ekleyin. Kod DDL komut dosyası bir veritabanı oluşturur, yeni bir varlık bağlamına ekler ve değişiklikleri veritabanına kaydeder görünümleri, veritabanı sunucusu ile bağlantı dizesi başlatır.  
  
     [!code-csharp[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/csharp/VS_Snippets_Data/DP ObjectServices Concepts/CS/Source.cs#ddl)]
     [!code-vb[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP ObjectServices Concepts/VB/Source.vb#ddl)]
