---
title: _CorDllMain İşlevi
ms.date: 03/30/2017
api_name:
- _CorDllMain
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorDllMain
helpviewer_keywords:
- _CorDllMain function [.NET Framework hosting]
ms.assetid: bc7b51cf-39d3-48ec-a5cb-2f179fbefff8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5d541f834e829305fa2b091c45d0dc8f387bb55
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="cordllmain-function"></a>_CorDllMain İşlevi
Ortak dil çalışma zamanı (CLR) başlatır, DLL derlemenin CLR üstbilgisinde yönetilen giriş noktasını bulur ve yürütmeye başlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `hInst`  
 [in] Yüklenen modülün örneği tanıtıcısı.  
  
 `dwReason`  
 [in] DLL giriş noktası işlevi neden çağrılan gösterir. Bu parametre aşağıdaki değerlerden biri olabilir: DLL_PROCESS_ATTACH, DllMain, DllMain veya DLL_PROCESS_DETACH. Bu değerleri açıklamaları için bkz: `DllMain` Platform SDK Belgeleri.  
  
 `lpReserved`  
 [in] Kullanılmayan.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem `true` başarı için ve `false` bir hata oluşursa.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu işlev, DLL derlemeler için işletim sistemi yükleyicisi tarafından çağrılır. Yürütülebilir derlemeler için yükleyici çağırır [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) yerine işlev.  
  
 İşletim sistemi yükleyicisi bağımsız olarak DLL dosyasında belirtilen giriş noktası bu yöntemi çağırır.  
  
 Windows 98, Windows ME, Windows NT ve Windows 2000'de, `_CorDllMain` işlevi çağrıldığında dolaylı olarak fixupin işletim sistemi yükleyicisi. Tüm diğer Windows sürümlerinde doğrudan işletim sistemi yükleyicisi tarafından çağrılır.  
  
 Ek bilgi için açıklamalar bölümünde bakın [_corvalidateımage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) konu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta Veri Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
