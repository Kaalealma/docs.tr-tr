---
title: LINQ-SQL güvenlik
ms.date: 03/30/2017
ms.assetid: d49787f7-414e-4c71-aa33-80a5895536b1
ms.openlocfilehash: b2c7de75295722da643d64ff22bc769e0633629d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="security-in-linq-to-sql"></a>LINQ-SQL güvenlik
Güvenlik riskleri, her zaman bir veritabanına bağlandığında yok. LINQ-SQL SQL Server'daki verilerle çalışmak için bazı yeni yollarını içerebilir ancak herhangi bir ek güvenlik mekanizması sağlamaz.  
  
## <a name="access-control-and-authentication"></a>Erişim denetimi ve kimlik doğrulama  
 LINQ-SQL, kendi kullanıcı model veya kimlik doğrulama mekanizmaları yok. Veritabanı, veritabanı tabloları, görünümleri ve nesne modeline eşlenen saklı yordamlar erişimi denetlemek için SQL Server güvenlik kullanın. Kullanıcılar için gereken en düşük erişim ve güçlü parolalar için kullanıcı kimlik doğrulaması gerektirir.  
  
## <a name="mapping-and-schema-information"></a>Eşleme ve şema bilgileri  
 Nesne modeli veya dış eşleme dosyası SQL CLR türü eşleme ve veritabanı şeması bilgileri dosya sistemindeki tüm bu dosyalara erişimi için kullanılabilir. Şema bilgileri nesne modeli veya dış eşleme dosyası erişebilen tüm kullanılabilir olacağını düşünün. Şema bilgileri için daha yaygın erişimi engellemek için kaynak dosyaları ve eşleme dosyaları korumak için dosya güvenlik mekanizmaları kullanın.  
  
## <a name="connection-strings"></a>Bağlantı dizeleri  
 Bağlantı dizeleri parolaları kullanmanızı mümkün olduğunca kaçınılmalıdır. Yalnızca bir bağlantı dizesi, kendi içinde bir güvenlik riski oluşturur, ancak bağlantı dizesini de düz metin olarak nesne modeli ya da dış eşleme dosyası Nesne İlişkisel Tasarımcısı veya SQLMetal komut satırı aracını kullanırken eklenebilir. (Bu bağlantı dizesinde varsa) nesne modeli veya dış eşleme dosyası dosya sistemi üzerinden erişimi olan herkes bağlantı parolası görebilir.  
  
 Bu tür riskleri en aza indirmek için tümleşik güvenlik SQL Server ile güvenilir bağlantı yapmak için kullanın. Bu yaklaşımı kullanarak, bir parola bağlantı dizesinde depolamak gerekmez. Daha fazla bilgi için bkz: [SQL Server Güvenlik](../../../../../../docs/framework/data/adonet/sql/sql-server-security.md).  
  
 Tümleşik güvenlik olmaması durumunda bir düz metin parola bağlantı dizesinde gerekir. Artan düzende risk, bağlantı dizenizi güvenli hale getirmek için en iyi yolu aşağıdaki gibidir:  
  
-   Tümleşik güvenlik kullanın.  
  
-   Bağlantı dizeleri parolalarla güvenli ve bağlantı dizeleri geçici geçirme en aza.  
  
-   Kullanım bir <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> Etkilenme süresini sınırlar bu yana bir bağlantı dizesi yerine sınıfı. LINQ-SQL <xref:System.Data.Linq.DataContext?displayProperty=nameWithType> sınıfı kullanılarak oluşturulabilir bir <xref:System.Data.SqlClient.SqlConnection>.  
  
-   Yaşam süresi en aza indirmek ve noktaya tüm bağlantı dizeleri için dokunun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [Sık Sorulan Sorular](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md)
