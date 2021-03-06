---
title: 'Nasıl yapılır: İki Aşamalı bir Bekleme İşlemini Uygulamak için SpinWait Kullanma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinWait, how to synchronize two-phase wait
ms.assetid: b2ac4e4a-051a-4f65-b4b9-f8e103aff195
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af6e4e8d0d754b97478788422b4dd84eeddc6491
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a>Nasıl yapılır: İki Aşamalı bir Bekleme İşlemini Uygulamak için SpinWait Kullanma
Aşağıdaki örnekte nasıl kullanılacağını gösteren bir <xref:System.Threading.SpinWait?displayProperty=nameWithType> aşamalı bir bekleme işlemini uygulamak için nesne. İlk aşamada, eşitleme nesnesi bir `Latch`, kilit kullanılabilir hale olup olmadığını denetlerken birkaç döngüsü boyunca döner. İkinci aşamada kilit kullanılabilir hale gelirse sonra `Wait` yöntemi döndürür kullanmadan <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> kendi bekleyin; gerçekleştirmek için Aksi halde, `Wait` bekleme gerçekleştirir.  
  
## <a name="example"></a>Örnek  
 Bu örnek çok basit bir uygulama Mandal eşitleme ilkel gösterir. Bekleme süresini çok kısa olması beklenen olduğunda, bu veri yapısını kullanabilirsiniz. Bu örnek, yalnızca tanıtım amacıyla kullanılır. Programınıza tutma türü işlevsellik gerektiriyorsa kullanmayı <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 Mandal kullanan <xref:System.Threading.SpinWait> sonraki çağrısı kadar yalnızca yerinde dönmeye nesne `SpinOnce` neden <xref:System.Threading.SpinWait> iş parçacığının zaman dilimi elde etmek üzere. Bu noktada, Mandal kendi içerik anahtarı çağırarak neden olan <xref:System.Threading.WaitHandle.WaitOne%2A> üzerinde <xref:System.Threading.ManualResetEvent> ve zaman aşımı değerini geri kalanı geçirme.  
  
 Mandal ne sıklıkta kullanmadan kilit alınırken tarafından performansını artırabilirsiniz günlük çıktısı gösterir <xref:System.Threading.ManualResetEvent>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SpinWait](../../../docs/standard/threading/spinwait.md)  
 [İş Parçacığı Nesneleri ve Özellikleri](../../../docs/standard/threading/threading-objects-and-features.md)
