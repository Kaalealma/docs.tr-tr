---
title: ICLRRuntimeInfo::BindAsLegacyV2Runtime Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.BindAsLegacyV2Runtime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime
helpviewer_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime method [.NET Framework hosting]
- BindAsLegacyV2Runtime method [.NET Framework hosting]
ms.assetid: 65fd55ac-4a24-4479-9384-a2e8013bfb2b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 690287bf54f98c19298504ee3058a59ef88a87f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a>ICLRRuntimeInfo::BindAsLegacyV2Runtime Yöntemi
Tüm eski ortak dil çalışma zamanı (CLR) sürüm 2 etkinleştirme ilke kararları için geçerli çalışma zamanı bağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki belirli HRESULTs döndürür:  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Bağlama başarılı ya da bu çalışma zamanı eski CLR sürüm 2 etkinleştirme İlkesi çalışma zamanı zaten bağlıydı.|  
|CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND|Farklı bir çalışma zamanı eski CLR sürüm 2 etkinleştirme ilkesi zaten bağlıydı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Geçerli çalışma zamanının tüm eski CLR sürüm 2 etkinleştirme ilke kararları için zaten bağlıysa (kullanarak örneğin, `useLegacyV2RuntimeActivationPolicy` özniteliği [ \<başlangıç > öğesi](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) yapılandırma dosyası), bu yöntemi bir hata sonucu döndürmüyor; Bunun yerine, yalnızca bu yöntem eski etkinleştirme ilkesi başarıyla bağlı, olduğu gibi sonuç S_OK, olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MetaHost.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICLRRuntimeInfo Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [\<Başlangıç > öğesi](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
