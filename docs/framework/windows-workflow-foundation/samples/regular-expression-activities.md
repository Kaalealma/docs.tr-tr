---
title: Normal ifade etkinlikleri
ms.date: 03/30/2017
ms.assetid: b8f24694-49db-4339-92ec-014e3d4ae63b
ms.openlocfilehash: 34b1f18f26f0b79c4b8711d65da5707a85cf3bf0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="regular-expression-activities"></a>Normal ifade etkinlikleri
Bu örnek, normal ifade işlevselliğini kullanıma sunabilir etkinlikleri kümesi oluşturmak gösterilmiştir <xref:System.Text.RegularExpressions> ad alanı. Bu özel etkinlikler bir iş akışı uygulama içinde kullanılabilir. Normal ifadeler hakkında daha fazla bilgi için bkz: [t:System.Text.RegularExpressions.Regex](http://go.microsoft.com/fwlink/?LinkId=150434) Namespace.  
  
 Aşağıdaki tabloda, bu örnekteki özel etkinlikler ayrıntıları verilmektedir.  
  
|Etkinlik|Açıklama|  
|--------------|-----------------|  
|IsMatch|Normal ifade bir girdi dizesindeki eşleşme olup olmadığını belirtir.|  
|Eşleşmeler|Normal bir ifade tüm oluşumları için giriş dizesi arar ve tüm başarılı eşleşenleri döndürür.|  
|Değiştir|Belirtilen giriş dizesi içinde belirtilen değiştirme dizesi ile bir normal ifade ile eşleşen dizelerini değiştirir.|  
  
## <a name="ismatch"></a>IsMatch  
 `IsMatch` Özel etkinlik döndürür `true` varsa `Input` dize özelliği, belirtilen normal ifadede bir eşleşme bulur `Pattern` özelliği. Etkinlik türetilen <xref:System.Activities.CodeActivity%601> ve içinde <xref:System.Activities.CodeActivity%601.Execute%2A> yöntem çağrılarını <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> yöntemi.  
  
 Aşağıdaki tabloda özellikleri ve dönüş değeri açıklanmaktadır `IsMatch` özel etkinlik.  
  
|Özellik veya dönüş değeri|Açıklama|  
|------------------------------|-----------------|  
|Desen (gerekli)|İle aramak için normal ifade.|  
|Giriş (gerekli)|Aramak için giriş dizesi.|  
|RegexOptions|Bit düzeyinde OR birleşimi [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) numaralandırma değerleri.|  
|Dönüş değeri|`true` Giriş sağlanan desende bir eşleşme bulursa; Aksi takdirde `false`.|  
  
 Aşağıdaki kod örneğinde nasıl kullanılacağı ortaya `IsMatch` özel etkinlik.  
  
```  
new IsMatch  
{  
    Pattern = new InArgument<string>( @"^-?\d+(\.\d{2})?$"),  
    Input = "20.00",  
};  
```  
  
## <a name="matches"></a>Eşleşmeler  
 `Matches` Özel etkinlik normal bir ifade tüm oluşumları için giriş dizesi arar ve tüm başarılı eşleşenleri döndürür. Etkinlik türetilen <xref:System.Activities.CodeActivity%601> ve içinde <xref:System.Activities.CodeActivity%601.Execute%2A> yöntem çağrılarını <xref:System.Text.RegularExpressions.Regex.Matches%2A> yöntemi.  
  
 Aşağıdaki tabloda özellikleri ve dönüş değeri açıklanmaktadır `IsMatch` özel etkinlik.  
  
|Özellik veya dönüş değeri|Açıklama|  
|------------------------------|-----------------|  
|Desen (gerekli)|İle aramak için normal ifade.|  
|Giriş (gerekli)|Aramak için giriş dizesi.|  
|RegexOptions|Bit düzeyinde OR birleşimi [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) numaralandırma değerleri.|  
|Dönüş Değeri|A <xref:System.Text.RegularExpressions.MatchCollection> başarılı eşleşmeleri koleksiyonunu içerir.|  
  
 Aşağıdaki kod örneğinde nasıl kullanılacağı ortaya `Matches` özel etkinlik.  
  
```  
new Matches  
{  
    Pattern = @"\b(?<word>\w+)\s+(\k<word>)\b",  
    Input = "The quick brown fox  fox jumped over over the lazy dog dog.",  
};  
```  
  
## <a name="replace"></a>Değiştir  
 `Replace` Özel etkinlik giriş dizesi arar ve bir dizeyle belirtilen normal ifadeyle eşleşen tüm dizelerini değiştirir. Etkinlik türetilen <xref:System.Activities.CodeActivity%601> ve içinde <xref:System.Activities.CodeActivity%601.Execute%2A> yöntem çağrılarını <xref:System.Text.RegularExpressions.Regex.Replace%2A> yöntemi.  
  
 Aşağıdaki tabloda özellikleri ve dönüş değeri açıklanmaktadır `Replace` özel etkinlik.  
  
|Özellik veya dönüş değeri|Açıklama|  
|------------------------------|-----------------|  
|Desen (gerekli)|İle aramak için normal ifade.|  
|Giriş (gerekli)|Aramak için giriş dizesi.|  
|Değiştirme|Değişim dizesi.<br /><br /> Varsa bir `Replacement` belirtilirse, sonra `MatchEvaluator` özelliği yoksayılır. Ya da `Replacement` veya `MatchEvaluator` özelliği ayarlanmalıdır.|  
|MatchEvaluator|Her eşleşme inceler ve özgün eşleşen dize veya bir değiştirme dizesi döndürür özel bir yöntem.<br /><br /> Varsa bir `Replacement` belirtilirse, sonra `MatchEvaluator` özelliği yoksayılır. Ya da `Replacement` veya `MatchEvaluator` özelliği ayarlanmalıdır.|  
|RegexOptions|Bit düzeyinde OR birleşimi [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) numaralandırma değerleri.|  
|Dönüş Değeri|A <xref:System.Text.RegularExpressions.MatchCollection> başarılı eşleşmeleri koleksiyonunu içerir.|  
  
 Aşağıdaki kod örneğinde nasıl kullanılacağı ortaya `Replace` özel etkinlik.  
  
```  
// Using the replacement string.  
new Replace  
{  
    Pattern = @"\bWorld\b",  
    Input = "Hello World! This is a wonderful World",  
    Replacement = "Universe"  
};  
  
// Using a match evaluator.  
new Replace  
{  
    Pattern = new InArgument<string>(pattern),  
    Input = new InArgument<string>(input),  
    MatchEvaluator = new MatchEvaluator(CapText)                  
};  
```  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], RegexActivities.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Çözümü çalıştırmak için CTRL + F5 tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Regex`