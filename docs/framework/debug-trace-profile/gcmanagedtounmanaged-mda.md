---
title: gcManagedToUnmanaged MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- GcManagedToUnmanaged MDA
- GC managed to unmanaged
- transitioning threads managed to unmanaged code
- threading [.NET Framework], garbage collection
- managed to unmanaged garbage collection
- managed debugging assistants (MDAs), garbage collection
- threading [.NET Framework], managed debugging assistants
- garbage collection, run-time errors
ms.assetid: 7417f837-805e-4fed-a430-ca919c8421dc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9be8165af499729c7b3a95c480cb64d0200e23fd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="gcmanagedtounmanaged-mda"></a>gcManagedToUnmanaged MDA
`gcManagedToUnmanaged` Yönetilen hata ayıklama Yardımcısı (MDA) yönetilmeyen kod için yönetilen bir iş parçacığı gelen geçiş her bir atık toplama neden olur.  
  
## <a name="symptoms"></a>Belirtiler  
 Bir yönetilmeyen kullanıcı bileşeni COM'a gösterilen yönetilen bir nesnenin kullanmaya çalışırken bir erişim ihlali oluşturur COM nesnesi çıkarılan görünüyor. Erişim ihlali belirleyici değildir.  
  
## <a name="cause"></a>Sebep  
 Yönetilmeyen bir bileşen başvuru yönetilen bir COM nesnesi düzgün sayım değilse, çalışma zamanı yönetilmeyen bileşen hala nesneye bir başvurusu tuttuğunda com'a yönetilen bir nesnenin toplamak. Çalışma zamanı çağrıları <xref:System.Runtime.InteropServices.Marshal.Release%2A> çöp koleksiyonları sırasında şekilde çöp toplama oluşmadan önce kullanıcı Bileşen Nesne kullanıyorsa, sonra henüz alınamadı. Bu nondeterminism kaynağıdır.  
  
## <a name="resolution"></a>Çözüm  
 Bu Yardımcısı'nı etkinleştirme nesnesi için koleksiyonu uygun olduğunda arasında geçen zamanı azaltır ve <xref:System.Runtime.InteropServices.Marshal.Release%2A> olarak adlandırılan, yönetilmeyen hangi bileşenin ilk toplanan nesne erişmeye çalıştığında aşağı izlemek için yardımcı olur.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 Yönetilmeyen kod için bir iş parçacığı geçişler yönetilen her bir atık toplama neden olur.  
  
## <a name="output"></a>Çıkış  
 Bu MDA herhangi bir çıktı oluşturmaz.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcManagedToUnmanaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Birlikte Çalışma için Hazırlama](../../../docs/framework/interop/interop-marshaling.md)  
 [gcUnmanagedToManaged](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)
