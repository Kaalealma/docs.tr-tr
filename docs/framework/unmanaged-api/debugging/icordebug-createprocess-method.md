---
title: ICorDebug::CreateProcess Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebug.CreateProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::CreateProcess
helpviewer_keywords:
- ICorDebug::CreateProcess method [.NET Framework debugging]
- CreateProcess method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: b6128694-11ed-46e7-bd4e-49ea1914c46a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 044f94a567dc4bc2b169ba2a5f2a5d7b4f98e516
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugcreateprocess-method"></a>ICorDebug::CreateProcess Yöntemi
Hata ayıklayıcı denetiminde birincil kendi iş parçacığı ve bir işlem başlatır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateProcess (  
    [in]  LPCWSTR                     lpApplicationName,  
    [in]  LPWSTR                      lpCommandLine,  
    [in]  LPSECURITY_ATTRIBUTES       lpProcessAttributes,  
    [in]  LPSECURITY_ATTRIBUTES       lpThreadAttributes,  
    [in]  BOOL                        bInheritHandles,  
    [in]  DWORD                       dwCreationFlags,  
    [in]  PVOID                       lpEnvironment,  
    [in]  LPCWSTR                     lpCurrentDirectory,  
    [in]  LPSTARTUPINFOW              lpStartupInfo,  
    [in]  LPPROCESS_INFORMATION       lpProcessInformation,  
    [in]  CorDebugCreateProcessFlags  debuggingFlags,  
    [out] ICorDebugProcess            **ppProcess  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `lpApplicationName`  
 [in] İşaretçi null ile sonlandırılmış dizeye başlatılan işlem tarafından yürütülecek Modülü belirtir. Modül çağırma işlemi güvenlik bağlamında çalıştırılır.  
  
 `lpCommandLine`  
 [in] İşaretçi null ile sonlandırılmış dizeye başlatılan işlem tarafından yürütülecek komut satırını belirtir. Uygulama adı (örneğin, "SomeApp.exe"), ilk bağımsız değişken olmalıdır.  
  
 `lpProcessAttributes`  
 [in] Win32 işaretçi `SECURITY_ATTRIBUTES` işlemi için güvenlik tanımlayıcısı belirtir yapısı. Varsa `lpProcessAttributes` olan null, işlem varsayılan güvenlik tanımlayıcısını alır.  
  
 `lpThreadAttributes`  
 [in] Win32 işaretçi `SECURITY_ATTRIBUTES` işleminin birincil iş parçacığı için güvenlik tanımlayıcısı belirtir yapısı. Varsa `lpThreadAttributes` olan varsayılan güvenlik tanımlayıcısı boş iş parçacığı alır.  
  
 `bInheritHandles`  
 [in] Kümesine `true` her devralınabilir tanıtıcı arama işleminde başlatılan işlem tarafından devralınır belirtmek için veya `false` tanıtıcıları devralınmaz belirtmek için. Devralınan tanıtıcıları özgün tanıtıcıları aynı değeri ve erişim haklarına sahip.  
  
 `dwCreationFlags`  
 [in] Bit düzeyinde bileşimini [Win32 işlem oluşturma bayrakları](http://go.microsoft.com/fwlink/?linkid=69981) Öncelik sınıfını ve başlatılan işlem davranışını kontrol eden.  
  
 `lpEnvironment`  
 [in] Yeni işlem için bir ortam bloğu işaretçi.  
  
 `lpCurrentDirectory`  
 [in] İşaretçi null ile sonlandırılmış dizeye işlemi için geçerli dizin tam yolunu belirtir. Bu parametre null ise, yeni işlem çağırma işlemi aynı geçerli sürücü ve dizine sahip.  
  
 `lpStartupInfo`  
 [in] Win32 işaretçi `STARTUPINFOW` yapısı pencere istasyonu, masaüstü, standart tanıtıcıları ve başlatılan işlem için ana penceresinin görünümünü belirtir.  
  
 `lpProcessInformation`  
 [in] Win32 işaretçi `PROCESS_INFORMATION` yapısı başlatılacak işlemi kimlik bilgilerini belirtir.  
  
 `debuggingFlags`  
 [in] Hata ayıklama seçeneklerini belirtir. CorDebugCreateProcessFlags numaralandırması değeri.  
  
 `ppProcess`  
 [out] İşlemi temsil eden bir Icordebugprocess nesnesi adresini gösteren bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem parametrelerini Win32 aynıdır `CreateProcess` yöntemi.  
  
 Yönetilmeyen karışık mod hata ayıklamayı etkinleştirmek için ayarlanmış `dwCreationFlags` DEBUG_PROCESS için &#124; DEBUG_ONLY_THIS_PROCESS. Yalnızca yönetilen hata ayıklama kullanmak istiyorsanız, bu bayraklar ayarlı değil.  
  
 Hata ayıklayıcı ve işlem olmasını (ekli işlemi) hata ayıklaması, tek bir konsol paylaşabilir ve birlikte çalışma hata ayıklama kullanılırsa, ekli işleminin konsol için kilitler ve hata ayıklama etkinlikte durdurmak mümkündür. Hata ayıklayıcı sonra Konsolu'nu kullanma girişimleri engellenir. Bu sorunu önlemek için CREATE_NEW_CONSOLE bayrağını ayarlayın `dwCreationFlags` parametresi.  
  
 Birlikte çalışma hata ayıklama IA-64 tabanlı ve AMD64 tabanlı platformları gibi Win9x ve x86 olmayan platformlarda desteklenmiyor.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebug Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
