---
title: -win32manifest (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /win32manifest
helpviewer_keywords:
- /win32manifest compiler option [C#]
- win32manifest compiler option [C#]
- -win32manifest compiler option [C#]
ms.assetid: 9460ea1b-6c9f-44b8-8f73-301b30a01de1
ms.openlocfilehash: 3ac2b60b5e638290ea7e17e539519e3a0d355c12
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="-win32manifest-c-compiler-options"></a>-win32manifest (C# Derleyici Seçenekleri)
Kullanım **-win32manifest** seçeneği bir projenin taşınabilir yürütülebilir (PE) dosyasına katıştırılmış bir kullanıcı tarafından tanımlanan Win32 uygulama bildirim dosyası belirtin.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-win32manifest: filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Özel bildirim dosyasının konumunu ve adını.  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, Visual C# Derleyici "asInvoker." istenen yürütme düzeyini belirten bir uygulama bildirimi katıştırır. Hangi yürütülebilir yapılandırıldığında, genellikle bin\Debug veya bin\Release klasörü, Visual Studio kullandığınızda aynı klasörde bildirimi oluşturur. Örneğin "highestAvailable" veya "requireAdministrator" istenen yürütme düzeyini belirtmek özel bir bildirimi sağlamak istiyorsanız, dosya adını belirtmek için bu seçeneği kullanın.  
  
> [!NOTE]
>  Bu seçenek ve [-win32res (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) seçeneği karşılıklı olarak birbirini dışlar. Her iki seçenek aynı komut satırında kullanmaya çalışırsa, bir derleme hatası alırsınız.  
  
 Hiçbir uygulama bildirimini olan bir uygulama, istenen yürütme düzeyinin Windows kullanıcı hesabı denetimi özelliği altında dosya/kayıt defteri sanallaştırma tabi olacağını belirtir. Daha fazla bilgi için bkz: [kullanıcı hesabı denetimi](/windows/access-protection/user-account-control/user-account-control-overview).  
  
 Bu koşulların doğru ise, uygulama sanallaştırma tabi olacaktır:  
  
-   Kullandığınız **-nowin32manifest** seçeneğini sağlamaz daha yeni bir derleme adımı veya Windows Kaynak (.res) dosyasının bir parçası olarak bir bildirim kullanarak **-win32res** seçeneği.  
  
-   İstenen yürütme düzeyinin belirtmiyor özel bir bildirim sağlar.  
  
 Visual Studio varsayılan .manifest dosyası oluşturur ve yürütülebilir dosyanın yanında hata ayıklama ve yayın dizinleri depolar. Özel bir bildirimi, aşağıdakilerden herhangi bir metin düzenleyicisinde oluşturarak ve ardından dosyayı projeye ekleyerek ekleyebilirsiniz. Alternatif olarak, sağ tıklayarak **proje** simgesine **Çözüm Gezgini**, tıklatın **Yeni Öğe Ekle**ve ardından **uygulama bildirim dosyası**. Yeni veya varolan bildirim dosyanızı ekledikten sonra görüneceği **bildirim** açılan liste. Daha fazla bilgi için bkz: [uygulama sayfası, Proje Tasarımcısı (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).  
  
 Kullanarak oluşturma sonrası özel bir adım veya Win32 kaynak dosyasını bir parçası olarak uygulama bildirimini sağlayabilirsiniz [-nowin32manifest (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md) seçeneği. Uygulamanızın Windows Vista dosya veya kayıt defteri sanallaştırma tabi olmasını istiyorsanız aynı seçeneği kullanın. Bu oluşturma ve taşınabilir yürütülebilir (PE) dosyasında varsayılan bildirim katıştırma derleyici engeller.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Visual C# Derleyici bir PE'ye eklediği varsayılan bildirimi gösterir.  
  
> [!NOTE]
>  Derleyici standart uygulama adı "MyApplication.app şeklinde" xml öğesine ekler. Bu, uygulamaların Windows Server 2003 Service Pack 3 üzerinde çalışmasını etkinleştirmek için bir çözüm olabilir.  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
  <assemblyIdentity version="1.0.0.0" name="MyApplication.app"/>  
  <trustInfo xmlns="urn:schemas-microsoft-com:asm.v2">  
    <security>  
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">  
        <requestedExecutionLevel level="asInvoker"/>  
      </requestedPrivileges>  
    </security>  
  </trustInfo>  
</assembly>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [-nowin32manifest (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md)  
 [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
