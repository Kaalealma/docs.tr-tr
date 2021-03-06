---
title: ISymUnmanagedMethod Arabirimi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod
helpviewer_keywords:
- ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: f204d74c-cc79-4092-83bb-60654be95649
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 728acc09f739fe567fca4a2571cbabf1ba8838a2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedmethod-interface"></a>ISymUnmanagedMethod Arabirimi
Sembol deposu içinde yöntemi temsil eder. Bu arabirim türü ile ilgili öznitelikleri yerine bir yöntemin yalnızca simgesi ilgili öznitelikleri erişim sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetNamespace Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getnamespace-method.md)|Bu yöntem tanımlandığı ad alır.|  
|[GetOffset Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getoffset-method.md)|Bir belge içinde belirli bir konuma karşılık gelen bu yöntem içinde uzaklığını döndürür.|  
|[GetParameters Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getparameters-method.md)|Bu yöntem için parametre alır.|  
|[GetRanges Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getranges-method.md)|Bir konumda bir belge, bu yöntem içinde konumu kapsayan Microsoft Ara dili (MSIL) aralıklarına karşılık gelir başlangıç ve bitiş uzaklığında çiftleri dizisi döndürür.|  
|[GetRootScope Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getrootscope-method.md)|Bu yöntem için kök sözcük kapsamda alır. Bu kapsam tüm yöntemi barındırır.|  
|[GetScopeFromOffset Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getscopefromoffset-method.md)|Belirtilen uzaklık kapsayan bu yöntem en kapsayan sözcük kapsamında alır.|  
|[GetSequencePointCount Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepointcount-method.md)|Bu yöntem içinde sıralama noktaları sayısını alır.|  
|[GetSequencePoints Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepoints-method.md)|Bu yöntem içindeki tüm sıralama noktaları alır.|  
|[GetSourceStartEnd Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsourcestartend-method.md)|Bu yöntem kaynak için başlangıç ve bitiş belge konumlarına alır.|  
|[GetToken Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-gettoken-method.md)|Bu yöntem için meta veri belirtecini döndürür.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tanılama Simge Deposu Arabirimleri](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
