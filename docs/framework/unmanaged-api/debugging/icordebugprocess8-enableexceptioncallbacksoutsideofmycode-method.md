---
title: ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Yöntemi
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5f08f24e16b34d911793b5c8d4a28168f7677b22
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a>ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Yöntemi
[Desteklenen [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] ve sonraki sürümlerinde]  
  
 Etkinleştirir ya da belirli türlerdeki devre dışı bırakır [Icordebugmanagedcallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) özel durum geri aramalar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `enableExceptionsOutsideOfJMC`  
 [in]  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa değerini `enableExceptionsOutsideOfJMC` olan `false`:  
  
-   Bir DEBUG_EXCEPTION_FIRST_CHANCE özel çağırma işleminde hata ayıklayıcısı için yol açmaz.  
  
-   Özel durum hiç kullanıcı koda çıkışları DEBUG_EXCEPTION_CATCH_HANDLER_FOUND özel durum çağırma işleminde hata ayıklayıcıya neden olur değil (diğer bir deyişle, bir özel durum işleyici bir özel durum kaynaktan yoluna JustMyCode veya JMC olarak işaretlenmiş yöntemi yok).  
  
 Varsayılan değer olan `enableExceptionsOutsideOfJMC` olan `true`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugProcess8 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
