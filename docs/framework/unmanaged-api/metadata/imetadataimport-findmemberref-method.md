---
title: IMetaDataImport::FindMemberRef Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMemberRef
helpviewer_keywords:
- IMetaDataImport::FindMemberRef method [.NET Framework metadata]
- FindMemberRef method [.NET Framework metadata]
ms.assetid: 1ccda329-d752-4d89-abe8-511af3c3f4c9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c3736d604b7e77028a2b99d462d88ae207df926c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimportfindmemberref-method"></a>IMetaDataImport::FindMemberRef Yöntemi
Üye için MemberRef belirteci için bir işaretçi başvuru diğer bir deyişle alır içine tarafından belirtilen <xref:System.Type> ve belirtilen adı ve meta veri imza sahip.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMemberRef        *pmr  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `td`  
 [in] Sınıf veya aramak için üye başvuru barındırır arabirimi için TypeRef belirteci. Bu değer ise `mdTokenNil`, genel değişken veya işlev genel başvurusu için arama yapılır.  
  
 `szName`  
 [in] Aranacak üye referansın adı.  
  
 `pvSigBlob`  
 [in] Üye başvuru ikili meta verileri imza için bir işaretçi.  
  
 `cbSigBlob`  
 [in] Bayt cinsinden boyutu `pvSigBlob`.  
  
 `pmr`  
 [out] Eşleşen MemberRef belirteci için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Kapsayan sınıf ya da arabirimi kullanarak üyesi belirtin (`td`), kendi adını (`szName`) ve isteğe bağlı olarak imzası (`pvSigBlob`).  
  
 İmza geçirilen `FindMemberRef` imzalar için belirli bir kapsam bağlı olduğundan geçerli kapsamda oluşturulmuş olmalıdır. İmza kapsayan sınıfı veya değer türünü tanımlayan bir belirteç eklenebilir. Belirteç yerel TypeDef tabloya dizinidir. Geçerli kapsam bağlamında dışında bir çalışma zamanı imzası oluşturmak ve girdi olarak bu imza kullanmak `FindMemberRef`.  
  
 `FindMemberRef` doğrudan sınıfta veya arabirimde tanımlanan üye başvuruları bulur; devralınan üye başvuruları bulmaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
