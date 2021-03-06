---
title: İzleme Türü Özeti
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: e3bc66753dd44e1dc4c7417caf593820300f69a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="trace-type-summary"></a>İzleme Türü Özeti
[Kaynak düzeyleri](http://go.microsoft.com/fwlink/?LinkID=94943) çeşitli izleme düzeyleri tanımlar: Kritik hata, uyarı, bilgi ve ayrıntılı, sağlar açıklaması `ActivityTracing` çıktısını değiştirir bayrağı sınır ve etkinlik aktarım olayları izleme.  
  
 Ayrıca gözden geçirebilirsiniz [TraceEventType](http://go.microsoft.com/fwlink/?LinkId=95169) gelen yayılan izlerini türleri için <xref:System.Diagnostics>.  
  
 Aşağıdaki tabloda en önemlileri listeler.  
  
|İzleme türü|Açıklama|  
|----------------|-----------------|  
|Kritik|Önemli hata veya uygulama kilitlenme.|  
|Hata|Kurtarılamaz bir hata.|  
|Uyarı|Bilgi iletisi.|  
|Bilgiler|Kritik olmayan sorun.|  
|Ayrıntılı|Hata ayıklama izleme.|  
|Başlat|İşlem bir mantıksal birim başlatılıyor.|  
|Askıya alma|İşleme bir mantıksal birim ertelenmesi.|  
|Devam etme|İşleme bir mantıksal birim sürdürme.|  
|Durdur|İşleme bir mantıksal birim durduruluyor.|  
|Aktarma|Bağıntı kimliğini değiştirme.|  
  
 Bir etkinlik izleme türleri yukarıdaki bileşimi tanımlanır.  
  
 Yerel (izleme kaynak) kapsamda ideal bir etkinlik tanımlayan normal bir ifade değil,  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 Başka bir deyişle, bir etkinlik aşağıdaki koşulları karşılaması gerekir.  
  
-   Başlamalı ve sırasıyla Başlat ve Durdur izlemeler tarafından Durdur  
  
-   Askıya alma veya sürdürme izleme hemen önceki bir aktarım izleme olmalıdır  
  
-   Böyle izlemeleri varsa askıya alma ve sürdürme izlemeleri arasındaki tüm izlemeleri olmamalıdır  
  
-   Önceki koşullar gözlenen sürece herhangi ve birçok Kritik/hata/uyarı/bilgi/Verbose/aktarım izlemeleri olarak olabilir  
  
 Genel kapsamda ideal bir etkinlik tanımlayan normal bir ifade değil,  
  
```  
R+   
```  
  
 yerel kapsam içinde bir etkinlik için normal ifade edilen R ile. Bu şekilde çevirir,  
  
```  
[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+  
```
