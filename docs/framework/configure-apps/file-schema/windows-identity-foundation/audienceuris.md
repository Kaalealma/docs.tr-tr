---
title: '&lt;AudienceUri&gt;'
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 7415cb3f1792d2de566161ae6c348ef591b4a0c3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltaudienceurisgt"></a>&lt;AudienceUri&gt;
Bağlı olan taraf (RP) kabul edilebilir tanımlayıcılardır URI'ler kümesini belirtir. İzin verilen kitle URI'ler biri için kapsamındaki sürece belirteçleri kabul edilmedi.  
  
 \<system.identityModel>  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<securityTokenHandlerConfiguration >  
\<AudienceUri >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <audienceUris mode=xs:string>  
          <add value=xs:string />  
          <clear />  
          <remove value=xs:string />  
        </audienceUris>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|mod|Bir <xref:System.IdentityModel.Selectors.AudienceUriMode> İzleyici kısıtlama için gelen belirteci uygulanmış olup olmadığını belirten değer. Olası değerler şunlardır: "Her zaman", "Hiçbir zaman"'i ve "BearerKeyOnly". "Her zaman" varsayılandır. İsteğe bağlı.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`<add value=xs:string>`|Belirtilen URI ekler `value` özniteliği için AudienceUri koleksiyonu. `value` Özniteliği gereklidir. URI büyük/küçük harf duyarlıdır.|  
|`<clear>`|AudienceUri koleksiyonunu temizler. Tüm kimliklerin koleksiyondan kaldırılır.|  
|`<remove value=xs:string>`|Belirtilen URI kaldırır `value` AudienceUri koleksiyonundan özniteliği. `value` Özniteliği gereklidir. URI büyük/küçük harf duyarlıdır.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Güvenlik bir koleksiyon için yapılandırma belirteci işleyicileri sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, koleksiyon boştur; kullanmak `<add>`, `<clear>`, ve `<remove>` öğe koleksiyonunu Değiştir. <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> ve <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> herhangi yapılandırmak için hedef kitleye URI koleksiyonu izin verilen değerler İzleyici URI kısıtlamaları kullanım nesneleri <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> nesneleri.  
  
 `<audienceUris>` Öğesi ile temsil edilir <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> sınıfı. Koleksiyona eklenen ayrı bir URI tarafından temsil edilen <xref:System.IdentityModel.Configuration.AudienceUriElement> sınıfı.  
  
> [!NOTE]
>  Kullanımını `<audienceUris>` öğesi bir alt öğesi olarak [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi kullanım dışı bırakıldı, ancak hala geriye dönük uyumluluk için desteklenir. Ayarları `<securityTokenHandlerConfiguration>` öğesi geçersiz kılar üzerinde `<identityConfiguration>` öğesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML, bir uygulama için kabul edilebilir İzleyici URI'ler yapılandırma gösterilmektedir. Bu örnek, tek bir URI yapılandırır. Bu URI için kapsamlı belirteçleri kabul eder, diğerlerini reddedilir.  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
