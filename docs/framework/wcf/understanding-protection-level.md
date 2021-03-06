---
title: Koruma Düzeylerini Anlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
- ProtectionLevel property
ms.assetid: 0c034608-a1ac-4007-8287-b1382eaa8bf2
ms.openlocfilehash: 157e660a8b4d3866b9ab1994c409f82f16ac8359
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="understanding-protection-level"></a>Koruma Düzeylerini Anlama
`ProtectionLevel` Özelliği bulundu birçok farklı sınıflarında gibi <xref:System.ServiceModel.ServiceContractAttribute> ve <xref:System.ServiceModel.OperationContractAttribute> sınıfları. Özelliği bir ileti bölümü (veya tam) nasıl korumalı denetler. Bu konuda, Windows Communication Foundation (WCF) özelliği ve nasıl çalıştığı açıklanmaktadır.  
  
 Koruma düzeyini ayarlama ile ilgili yönergeler için bkz: [nasıl yapılır: ProtectionLevel özelliğini ayarlama](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md).  
  
> [!NOTE]
>  Koruma düzeyleri yalnızca yapılandırmada yok kod ayarlanabilir.  
  
## <a name="basics"></a>temel kavramları  
 Koruma düzeyi özelliği anlamak için aşağıdaki temel ifadeler geçerlidir:  
  
-   Koruma üç temel düzeyde bir ileti, herhangi bir bölümünü mevcut. (Bunu yerde oluşur) özelliği birine ayarlayın <xref:System.Net.Security.ProtectionLevel> numaralandırma değerleri. Koruma artan içerirler:  
  
    -   `None`.  
  
    -   `Sign`. Korumalı bölümü dijital olarak imzalanır. Bu, herhangi bir korumalı iletiyi bölümüyle değiştirme algılanamadı sağlar.  
  
    -   `EncryptAndSign`. İleti bölümü imzalanmış olduğu önce gizliliğini sağlamak için şifrelenir.  
  
-   Koruma gereksinimleri yalnızca ayarlayabilirsiniz *uygulama verilerini* bu özellik ile. Örneğin, WS-adresleme üstbilgileri altyapı verileri ve, bu nedenle, etkilenmez `ProtectionLevel`.  
  
-   Güvenlik modu ayarlandığında `Transport`, tüm ileti aktarım mekanizması tarafından korunur. Bu nedenle, bir iletinin farklı bölümleri için ayrı koruma düzeyini ayarlama hiçbir etkisi olmaz.  
  
-   `ProtectionLevel` Ayarlamak için geliştiriciye için bir yoldur *düşük düzeyde* , bağlama uymanız gerekir. Bir hizmet dağıtıldığında, yapılandırmada belirtilen gerçek bağlama olabilir veya düşük düzeyde desteklemeyebilir. Örneğin, varsayılan olarak, <xref:System.ServiceModel.BasicHttpBinding> sınıfı (zaman etkinleştirilebilir rağmen) güvenlik sağlamıyorsa. Bu nedenle, hiçbir ayarı dışında olan sözleşme ile kullanarak `None` bir özel durum oluşturulmasına neden olur.  
  
-   Hizmet gerektiriyorsa en düşük `ProtectionLevel` için tüm iletileri `Sign`, (belki de bir WCF olmayan teknoloji tarafından oluşturulan) bir istemci şifrelemek ve tüm iletileri imzalamak (birden çok gereken en düşük olduğu). Bu durumda, WCF, istemci en düşük düzeyde birden fazla yapmıştır olduğundan, bir özel durum oluşturmayacaksa. Ancak, WCF uygulamaları (Hizmetleri veya istemciler) bir ileti bölümü mümkünse aşırı güvenliğini sağlamaz ancak en düşük düzeyi ile uyumlu unutmayın. Kullanırken ayrıca `Transport` daha ayrıntılı bir düzeyde güvenli kendiliğinden alamıyor çünkü güvenlik modu olarak taşıma ileti akışı aşırı güvenli.  
  
-   Ayarlarsanız `ProtectionLevel` açıkça ya da için `Sign` veya `EncryptAndSign`bir özel durum veya güvenliği etkinleştirilmiş bir bağlama sonra kullanmanız gerekir.  
  
-   Güvenlik sağlayan bir bağlama seçerseniz ve ayarlanmamış `ProtectionLevel` veri şifrelenir ve imzalanmış tüm uygulama sözleşme üzerinde herhangi bir yere özelliği.  
  
-   Etkin güvenliğe sahip olmayan bir bağlama seçeneğini belirlerseniz (örneğin, `BasicHttpBinding` sınıfı varsayılan olarak devre dışı güvenlik sahiptir) ve `ProtectionLevel` hiçbiri uygulama verilerinin korumalı sonra açıkça, ayarlı değil.  
  
-   Aktarım düzeyinde güvenlik uygulayan bir bağlama kullanıyorsanız, tüm uygulama verilerini taşıma özelliklerine göre güvenli.  
  
-   İleti düzeyinde güvenlik uygulayan bir bağlama kullanırsanız, sonra uygulama verileri sözleşmenin ayarlamak koruma düzeyleri göre güvenli hale. İletileri tüm uygulama verileri şifrelenir ve imzalanmış sonra bir koruma düzeyi belirtmezseniz.  
  
-   `ProtectionLevel` Kapsam farklı düzeylerde ayarlanabilir. Yoktur, sonraki bölümde açıklanan kapsamı ile ilişkilendirilmiş bir hiyerarşi.  
  
## <a name="scoping"></a>Kapsamı  
 Ayarı `ProtectionLevel` en üstteki API düzeyini altındaki tüm düzeyleri için ayarlar. Varsa `ProtectionLevel` için farklı bir değer hiyerarşi düzeyi şimdi yeni düzeye sıfırlanacak daha düşük düzeyde, aşağıdaki tüm API'leri ayarlayın (ancak, API, yukarıda hala etkilenir en üstteki düzeyine göre). Hiyerarşi aşağıdaki gibidir. Aynı düzeyde öznitelikleri, eş görüntülenir.  
  
 <xref:System.ServiceModel.ServiceContractAttribute>  
  
 <xref:System.ServiceModel.OperationContractAttribute>  
  
 <xref:System.ServiceModel.FaultContractAttribute>  
  
 <xref:System.ServiceModel.MessageContractAttribute>  
  
 <xref:System.ServiceModel.MessageHeaderAttribute>  
  
 <xref:System.ServiceModel.MessageBodyMemberAttribute>  
  
## <a name="programming-protectionlevel"></a>Programlama ProtectionLevel  
 Programa `ProtectionLevel` hiyerarşideki herhangi bir noktada yalnızca özelliği uygun bir değer için öznitelik uygularken ayarlayın. Örnekler için bkz: [nasıl yapılır: ProtectionLevel özelliğini ayarlama](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md).  
  
> [!NOTE]
>  Özellik, hataları ve sözleşmeleri gerektiriyor bu özellikleri nasıl çalıştığını anlamak iletisi ayarlama. Daha fazla bilgi için bkz: [nasıl yapılır: ProtectionLevel özelliğini ayarlama](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md) ve [kullanarak ileti sözleşmeleri](../../../docs/framework/wcf/feature-details/using-message-contracts.md).  
  
## <a name="ws-addressing-dependency"></a>Bağımlılık WS adresleme  
 Çoğu durumda, kullanarak [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) bir istemci oluşturmak için istemci ve hizmet sözleşmeleri aynı olmasını sağlar. Ancak, görünen aynı sözleşmeleri bir özel durum istemciye neden olabilir. Bu bağlama WS adresleme belirtimini desteklemez ve koruma birden çok düzeyi sözleşmesinde belirtilen her gerçekleşir. Örneğin, <xref:System.ServiceModel.BasicHttpBinding> sınıfı belirtimini desteklemez veya oluşturursanız, bağlama özel bir WS adresleme desteklemiyor. `ProtectionLevel` Farklı koruma düzeyleri tek sözleşmesindeki etkinleştirmek için WS adresleme belirtimi özelliğini kullanır. Bağlama WS adresleme belirtimi desteklemiyorsa, tüm düzeyler aynı koruma düzeyini ayarlanır. Etkili koruma düzeyi sözleşmesindeki tüm kapsamlar için güçlü koruma düzeyi sözleşmesinde kullanılan şekilde ayarlanacak.  
  
 Bu, ilk bakışta hata ayıklamak sabit bir sorunu neden olabilir. Birden fazla hizmet için yöntemleri içeren bir istemci Sözleşme (bir arabirim) oluşturmak mümkündür. Diğer bir deyişle, aynı arabirimi birçok Hizmetleri ile iletişim kuran bir istemci oluşturmak için kullanılır ve tek bir arabirim tüm hizmetler için yöntemler içerir. Geliştirici her belirli bir hizmet için geçerli olan yöntemleri çağırmak için bu nadir senaryoda ilgilenebilmek gerekir. Bağlama <xref:System.ServiceModel.BasicHttpBinding> sınıfı, birden çok koruma düzeyleri olamaz desteklenir. Ancak, istemciye yanıtlama hizmet gerekli daha düşük bir koruma düzeyine sahip bir istemci yanıt vermeyebilir. Bu durumda, daha yüksek bir koruma düzeyi beklediği istemci bir özel durum oluşturur.  
  
 Kod örneği, bu sorun gösterilmektedir. Aşağıdaki örnek, bir hizmet ve istemci sözleşme gösterir. Bağlama olduğunu varsayın [ \<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) öğesi. Bu nedenle, bir sözleşme tüm işlemler aynı koruma düzeyine sahip. Bu Tekdüzen koruma düzeyi, tüm işlemler arasındaki en yüksek koruma düzeyi olarak belirlenir.  
  
 Hizmet sözleşmesi şöyledir:  
  
 [!code-csharp[c_ProtectionLevel#7](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#7)]
 [!code-vb[c_ProtectionLevel#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#7)]  
  
 Aşağıdaki kod istemci sözleşme arabirimi gösterir. İçerdiği Not bir `Tax` farklı bir hizmet ile kullanılmak üzere tasarlanmıştır yöntemi:  
  
 [!code-csharp[c_ProtectionLevel#8](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#8)]
 [!code-vb[c_ProtectionLevel#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#8)]  
  
 İstemci çağırdığında `Price` yöntemi, onu aykırı hizmetinden bir yanıt aldığında. Bu istemci belirtmediği nedeniyle oluşur bir `ProtectionLevel` üzerinde `ServiceContractAttribute`, ve istemcisi, varsayılan olarak, bu nedenle kullanır (<xref:System.Net.Security.ProtectionLevel.EncryptAndSign>) dahil olmak üzere tüm yöntemleri için `Price` yöntemi. Ancak, hizmeti değerini kullanarak döndürür <xref:System.Net.Security.ProtectionLevel.Sign> hizmet sözleşmesi ayarlamak koruma düzeyi sahip tek bir yöntem tanımladığından düzey <xref:System.Net.Security.ProtectionLevel.Sign>. Bu durumda, istemci hizmetinden gelen yanıt doğrulanırken bir hata atar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 <xref:System.ServiceModel.FaultContractAttribute>  
 <xref:System.ServiceModel.MessageContractAttribute>  
 <xref:System.ServiceModel.MessageHeaderAttribute>  
 <xref:System.ServiceModel.MessageBodyMemberAttribute>  
 <xref:System.Net.Security.ProtectionLevel>  
 [Hizmetleri Güvenli Hale Getirme](../../../docs/framework/wcf/securing-services.md)  
 [Nasıl yapılır: ProtectionLevel Özelliğini Ayarlama](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md)  
 [Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)  
 [İleti Anlaşmaları Kullanma](../../../docs/framework/wcf/feature-details/using-message-contracts.md)
