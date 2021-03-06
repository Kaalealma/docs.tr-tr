---
title: Güvenlik ve Kullanıcı Girdisi
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], user input
- user input, security
- secure coding, user input
- code security, user input
ms.assetid: 9141076a-96c9-4b01-93de-366bb1d858bc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 858ee30479c959f30673725b4ba8088fcc2d8f3b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="security-and-user-input"></a>Güvenlik ve Kullanıcı Girdisi
Herhangi türde bir giriş (bir Web isteği veya URL, bir Microsoft Windows Forms uygulaması ve benzeri denetimleri için giriş verileri), genellikle bu verilere doğrudan parametre olarak başka bir kod çağırmak için kullanıldığından kod olumsuz yönde etkileyebilir kullanıcı verileri. Bu durum kötü amaçlı kod kodunuzu garip parametrelerle çağırma paraleldir ve aynı önlemler yapılması gerekir. Kullanıcı girişi gerçekten zor olduğu için büyük olasılıkla güvenilmeyen veri izlemek için hiçbir yığın çerçevesi güvenli olmasını sağlamaktır.  
  
 Bunlar, bunlar için başka bir kod aracılığıyla hatalı veri iletmek için bir ağ geçidi, güvenlik görünen ilgisiz olan kod bulunabilir ancak çünkü bulmak için belirsiz ve en zor güvenlik hatalar arasındadır. Bu hatalar için aramak için herhangi bir giriş verisi türünü izleyin, ne olası değerleri aralığı olabilir ve bu verileri görmesini kodu tüm durumlarda işlenip işlenmeyeceğini göz önünde bulundurun düşünün. Denetleme ve kod işleyemiyor herhangi bir giriş reddetme aralığı üzerinden bu hataları düzeltebilir.  
  
 Kullanıcı verilerini içeren bazı önemli noktalar şunlardır:  
  
-   Sunucu yanıtı herhangi bir kullanıcı verisini istemcide sunucunun site bağlamında çalışır. Web sunucunuzun kullanıcı verileri alır ve döndürülen Web sayfasına ekler, örneğin, dahil bir  **\<komut dosyası >** etiketi ve sunucudan gibi çalıştırın.  
  
-   İstemcinin herhangi bir URL isteyebileceği unutmayın.  
  
-   Hassas ya da geçersiz yolları göz önünde bulundurun:  
  
    -   .. \, aşırı uzun yolları.  
  
    -   Joker karakter (*) kullanın.  
  
    -   Belirteç genişletme (% belirteci %).  
  
    -   Garip formları özel bir anlamı olan yol.  
  
    -   Dosya sistemi akışı adları gibi alternatif `filename::$DATA`.  
  
    -   Dosya adlarının sürümleri gibi kısa `longfi~1` için `longfilename`.  
  
-   Eval(UserData) herhangi bir şey yapabileceğinizi unutmayın.  
  
-   Bazı kullanıcı verilerini içeren bir ad olarak geç bağlama dikkatli olun.  
  
-   Web verilerle çalışıyorsanız dahil olmak üzere izin verilen, çıkışları çeşitli biçimlerde göz önünde bulundurun:  
  
    -   Onaltılık çıkışları (% nn).  
  
    -   Unicode çıkışları (% nnn).  
  
    -   Overlong UTF-8 çıkışları (% nn % nn).  
  
    -   Çift kaçış karakterleri (% nn % mm '%' kaçış olduğu % mmnn olur).  
  
-   Birden fazla kurallı biçimi olabilecek kullanıcı adlarını dikkatli olun. Örneğin, genellikle ya da MYDOMAIN kullanabilirsiniz\\*kullanıcıadı* form veya *kullanıcıadı* @mydomain.example.com formu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenli Kodlama Yönergeleri](../../../docs/standard/security/secure-coding-guidelines.md)
