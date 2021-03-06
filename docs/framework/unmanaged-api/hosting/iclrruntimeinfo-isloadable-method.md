---
title: ICLRRuntimeInfo::IsLoadable Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoadable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoadable
helpviewer_keywords:
- IsLoadable method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoadable method [.NET Framework hosting]
ms.assetid: 205ca53b-e78e-49b2-9a46-2a7823e96b8c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e60c3b06453e0f447249bddf5d4da5c240576577
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="iclrruntimeinfoisloadable-method"></a>ICLRRuntimeInfo::IsLoadable Yöntemi
Geçerli işlemine dikkate alarak bu arabirimle ilişkili çalışma zamanının yüklü olup olmadığını gösterir işlemine zaten yüklenmiş diğer çalışma zamanları.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pbLoadable`  
 [out] `true` bu çalışma zamanı, geçerli işlemin içine yüklenen Aksi takdirde `false`.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_POINTER|`pbLoadable` null şeklindedir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Başka bir çalışma zamanı işlemine zaten yüklü ve bu arabirimle ilişkili çalışma zamanı işlem içi yan yana yürütme için yüklenebilir `pbLoadable` döndürür `true`. İki çalışma zamanları yan yana işlemdeki, çalıştırırsanız `pbLoadable` döndürür `false`. Örneğin, ortak dil çalışma zamanı (CLR) sürüm 4-yana CLR Version 2.0 sürümü ile aynı işlemde veya CLR sürüm 1.1 çalıştırabilirsiniz. Ancak, CLR sürüm 1.1 ve CLR Version 2.0 sürümü yan yana işlemdeki çalıştırılamaz.  
  
 Hiç çalışma zamanları işlem içine yüklenmiş ise, bu yöntem her zaman döndürür `true`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MetaHost.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICLRRuntimeInfo Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)
