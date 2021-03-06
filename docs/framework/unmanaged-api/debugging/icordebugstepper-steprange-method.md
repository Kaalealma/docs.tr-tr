---
title: ICorDebugStepper::StepRange Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.StepRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::StepRange
helpviewer_keywords:
- StepRange method [.NET Framework debugging]
- ICorDebugStepper::StepRange method [.NET Framework debugging]
ms.assetid: b9776112-6e6d-4708-892a-8873db02e16f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 838f2df06f8875037edbe39d2db0411f31abe01f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugsteppersteprange-method"></a>ICorDebugStepper::StepRange Yöntemi
Tek adım içeren kendi iş parçacığı aracılığıyla ve en son belirtilen aralıkların dışında kod ulaştığında döndürmek için bu ICorDebugStepper neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `bStepIn`  
 [in] Kümesine `true` iş parçacığı içinde adlı bir işlev adımla için. Kümesine `false` işlevi Adımlama için.  
  
 `ranges`  
 [in] Her biri bir aralığı belirtir dizisi COR_DEBUG_STEP_RANGE yapıların.  
  
 `cRangeCount`  
 [in] Boyutunu `ranges` dizi.  
  
## <a name="remarks"></a>Açıklamalar  
 `StepRange` Yöntem çalışır gibi [ICorDebugStepper::Step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md) yöntemi, verilen aralığı dışındaki kodu kadar tamamlanmazsa dışında oranında doldu.  
  
 Bu, aynı anda tek bir yönerge atlama'den daha etkili olabilir. Aralıkları Adımlayıcı 's çerçeve başlangıç uzaklık çiftlerinden oluşan bir liste olarak belirtilir.  
  
 Bir yöntem Microsoft Ara dili (MSIL) kod göre aralıktır. Çağrı [ICorDebugStepper::setrangeıl](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md) ile `false` bir yöntemin yerel kod göre aralıkları yapma.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
