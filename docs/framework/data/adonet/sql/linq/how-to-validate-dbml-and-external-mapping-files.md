---
title: 'Nasıl yapılır: DBML ve dış eşleme dosyaları doğrula'
ms.date: 03/30/2017
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
ms.openlocfilehash: 9bf21353aebd0ae57c51b2ddf3b31b5e7f1ac615
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-validate-dbml-and-external-mapping-files"></a>Nasıl yapılır: DBML ve dış eşleme dosyaları doğrula
Dış eşleme dosyaları ve değiştirmeniz .dbml dosyaları ilgili şema tanımlarını karşı doğrulanmalıdır. Bu konu, doğrulama işlemini uygulamak için Visual Studio kullanıcılarla adımları sağlar.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
### <a name="to-validate-a-dbml-or-xml-file"></a>.Dbml veya XML dosyasını doğrulamak için  
  
1.  Visual Studio üzerinde **dosya** menüsündeki **açık**ve ardından **dosya**.  
  
2.  İçinde **Dosya Aç** iletişim kutusunda, .dbml veya doğrulamak istediğiniz XML eşleme dosyası'ı tıklatın.  
  
     Dosya açılır **XML Düzenleyicisi**.  
  
3.  Pencerenin sağ tıklayın ve ardından **özellikleri**.  
  
4.  İçinde **özellikleri** penceresinde için üç nokta düğmesine **şemaları** özelliği.  
  
     **XML şemaları** iletişim kutusu açılır.  
  
5.  Amacınıza uygun şema tanımı unutmayın.  
  
    -   DbmlSchema.xsd .dbml dosyası doğrulanıyor şema tanımıdır. Daha fazla bilgi için bkz: [LINQ-SQL kod oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).  
  
    -   LinqToSqlMapping.xsd dış XML eşleme dosyası doğrulama şema tanımı ' dir. Daha fazla bilgi için bkz: [dış eşleme](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
6.  İçinde **kullanım** istenen şema tanımı satır açılır kutusunu açın ve ardından tıklatıp sütunu **Bu şemayı kullanan**.  
  
     Şema tanımı, DBML ile ilişkili artık veya dosya eşleme XML dosyasıdır.  
  
     Başka bir şema tanımları seçili olduğundan emin olun.  
  
7.  Üzerinde **Görünüm** menüsünde tıklatın **hata listesi**.  
  
     Hataları, uyarıları veya iletileri oluşturulmuş olup olmadığını belirler. Aksi durumda, şema tanımına göre geçerli XML dosyasıdır.  
  
## <a name="alternate-method-for-supplying-schema-definition"></a>Şema tanımı sağlama için alternatif yöntemi  
 Bazı nedenlerle uygun .xsd içinde dosya görünmüyorsa **XML şemaları** iletişim kutusu, bir Yardım konusunun .xsd dosyası indirebilirsiniz. Aşağıdaki adımlar, Visual Studio XML Düzenleyicisi tarafından gerekli Unicode biçiminde indirilen dosya kaydetmenize yardımcı.  
  
#### <a name="to-copy-a-schema-definition-file-from-a-help-topic"></a>Bir şema tanımı dosyası bir Yardım konusunun kopyalamak için  
  
1.  Bu konunun önceki kısımlarında açıklandığı gibi şema tanımını içerdiğinden Yardım konusunu bulun.  
  
    -   .DBML dosyalar için bkz: [LINQ-SQL kod oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).  
  
    -   Dış eşleme dosyalar için bkz: [dış eşleme](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
2.  Tıklatın **kod Kopyala** kod dosyası panoya kopyalamak için.  
  
3.  Yeni bir dosya oluşturmak için Not Defteri'ni başlatın.  
  
4.  Panodaki kodu Not Defteri dosyaya yapıştırın.  
  
5.  Not Defteri'ni üzerinde **dosya** menüsünde tıklatın **Kaydet**.  
  
6.  İçinde **kodlama** kutusunda **Unicode**.  
  
    > [!IMPORTANT]
    >  Bu seçim, Unicode 16 bayt sırası işaret güvence altına alır (`FFFE`) metin dosyasına eklenir.  
  
7.  İçinde **dosya adı** kutusunda, .xsd uzantılı bir dosya adı oluşturun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başvuru](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
