---
title: ICorProfilerCallback::ObjectReferences Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectReferences
helpviewer_keywords:
- ObjectReferences method [.NET Framework profiling]
- ICorProfilerCallback::ObjectReferences method [.NET Framework profiling]
ms.assetid: dd5e9b64-b4a3-4ba6-9be6-ddb540f4ffcf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e64eeff8ef80aa264c9c49bd12a0cc45e0da18a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackobjectreferences-method"></a>ICorProfilerCallback::ObjectReferences Yöntemi
Profil Oluşturucu belirtilen nesne tarafından başvurulan bellek nesneleri hakkında uyarır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
#### <a name="parameters"></a>Parametreler  
 `objectId`  
 [in] Nesnelere başvurma nesnesinin kimliği.  
  
 `classId`  
 [in] Belirtilen nesne örneği sınıfı kimliği.  
  
 `cObjectRefs`  
 [in] Belirtilen nesne tarafından başvurulan nesne sayısı (diğer bir deyişle, öğe sayısı `objectRefIds` array).  
  
 `objectRefIds`  
 [in] Tarafından başvurulan kimlikleri nesnelerinin bir dizisi `objectId`.  
  
## <a name="remarks"></a>Açıklamalar  
 `ObjectReferences` Yöntemi yığınında çöp toplama tamamlandıktan sonra geri kalan her bir nesne için çağrılır. Profil Oluşturucu bu geri aramasından hata verirse, profil oluşturma hizmetleri sonraki çöp toplama kadar bu geri çağırma devam etmeyecek.  
  
 `ObjectReferences` Geri çağırma ile birlikte kullanılabilir [Icorprofilercallback::rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) çalışma zamanı için tam nesne başvurusu grafik oluşturmak için geri çağırma. Ortak dil çalışma zamanı (CLR) her nesne başvurusu tarafından yalnızca bir kez bildirilir sağlar `ObjectReferences` yöntemi.  
  
 Tarafından döndürülen nesne kimlikleri `ObjectReferences` çöp toplama nesneleri taşıma ortasında olabileceği için geri çağırma sırasında kendisini geçerli değildir. Bu nedenle, profil oluşturucular sırasında nesneleri incelemek çalışmamalısınız bir `ObjectReferences` çağırın. Zaman [Icorprofilercallback2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) çağrılır, atık toplama tamamlandığında ve İnceleme güvenle yapılabilir.  
  
 Bir null `ClassId` belirten `objectId` kaldırdığı bir türe sahip.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
