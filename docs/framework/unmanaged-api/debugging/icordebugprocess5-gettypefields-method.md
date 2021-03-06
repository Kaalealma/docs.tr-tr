---
title: ICorDebugProcess5::GetTypeFields Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeFields
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeFields
helpviewer_keywords:
- GetTypeFields method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeFields method [.NET Framework debugging]
ms.assetid: 6a0ad3ee-dacb-47e9-abae-4536bcc4804b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 214fc97e41d8d220547a5f8bd28117ff411fa89b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocess5gettypefields-method"></a>ICorDebugProcess5::GetTypeFields Metodu
Bir türe ait alanları hakkında bilgi sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],   
    [out] ULONG32 *pceltNeeded  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `id`  
 [in] Alan bilgilerini alınan tür tanımlayıcısı.  
  
 `celt`  
 [in] Sayısı [cor_fıeld](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) , alan bilgidir alınacak nesneleri.  
  
 `fields`  
 [out] Bir dizi [cor_fıeld](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) türe ait alanları hakkında bilgi sağlayan nesne.  
  
 `pceltNeeded`  
 [out] Sayısını gösteren bir işaretçi [cor_fıeld](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) dahil nesneleri `fields`.  
  
## <a name="remarks"></a>Açıklamalar  
 `celt` Alan bilgilerini doldurmak için yöntemini kullanır alan sayısını belirten parametresi `fields`, değerine karşılık gelmelidir `COR_TYPE_LAYOUT::numFields` alan.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugProcess5 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
