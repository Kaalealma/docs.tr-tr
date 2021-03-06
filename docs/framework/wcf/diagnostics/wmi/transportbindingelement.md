---
title: TransportBindingElement
ms.date: 03/30/2017
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
ms.openlocfilehash: dc7a29e5911a9d0a774e36f5be8c1f3cacad69b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="transportbindingelement"></a>TransportBindingElement
TransportBindingElement  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 TransportBindingElement sınıfı herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 TransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="manualaddressing"></a>manualAddressing  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Kullanıcı ileti adresleme denetimini almak istediği olup olmadığını belirten bir Boole değeri.  
  
### <a name="maxbufferpoolsize"></a>maxBufferPoolSize  
 Veri türü: sint64  
  
 Erişim türüne: salt okunur  
  
 Bağlama için en büyük arabellek havuzu boyutu.  
  
### <a name="maxreceivedmessagesize"></a>MaxReceivedMessageSize  
 Veri türü: sint64  
  
 Erişim türüne: salt okunur  
  
 Bu bağlama tarafından işlenen bir ileti için en büyük boyutu.  
  
### <a name="scheme"></a>Düzen  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Taşıma için kullanılacak URI düzeni.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.TransportBindingElement>
