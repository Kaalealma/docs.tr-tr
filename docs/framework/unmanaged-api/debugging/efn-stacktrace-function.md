---
title: _EFN_StackTrace İşlevi
ms.date: 03/30/2017
api_name:
- _EFN_StackTrace
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_StackTrace
helpviewer_keywords:
- _EFN_StackTrace function [.NET Framework debugging]
ms.assetid: caea7754-867c-4360-a65c-5ced4408fd9d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 39a249108d10e5dc382775378e2d6b84bba87356
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="efnstacktrace-function"></a>_EFN_StackTrace İşlevi
Yönetilen yığın izlemesi metin gösterimini ve bir dizi sağlar `CONTEXT` kaydeder, bir yönetilmeyen ve yönetilen kod arasında her geçiş için.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CALLBACK _EFN_StackTrace(  
    [in]  PDEBUG_CLIENT  Client,  
    [out] WCHAR          wszTextOut[],  
    [out] size_t         *puiTextLength,  
    [out] LPVOID         pTransitionContexts,  
    [out] size_t         *puiTransitionContextCount,  
    [in]  size_t         uiSizeOfContext,  
    [in]  DWORD          Flags  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `Client`  
 [in] Ayıklanacak istemci.  
  
 `wszTextOut`  
 [out] Yığın izleme metin gösterimi.  
  
 `puiTextLength`  
 [out] Karakter sayısını gösteren bir işaretçi `wszTextOut`.  
  
 `pTransitionContexts`  
 [out] Geçişi içerikleri dizisi.  
  
 `puiTransitionContextCount`  
 [out] Geçişi içerikleri dizisindeki sayısı için bir işaretçi.  
  
 `uiSizeOfContext`  
 [in] Bağlam yapısı boyutu.  
  
 `Flags`  
 [in] EBP kayıt ve her önünde enter yığın işaretçisi (ESP) göstermek için 0 veya SOS_STACKTRACE_SHOWADDRESSES (0x01) olarak ayarlayın `module!functionname` satır.  
  
## <a name="remarks"></a>Açıklamalar  
 `_EFN_StackTrace` Yapısı WinDbg programlı arabiriminden çağrılabilir. Parametreleri aşağıdaki gibi kullanılır:  
  
-   Varsa `wszTextOut` null ve `puiTextLength` olan null, işlev dize uzunluğunu döndürür `puiTextLength`.  
  
-   Varsa `wszTextOut` olan null, işlev metinde depolar `wszTextOut` tarafından belirtilen konumda kadar `puiTextLength`. Başarıyla arabellek yeterince uzun değildi, arabellek ya da döndürür E_OUTOFMEMORY yeterli alan olduğunu döndürür.  
  
-   İşlev geçiş kısmı yoksayılır `pTransitionContexts` ve `puiTransitionContextCount` her ikisi de null olan. Bu durumda, yalnızca işlev adlarını metin çıktısını ile arayanlar işlevi sağlar.  
  
-   Varsa `pTransitionContexts` null ve `puiTransitionContextCount` olan null, işlevi gerekli sayısı bağlam giriş döndürür `puiTransitionContextCount`.  
  
-   Varsa `pTransitionContexts` olan null, işlevi ona yapıları uzunlukta bir dizi gibi davranır `puiTransitionContextCount`. Yapı boyutu tarafından verilen `uiSizeOfContext`, ve boyutunu olmalıdır [SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) veya `CONTEXT` mimarisi için.  
  
-   `wszTextOut` şu biçimde yazılır:  
  
    ```  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
-   Onaltılık uzaklık 0x0 ise, uzaklık yazılır.  
  
-   Varsa yönetilen kod yok iş parçacığı üzerinde şu anda bağlamında, işlevi SOS_E_NOMANAGEDCODE döndürür.  
  
-   `Flags` Parametredir 0 veya EBP ve ESP her önünde görmek için SOS_STACKTRACE_SHOWADDRESSES `module!functionname` satır. Varsayılan olarak, 0'dır.  
  
    ```  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** SOS_Stacktrace.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
