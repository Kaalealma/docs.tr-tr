---
title: ICorDebugILCode::GetEHClauses Metodu
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode.GetEHClauses
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: cf7a0e00-06ae-47a5-8037-598b26196802
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8eca550130a22532cb781e09ec59c60c11a5ba33
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugilcodegetehclauses-method"></a>ICorDebugILCode::GetEHClauses Metodu
[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]  
  
 Özel durum işleme bu Ara dile (IL) tanımlanır (EH) yan tümceleri listesine bir işaretçi döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cClauses`  
 [in] Depolama kapasitesini `clauses` dizi. Daha fazla bilgi için Açıklamalar bölümüne bakın.  
  
 `pcClauses`  
 [out] Hakkında bilgi yazılır yan tümceleri sayısı `clauses` dizi.  
  
 yan tümceleri  
 [out] Bir dizi [CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) özel durum yan tümceleri bu IL için tanımlanan işleme hakkında bilgi içeren nesne.  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa `cClauses` 0'dır ve `pcClauses` olan olmayan**null**, `pcClauses` kullanılabilir özel durum yan tümceleri işleme sayısını ayarlayın. Varsa `cClauses` sıfır, değil depolama kapasitesini temsil `clauses` dizi. Yöntem döndüğünde `clauses` en fazla içeren `cClauses` öğeleri ve `pcClauses` gerçekte yazılan yan tümceleri sayısına ayarlayın `clauses` dizi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugILCode Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 [CorDebugEHClause Yapısı](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
