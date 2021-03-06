---
title: Birlikte Çalışma için Niteleyici .NET Türleri
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, qualifying .NET types
- qualifying .NET types for interoperation
- interoperation with unmanaged code, qualifying .NET types
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: 4b8afb52-fb8d-4e65-b47c-fd82956a3cdd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: baa5b9f250fe7117838f936b09b050ba500b7209
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="qualifying-net-types-for-interoperation"></a>Birlikte Çalışma için Niteleyici .NET Türleri
COM uygulamaları için derlemedeki türleri kullanıma sunmak istiyorsanız, tasarım zamanında COM birlikte çalışma gereksinimlerini göz önünde bulundurun. Aşağıdaki yönergelere uygun olduğunda yönetilen türler (sınıf, arabirim, yapısı ve numaralandırma) COM türleri ile sorunsuz tümleştirme:  
  
-   Sınıflar arabirimleri açıkça uygulamanız gerekir.  
  
     COM birlikte çalışma otomatik olarak sınıfın tüm üyeleri ve devralınabilir. taban sınıfı üyeleri içeren bir arabirim oluşturmak için bir mekanizma sağlasa da, açık arabirimler sağlamak çok daha iyidir. Otomatik olarak oluşturulan arabirimi sınıf arabirimi adı verilir. Yönergeler için bkz: [sınıf arabirimi Tanıtımı](com-callable-wrapper.md#introducing-the-class-interface).  
  
     Arabirim tanımları arabirimi tanım dili (IDL) veya eşdeğer kullanmak zorunda olmak yerine, kodunuzda birleştirmek için Visual Basic, C# ve C++ kullanabilirsiniz. Sözdizimi ayrıntılarını dil belgelerinize bakın.  
  
-   Yönetilen türler ortak olmalıdır.  
  
     Yalnızca genel türleri derlemedeki kayıtlı ve tür kitaplığı dışarı. Sonuç olarak, yalnızca genel türleri COM'a görülebilir  
  
     Türleri sunmaya özellikleri COM'a gösterilmeyen diğer yönetilen kod için yönetilen Örneğin, parametreli Oluşturucular, statik yöntemler ve sabit alanları COM istemcilere sunulmaz. Veri türü ve çalışma zamanı sıralar gibi Ayrıca, verileri kopyalanan ya da.  
  
-   Yöntemler, özellikler, alanları ve olayları ortak olmalıdır.  
  
     Genel tür üyeleri ayrıca COM'a görünür olmasını olmaları durumunda ortak olmalıdır Bir derlemeyi, genel bir tür ya da ortak bir türün genel üyeleri görünürlüğünü uygulayarak kısıtlayabilirsiniz <xref:System.Runtime.InteropServices.ComVisibleAttribute>. Varsayılan olarak, tüm genel türleri ve üyeleri görülebilir.  
  
-   Türleri COM'dan etkinleştirilmesi için bir ortak varsayılan oluşturucuya sahip olmalıdır  
  
     Yönetilen, genel türleri COM'a görünür Ancak, bir ortak varsayılan oluşturucu (bağımsız değişken içermeyen bir oluşturucuya) COM istemcileri türü oluşturulamıyor. Başka bir şekilde etkinleştirdiyseniz COM istemcileri türü kullanmaya devam edebilirsiniz.  
  
-   Türleri Özet olamaz.  
  
     COM istemcileri ne .NET istemcileri soyut türler oluşturabilirsiniz.  
  
 COM verildiğinde, yönetilen tür devralma hiyerarşisini düzleştirilmiş. Sürüm oluşturma da yönetilen ve yönetilmeyen ortamlar arasında farklılık gösterir. Com'a türleri yönetilen diğer türleri ile aynı sürüm özelliklere sahip değilsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>  
 [.NET Framework Bileşenlerini COM'da Gösterme](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [Sınıf arabirimi Tanıtımı](com-callable-wrapper.md#introducing-the-class-interface)  
 [Birlikte Çalışma Özniteliklerini Uygulama](../../../docs/framework/interop/applying-interop-attributes.md)  
 [COM için Bütünleştirilmiş Kod Paketleme](../../../docs/framework/interop/packaging-an-assembly-for-com.md)
