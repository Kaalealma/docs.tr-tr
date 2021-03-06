---
title: IGCHost::GetStats Metodu
ms.date: 03/30/2017
api_name:
- IGCHost.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetStats
helpviewer_keywords:
- GetStats method, IGCHost interface [.NET Framework hosting]
- IGCHost::GetStats method [.NET Framework hosting]
ms.assetid: c4ae022c-46ac-4f19-9ddd-09b955f19412
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3e0d6f68ffa5280d4616d4fa4ac60b4cb86f6a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="igchostgetstats-method"></a>IGCHost::GetStats Metodu
İstatistikleri çöp toplama sistemi için geçerli durumunu alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pStats`  
 [içinde out] Bir işaretçi bir [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) çöp toplama sistemi geçerli durumu ile ilgili istatistikleri içeren yapısı.  
  
## <a name="remarks"></a>Açıklamalar  
 İstatistikleri çalışması çöp toplama sistemi yardımcı olmak için bir akıllı ayırma sistem tarafından kullanılabilir. Örneğin, daha fazla bellek ekleyin veya bir koleksiyon zorlamak için gereken istatistikleri gözden geçirdikten sonra ayırma sistemi belirleyebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** GCHost.idl, GCHost.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IGCHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
