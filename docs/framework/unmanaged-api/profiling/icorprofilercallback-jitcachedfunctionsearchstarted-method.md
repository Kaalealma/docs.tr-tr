---
title: ICorProfilerCallback::JITCachedFunctionSearchStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchStarted
helpviewer_keywords:
- JITCachedFunctionSearchStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchStarted method [.NET Framework profiling]
ms.assetid: 5cba642c-0d80-48ee-889d-198c5044d821
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6d97b40412b6999000a601b72904a03edf2acd08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a>ICorProfilerCallback::JITCachedFunctionSearchStarted Yöntemi
Profil Oluşturucu, arama yerel Görüntü Oluşturucu (NGen.exe) kullanarak önceden derlenen bir işlev için başlatıldı bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `functionId`  
 [in] Arama gerçekleştirildiği işlevi kimliği.  
  
 `pbUseCachedFunction`  
 [out] `true` yürütme altyapısı, (varsa) bir işlev önbelleğe alınmış sürümünü kullanmanız gerekir, aksi takdirde `false`. Değer ise `false`, yürütme altyapısı JIT derlerken JIT derlenmiş olmayan bir sürüm kullanmak yerine işlevi.  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework sürüm 2.0, `JITCachedFunctionSearchStarted` ve [Icorprofilercallback::jıtcachedfunctionsearchfinished yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) geri aramalar değil oluşturulacak normal NGen görüntüleri uygulamasında tüm işlevleri için. Yalnızca bir profil için en iyi duruma getirilmiş NGen görüntüleri tüm işlevleri için geri çağırmaları görüntüde oluşturur. Yalnızca bir işlevin derlenmiş tam zamanında (JIT) olmasını zorlamak için bu geri aramalar kullanmaya çalışırsa, ancak ek yükü nedeniyle, bir profil oluşturucu profil oluşturucu en iyileştirilmiş NGen görseller istemeniz gerekir. Aksi takdirde, profil oluşturucu işlevi bilgilerini toplamak için yavaş bir strateji kullanmanız gerekir.  
  
 Profil oluşturucular burada profili uygulamasının birden çok iş parçacığı aynı yöntemi aynı anda aramakta olduğunuz durumlarda desteklemesi gerekir. Örneğin, iş parçacığı A çağırır `JITCachedFunctionSearchStarted` ve profil oluşturucu ayarlayarak yanıt verdiğini *pbUseCachedFunction*JIT derleme zorlamak için false. Sonra A çağıran iş parçacığı [Icorprofilercallback::jıtcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) ve [Icorprofilercallback::jıtcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).  
  
 Şimdi B çağrıları iş parçacığı `JITCachedFunctionSearchStarted` aynı işlevi için. Profil Oluşturucu Niyet JIT derleme işlevi için belirtilen olsa bile, iş parçacığı A'ın çağrısı için profil oluşturucu yanıtladı önce iş parçacığı B geri gönderdiği için profil oluşturucu ikinci geri çağırma alır `JITCachedFunctionSearchStarted`. İş parçacıklarını nasıl zamanlanmış iş parçacıklarının çağrıları yapma sırası bağlıdır.  
  
 Profil Oluşturucu yinelenen geri aramalar aldığında, tarafından başvurulan değer ayarlamalısınız `pbUseCachedFunction` tüm yinelenen geri aramalar için aynı değeri için. Diğer bir deyişle, ne zaman `JITCachedFunctionSearchStarted` birden çok kez aynı adlı `functionId` değeri, profil oluşturucu her zaman aynı yanıtlaması gerekir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
