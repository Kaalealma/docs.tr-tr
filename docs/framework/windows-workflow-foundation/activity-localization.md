---
title: Etkinlik yerelleştirme
ms.date: 03/30/2017
ms.assetid: 8ee7bc16-e609-469a-a3e8-8062952e2676
ms.openlocfilehash: 23a6d5c2ed202f030397eb70382896468a68a724
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="activity-localization"></a>Etkinlik yerelleştirme
İş akışı uygulamaları ve bileşenleri diğer kültürlere ve dilleri yerelleştirilmiş olma olasılığı varsa, böylece derlemeden yerelleştirilebilir kaynak dizeleri kullanılmalıdır.  
  
## <a name="activity-localization"></a>Etkinlik yerelleştirme  
 Olarak (farklı dillere ve kültürlere için farklı sürümleri de serbest), yerelleştirilmiş olmalıdır tüm uygulamalarla kullanıcıya görüntülenen herhangi bir dizgi değil doğrudan kodunda put, ancak yerine bir kaynak dosyasında depolanır. Dizeler ardından aracılığıyla erişilebilir <!--zz <xref:System.Environment.GetResourceString> --> `GetResourceString`. Çeşitli dillerde dağıtılmış bir bileşen geliştiriyorsanız, aynı zamanda etkinlik doğrulama iletileri için kullanıcı tanımlı veri, izleme iletileri ve hata iletileri izleme kaynak dizeleri kullanmak istediğiniz.  
  
 Aşağıdaki alıştırmada bir kaynak dosyasının nasıl kullanılacağını gösterir.  
  
#### <a name="using-resource-files-for-localized-strings"></a>Yerelleştirilmiş dizeleri için kaynak dosyalarını kullanma  
  
1.  İçinde [!INCLUDE[vs2010](../../../includes/vs2010-md.md)], projenize sağ **Çözüm Gezgini** seçip **Ekle...** , **Yeni öğe...** .  
  
2.  Seçin **kaynakları dosya** ve ErrorResources.resx dosya adı. **Ekle**'yi tıklatın.  
  
3.  Kaynak dosyasını açın. Yeni bir girdi ile eklemek bir **adı** ErrorString ve bir **değeri** "etkinliği geçerli değil.",  
  
4.  Aşağıdakileri ekleyin `using` deyimleri sınıfınıza.  
  
    ```  
    using System.Reflection;  
    using System.Resources;  
    ```  
  
5.  Bir kaynak yöneticisi projenizde oluşturun.  
  
    ```  
    ResourceManager ErrorManager;  
    ...  
    ErrorManager = new ResourceManager("MyNamespace.ErrorResources", Assembly.GetExecutingAssembly());  
    ```  
  
6.  Dize, gerekli olduğu Kaynak Yöneticisi'nden alın.  
  
    ```  
    String errorMessage = ErrorManager.GetString("ErrorString");  
    ```  
  
 Aşağıdaki kod örneği, yerelleştirilmiş dizeleri kullanmak gösterilmiştir <xref:System.Activities.Activity.CacheMetadata%2A> yöntemi.  
  
```  
       protected override void CacheMetadata(CodeActivityMetadata metadata)  
        {  
           .....  
          // rest of the code elided for brevity  
           .....  
            if (this.Value != null && this.To != null)  
            {  
                if (!TypeHelper.AreTypesCompatible(this.Value.ArgumentType, this.To.ArgumentType))  
                {  
//---------------------------------------------  
// ** SR.TypeMismatchForAssign will fetch the string from the resource manager **  
//---------------------------------------------  
                    metadata.AddValidationError(SR.TypeMismatchForAssign(  
                                this.Value.ArgumentType,  
                                this.To.ArgumentType,  
                                this.DisplayName));  
                }  
            }  
        }  
```
