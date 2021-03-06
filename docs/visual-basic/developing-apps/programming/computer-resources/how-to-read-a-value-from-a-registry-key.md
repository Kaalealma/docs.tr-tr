---
title: "Nasıl Yapılır: Visual Basic'te Kayıt Defteri Anahtarından Değer Okuma"
ms.date: 07/20/2015
helpviewer_keywords:
- registry keys [Visual Basic], determining if a value exists in
- My.Computer.Registry object, examples
- registry [Visual Basic], determining if values exist
- registry keys [Visual Basic], reading from
- registry [Visual Basic], reading
ms.assetid: 775d0a57-68c9-464e-8949-9a39bd29cc64
ms.openlocfilehash: 645ec80124a23ac86a06993bd4e06b59372a6d1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-read-a-value-from-a-registry-key-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Kayıt Defteri Anahtarından Değer Okuma
`GetValue` Yöntemi `My.Computer.Registry` nesnesi, Windows kayıt defteri değerlerini okumak için kullanılabilir.  
  
 Aşağıdaki örnekte, "Software\MyApp" anahtar mevcut değilse özel durum oluşur. Varsa `ValueName`, "Adı" aşağıdaki örnekte, mevcut olmadığından `Nothing` döndürülür.  
  
 `GetValue` Yöntemi de belirli bir değeri bir kayıt defteri anahtarı var olup olmadığını belirlemek için kullanılabilir.  
  
 Kod bir Web uygulamasından kayıt okuduğunda, geçerli kullanıcının kimlik doğrulaması ve Web uygulamasında uygulanan kimliğe bürünme tarafından belirlenir.  
  
### <a name="to-read-a-value-from-a-registry-key"></a>Kayıt defteri anahtarından değer okuma için  
  
-   Kullanmak `GetValue` yöntemi, adını ve yolunu belirtme) kayıt defteri anahtarından değer okuma için. Aşağıdaki örnek değeri okuyan `Name` gelen `HKEY_CURRENT_USER\Software\MyApp` ve bir ileti kutusu görüntüler.  
  
     [!code-vb[VbResourceTasks#4](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-read-a-value-from-a-registry-key_1.vb)]  
  
 Bu kod örneği bir IntelliSense kod parçacığı da kullanılabilir. Kod parçacığı Seçici bulunur **Windows işletim sistemi > kayıt defteri**. Daha fazla bilgi için bkz: [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
### <a name="to-determine-whether-a-value-exists-in-a-registry-key"></a>Bir değer olup olmadığını belirlemek için bir kayıt defteri anahtarı var  
  
-   Kullanım `GetValue` değerini almak için yöntem. Aşağıdaki kod, değer var ve mevcut değilse bir ileti döndürür denetler.  
  
     [!code-vb[VbResourceTasks#12](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-read-a-value-from-a-registry-key_2.vb)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Kayıt defteri en üst düzey tutan veya kök, verileri depolamak için kullanılan anahtarları. Örneğin, HKEY_LOCAL_MACHINE kök anahtarı HKEY_CURRENT_USER tek bir kullanıcıya özgü verileri depolamak için kullanılırken, tüm kullanıcılar tarafından kullanılan makine düzeyi ayarlarını depolamak için kullanılır.  
  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Anahtar adı `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Kullanıcının kayıt defteri anahtarları okuma izni yok (<xref:System.Security.SecurityException>).  
  
-   Anahtar adı 255 karakter sınırını aşıyor (<xref:System.ArgumentException>).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bu işlem çalıştırmak için derleme ayrıcalık düzeyi verilen tarafından gerektiriyor <xref:System.Security.Permissions.RegistryPermission> sınıfı. Kısmi güven bağlamda çalıştırıyorsanız, işlem nedeniyle yeterli ayrıcalığa sahip bir özel durum. Benzer şekilde, kullanıcının oluşturulması veya ayarları için doğru ACL olmalıdır. Örneğin, kod erişimi güvenlik izni olan yerel bir uygulama işletim sistemi izni olmayabilir. Daha fazla bilgi için bkz: [kod erişim güvenliği Temelleri](../../../../framework/misc/code-access-security-basics.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 <xref:Microsoft.Win32.RegistryHive>  
 [Kayıt Defterinden Okuma ve Kayıt Defterine Yazma](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
