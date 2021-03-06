---
title: Güvenlik ve Yarış Durumları
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], race conditions
- race conditions
- secure coding, race conditions
- code security, race conditions
ms.assetid: ea3edb80-b2e8-4e85-bfed-311b20cb59b6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fdfc4d9e9ba3653bd1a762767e3c39a4f62e587a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="security-and-race-conditions"></a>Güvenlik ve Yarış Durumları
Başka bir sorun olası güvenlik açıklarını yarış durumları tarafından yararlanan alanıdır. Bu durum oluşabilir birkaç yolu vardır. İzleyin konuları Geliştirici kaçınmalısınız ana Tuzaklar bazıları verilmiştir.  
  
## <a name="race-conditions-in-the-dispose-method"></a>Dispose yöntemi yarış durumları  
 Bir sınıf, kullanıcının **Dispose** yöntemi (daha fazla bilgi için bkz: [çöp toplama](../../../docs/standard/garbage-collection/index.md)) olan eşitlenmiş değil, mümkündür içinde kodu Temizleme **Dispose** çalıştırılabilir birden fazla Aşağıdaki örnekte gösterildiği gibi bir kez.  
  
```vb  
Sub Dispose()  
    If Not (myObj Is Nothing) Then  
       Cleanup(myObj)  
       myObj = Nothing  
    End If  
End Sub  
```  
  
```csharp  
void Dispose()   
{  
    if( myObj != null )   
    {  
        Cleanup(myObj);  
        myObj = null;  
    }  
}  
```  
  
 Çünkü bu **Dispose** uygulama eşitlenmemiş, mümkündür `Cleanup` önce bir iş parçacığı ve ardından ikinci bir iş parçacığı önce çağrılacak `_myObj` ayarlanır **null**. Bu bir güvenlik sorunu olup olmadığını bağlıdır ne olacağını zaman `Cleanup` kodu çalıştırır. Eşitlenmemiş bir önemli sorun **Dispose** uygulamaları dosyaları gibi kaynak tanıtıcıları kullanımını içerir. Hatalı elden, genellikle güvenlik açıkları için müşteri adayları kullanılmak üzere yanlış tanıtıcı neden olabilir.  
  
## <a name="race-conditions-in-constructors"></a>Yapıcılardaki yarış durumları  
 Bazı uygulamalarda, kendi sınıf oluşturucular tamamen çalıştırmadan önce sınıf üyeleri erişmek başka bir iş parçacığı için mümkün olabilir. Bu ortaya veya gerekiyorsa, iş parçacığı eşitleme hiçbir güvenlik sorunları olduğundan emin olmak için tüm sınıf oluşturucular gözden geçirmelidir.  
  
## <a name="race-conditions-with-cached-objects"></a>Önbelleğe alınan nesnelerle yarış durumları  
 Güvenlik bilgileri önbelleğe alır veya kod erişim güvenliği kullanan kodu [Assert](../../../docs/framework/misc/using-the-assert-method.md) işlemi de olabilir yarış durumları savunmasız sınıfı diğer bölümleri uygun şekilde eşitlenmemişse, aşağıdaki örnekte gösterildiği gibi.  
  
```vb  
Sub SomeSecureFunction()  
    If SomeDemandPasses() Then  
        fCallersOk = True  
        DoOtherWork()  
        fCallersOk = False()  
    End If  
End Sub  
  
Sub DoOtherWork()  
    If fCallersOK Then  
        DoSomethingTrusted()  
    Else  
        DemandSomething()  
        DoSomethingTrusted()  
    End If  
End Sub  
```  
  
```csharp  
void SomeSecureFunction()   
{  
    if(SomeDemandPasses())   
    {  
        fCallersOk = true;  
        DoOtherWork();  
        fCallersOk = false();  
    }  
}  
void DoOtherWork()   
{  
    if( fCallersOK )   
    {  
        DoSomethingTrusted();  
    }  
    else   
    {  
        DemandSomething();  
        DoSomethingTrusted();  
    }  
}  
```  
  
 Diğer yolları varsa `DoOtherWork` aynı nesneye sahip başka bir iş parçacığından çağrılabilir, güvenilmeyen bir çağıran bir isteğe bağlı irsaliyesi.  
  
 Kodunuzu güvenlik bilgileri önbelleğe alır, bu güvenlik açığı gözden emin olun.  
  
## <a name="race-conditions-in-finalizers"></a>Sonlandırıcılar yarış durumları  
 Yarış durumları sonra onun sonlandırıcıyı boşaltır statik veya yönetilmeyen bir kaynağa başvuran bir nesnedeki da oluşabilir. Birden çok nesne sınıf sonlandırıcıyı yönetilebilir bir kaynak paylaşıyorsanız, nesneleri bu kaynağa hiçbir erişim eşitlemeniz gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenli Kodlama Yönergeleri](../../../docs/standard/security/secure-coding-guidelines.md)
