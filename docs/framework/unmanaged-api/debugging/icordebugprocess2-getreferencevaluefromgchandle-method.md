---
title: ICorDebugProcess2::GetReferenceValueFromGCHandle Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetReferenceValueFromGCHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetReferenceValueFromGCHandle
helpviewer_keywords:
- GetReferenceValueFromGCHandle method [.NET Framework debugging]
- ICorDebugProcess2::GetReferenceValueFromGCHandle method [.NET Framework debugging]
ms.assetid: 8bdd7f4c-19f2-4ede-875e-603773e8c128
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60624a5f6323399d06bda4e0280de8fbe861bd9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a>ICorDebugProcess2::GetReferenceValueFromGCHandle Metodu
Bir başvuru işaretçi işlemek çöp toplama sahip belirtilen yönetilen nesneyi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `handle`  
 [in] Çöp toplama tanıtıcı sahip yönetilen bir nesne için bir işaretçi. Bu değer bir <xref:System.IntPtr> nesne ve kaynağından alınan <xref:System.Runtime.InteropServices.GCHandle> yönetilen nesne için.  
  
 `pOutValue`  
 [out] Bir işaretçi adresine Icordebugreferencevalue nesnenin belirtilen yönetilen nesneye bir başvurusu temsil eder.  
  
## <a name="remarks"></a>Açıklamalar  
 Döndürülen başvuru değeri bir atık toplama başvuru değeri ile karıştırmayın.  
  
 Döndürülen başvuru normal bir referans gibi davranır. Kod yürütmeyi kesme noktası sonra devam ettiğinde devre dışıdır. Hedef nesne ömrü başvuru değeri ömrü tarafından etkilenmez.  
  
> [!NOTE]
>  `GetReferenceValueFromGCHandle` Yöntemi tanıtıcı doğrulamaz. Bu nedenle, `GetReferenceValueFromGCHandle` yöntemi olası bozulmasına neden olabilir hata ayıklayıcı ve geçersiz bir tanıtıcı aktarılırsa ayıklanacak kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
