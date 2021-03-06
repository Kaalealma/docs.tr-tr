---
title: 'Nasıl yapılır: Birincil Birlikte Çalışma Derlemelerini Kaydetme'
ms.date: 03/30/2017
helpviewer_keywords:
- registering primary interop assemblies
- primary interop assemblies, registering
ms.assetid: 4b2fcf8a-429d-43ce-8334-e026040be8bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f54d77be130d57c39319e81d58ad5af7815e548
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-register-primary-interop-assemblies"></a>Nasıl yapılır: Birincil Birlikte Çalışma Derlemelerini Kaydetme
Sınıflar yalnızca COM birlikte çalışma tarafından sıralanabilir ve arabirimleri olarak her zaman hazırlanırlar. Bazı durumlarda sınıfı sıralama için kullanılan arabirim sınıf arabirimi olarak bilinir. Tercih ettiğiniz bir arabirim ile sınıf arabirimi geçersiz kılma hakkında daha fazla bilgi için bkz: [COM aranabilir sarmalayıcısı](../../../docs/framework/interop/com-callable-wrapper.md).  
  
 Bir .NET Framework uygulamasından COM türlerini kullanmak isteyen herhangi bir geliştirici birlikte çalışabilirlik bütünleştirilmiş oluşturabilirsiniz ancak bunu yaparsanız böylece bir sorun oluşturur. Her bir geliştirici alır ve geliştirici olanlar aktarılır ve başka bir geliştirici tarafından imzalandığı ile uyumsuz benzersiz türleri kümesi oluşturan bir COM tür kitaplığı imzalar. Her geliştirici satıcı tarafından sağlanan ve imzalanmış birincil birlikte çalışma derlemesi edinmek bu tür uyumsuzluğu sorunun çözümüdür.  
  
 Diğer uygulamalar için üçüncü taraf COM türlerini kullanıma planlıyorsanız, her zaman tanımladığı tür kitaplığı olarak aynı yayımcı tarafından sağlanan birincil birlikte çalışma derlemesi kullanın. Garantili türü uyumluluğunu sağlamanın yanı sıra, birincil birlikte çalışma derlemeleri genellikle birlikte çalışabilirlik geliştirmek için satıcı tarafından özelleştirilir.  
  
 Üçüncü taraf COM türlerini kullanıma planlıyor musunuz olsa bile, birincil birlikte çalışma derlemesi kullanarak COM bileşenleriyle birlikte görevini kolaylaştırabilir. Ancak, bu strateji bir satıcı birincil birlikte çalışma derlemesinde tanımlanan türler için yapabileceğiniz değişiklikleri hiçbir yalıtımı sağlar. Uygulamanız bu tür yalıtımı gerektirdiğinde, birincil birlikte çalışma derlemesi kullanmak yerine kendi birlikte çalışma derlemesi oluşturun.  
  
 Bunlarla başvuru önce tüm alınan birincil birlikte çalışma derlemeleri geliştirme bilgisayarınızda kaydetmeniz gerekir [!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)]. Visual Studio arar ve birincil birlikte çalışma derlemesi COM tür kitaplığından bir türe başvuruda ilk kez kullanır. Visual Studio türü Kitaplıkla ilişkilendirilmiş birincil birlikte çalışma derlemesi bulamazsanız, onu almanızı komut istemleri veya bir birlikte çalışma derlemesi yerine oluşturmak sunar. Benzer şekilde, [tür kitaplığı içeri Aktarıcı (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) kayıt defteri birincil birlikte çalışma derlemeleri bulmak için de kullanır.  
  
 Visual Studio kullanmayı düşünmüyorsanız birincil birlikte çalışma derlemeleri kaydetmek gerekli olmamasına karşın, kayıt iki avantajları sağlar:  
  
-   Kayıtlı bir birincil birlikte çalışma derlemesi özgün tür kitaplığı kayıt defteri anahtarında açıkça işaretlenmiştir. Kayıt, birincil birlikte çalışma derlemesi bilgisayarınızda bulmak en iyi yoludur.  
  
-   Yanlışlıkla oluşturma ve bazı zaman gelecekte bir kaydı birincil birlikte çalışma derlemesi sahip bir tür başvurmak için Visual Studio kullanıyorsanız, yeni bir birlikte çalışma derleme kullanarak önleyebilirsiniz.  
  
 Kullanım [derleme Kayıt Aracı (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) birincil birlikte çalışma derlemesi kaydetmek için.  
  
### <a name="to-register-a-primary-interop-assembly"></a>Birincil birlikte çalışma derlemesi kaydetmek için  
  
1.  Komut isteminde, şunları yazın:  
  
     **RegAsm** *assemblyname*  
  
     Bu komutta *assemblyname* kayıtlı derlemenin dosya adı. RegAsm.exe özgün tür kitaplığı olarak aynı kayıt defteri anahtarı altında birincil birlikte çalışma derlemesi için bir giriş ekler.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kaydeder `CompanyA.UtilLib.dll` birincil birlikte çalışma derlemesi.  
  
```console  
regasm CompanyA.UtilLib.dll  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Birincil birlikte çalışma derlemeleri ile programlama](https://msdn.microsoft.com/library/306fa1d6-0703-4004-9e93-d0a57f1be81e(v=vs.100))  
 [Birincil birlikte çalışma derlemeleri bulma](https://msdn.microsoft.com/library/d6768e4b-cd80-414d-a4f8-05d979eb393b(v=vs.100))  
 [Birincil birlikte çalışma derlemeleri yeniden dağıtma](https://msdn.microsoft.com/library/e76384f0-d631-474c-bdbd-13884cba0265(v=vs.100))
