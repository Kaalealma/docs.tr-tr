---
title: 'Nasıl yapılır: Uygulama Etki Alanını Boşaltma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Unload method
- application domains, unloading
- unloading application domains
ms.assetid: f356116d-e415-4f7c-a332-6e6a60227192
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0a9e5ee865b5e0ac9ec0214a4a0b5194bbcd9f30
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-unload-an-application-domain"></a>Nasıl yapılır: Uygulama Etki Alanını Boşaltma
Uygulama etki alanı ile işiniz bittiğinde, kullanarak unload <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> yöntemi. **Unload** yöntemi, belirtilen uygulama etki alanı düzgün biçimde kapatır. Kaldırma işlemi sırasında hiçbir yeni iş parçacıkları uygulama etki alanı erişebilir ve tüm uygulama etki alanı – özel veri yapıları serbest.  
  
 Uygulama etki alanına yüklenmiş derlemeleri kaldırılır ve artık kullanılamaz. Bütünleştirilmiş uygulama etki alanındaki etki alanı neutral ise, veri derleme için bütün işlem kapatılana kadar bellekte kalır. Tüm işlem kapatılıyor dışında bir etki alanı Tarafsız derleme kaldırmak için bir mekanizma yoktur. Burada bir uygulama etki alanını boşaltma isteği çalışmaz ve sonuçlanır durumlar vardır bir <xref:System.CannotUnloadAppDomainException>.  
  
 Aşağıdaki örnek olarak adlandırılan yeni bir uygulama etki alanı oluşturur `MyDomain`, bazı bilgileri konsola yazdırır ve uygulama etki alanı kaldırır. Kodu daha sonra konsola bellekten uygulama etki alanı kolay adını yazdırmak çalışır olduğunu unutmayın. Bu eylem, program sonunda try/catch deyimleri tarafından işlenen bir özel durum oluşturur.  
  
## <a name="example"></a>Örnek  
 [!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)]
 [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)]
 [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uygulama etki alanları ile programlama](application-domains.md#programming-with-application-domains)  
 [Nasıl yapılır: Uygulama Etki Alanı Oluşturma](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
 [Uygulama Etki Alanlarını Kullanma](../../../docs/framework/app-domains/use.md)
