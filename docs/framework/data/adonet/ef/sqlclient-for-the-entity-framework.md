---
title: Entity Framework SqlClient
ms.date: 03/30/2017
ms.assetid: 9a5d6d39-d955-43a5-a5c2-931c239398f1
ms.openlocfilehash: 159cada00c523a1b417f5c6f4d0fac43a80f5db9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="sqlclient-for-the-entity-framework"></a>Entity Framework SqlClient
Bu bölümde, .NET Framework veri sağlayıcısı için SQL Microsoft SQL Server üzerinde çalışmak Entity Framework sağlayan Server (SqlClient) açıklanmaktadır.  
  
## <a name="provider-schema-attribute"></a>Sağlayıcı şema özniteliği  
 `Provider` bir özniteliği olan `Schema` depo şeması tanım dili (SSDL) öğe.  
  
 SqlClient kullanmak için "System.Data.SqlClient" dizesi atamak `Provider` özniteliği `Schema` öğesi.  
  
## <a name="providermanifesttoken-schema-attribute"></a>ProviderManifestToken şema özniteliği  
 `ProviderManifestToken` gerekli bir özniteliği olan `Schema` SSDL öğesinde. Bu belirteç sağlayıcısı bildirimi çevrimdışı senaryolar için yüklemek için kullanılır. Hakkında daha fazla bilgi için `ProviderManifestToken` özniteliği için bkz: [şema öğesi (SSDL)](http://msdn.microsoft.com/library/fec75ae4-7f16-4421-9265-9dac61509222).  
  
 SqlClient veri sağlayıcısı olarak SQL Server'ın farklı sürümleri için kullanılabilir. Bu sürümleri farklı özelliklere sahiptir. Örneğin, [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)] desteklemediği `varchar(max)` ve `nvarchar(max)` ile sunulan türleri [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)].  
  
 SqlClient üretir ve SQL Server'ın farklı sürümleri için aşağıdaki sağlayıcı bildirim belirteci kabul eder.  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|-|-|-|  
|2000|2005|2008|  
  
> [!NOTE]
>  Visual Studio 2010 ile başlayan [ADO.NET varlık veri modeli Araçları](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527) SQL Server 2000 desteklemez.  
  
## <a name="provider-namespace-name"></a>Sağlayıcı Namespace adı  
 Tüm sağlayıcılar bir ad belirtmeniz gerekir. Bu özellik, hangi önekin türler ve işlevler gibi belirli yapıları için sağlayıcı tarafından kullanılan Entity Framework söyler. Ad alanı SqlClient sağlayıcısı bildirimleri için `SqlServer`. Ad alanları hakkında daha fazla bilgi için bkz: [ad alanları](../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md).  
  
## <a name="types"></a>Türler  
 SqlClient sağlayıcısı Entity Framework için kavramsal model türleri ve SQL Server türleri arasında eşleme bilgilerini sağlar. Daha fazla bilgi için bkz: [varlık FrameworkTypes SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).  
  
## <a name="functions"></a>İşlevler  
 SqlClient sağlayıcısı için Entity Framework sağlayıcı tarafından desteklenen işlevleri listesini tanımlar. Desteklenen işlevlerin bir listesi için bkz: [SqlClient Entity Framework işlevleri için](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Entity Framework için SqlClient İşlevleri](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)  
  
 [Entity FrameworkTypes için SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md)  
  
 [Entity Framework için SqlClient’ta Bilinen Sorunlar](../../../../../docs/framework/data/adonet/ef/known-issues-in-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Dili](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)  
 [Dil Başvurusu](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)  
 [Bilinen sorunlar Entity Framework SqlClient Sağlayıcısı'nda](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)
