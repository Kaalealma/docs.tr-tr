---
title: Eş Kanal Senaryoları
ms.date: 03/30/2017
ms.assetid: dae6e0f7-900c-45ee-8be9-3647698382fb
ms.openlocfilehash: 42b16ea394b9375be14aed4b2792d306fcb62f2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="peer-channel-scenarios"></a>Eş Kanal Senaryoları
Eş kanal API'leri aşağıdaki geliştirme senaryolarını destekler.  
  
## <a name="publicationsubscription-messaging"></a>Yayımlama/abonelik Mesajlaşma  
 Yayımlama/abonelik uygulamalar (örneğin, yürütebilmektedir ve haber başlıklarına publishers puanlarını spor, hava durumu raporları için) yapı şirketler eş kanalı sunucusuz uygulamalar için kullanabilirsiniz. Örneğin, kullanıcıların yaygın bir kafes (veya istemcileri grubu) birleştirerek son Spor puanları edinin ve sunucu iş yükü artırmadan büyük miktarda güncel oyun veri yayılması. Bu, sunucu tabanlı teknolojiler yatırım artırmadan önemli ölçüde daha yüksek hizmet kalitesi vermek için veri sağlayıcısının yardımcı olur.  
  
## <a name="collaboration"></a>Birlikte çalışma  
 Bağımsız yazılım satıcılarının (ISV'ler), eşler arası etkinlikleri katılım sıkı grupları oluşturmak kişilere uygulamalar oluşturabilirsiniz. Örneğin, bu arkadaşlarınız, diğer planlama etkinlikleri ve daha fazla arasında resim paylaşımı işbirliği projeleri üzerinde çalışan ekiplere içerebilir. Geleneksel olarak, bu etkinliklerin her zaman sunucuları içeren; Ancak, eş kanalı geleneksel sunucu-istemci modeli altında kolayca uygulanmadı çevrimdışı erişim senaryoları etkinleştirerek maliyet açısından daha verimli bir şekilde bunu bir yol sağlar.  
  
## <a name="distributed-processing-and-compute-clusters"></a>Dağıtılan işleme ve hesaplama kümeleri  
 Hesaplama kümeleri ve dağıtılmış işlem genellikle finansal/modelleme ve İnsan DNA kod çözme hava durumu gibi büyük ölçekli hesaplamalardan kullanılır. Genellikle, bu sunucuları ayrı ayrı hesaplama Kümeye katılan tüm istemcilere görevleri atamak sağlayarak gerçekleştirilir. Bu sunucular ek taleplerini da olabilir; Örneğin, tüm görevler, belirli bir süre içinde her görev için birden fazla makine gerektiren tamamlanmış olması gerekebilir. Ayrıca, bir görev çalıştıran herhangi bir istemci kullanılamaz hale gelirse, başka bir istemci görev alabilir ve üzerinde çalışmayı gerçekleştirmek mümkün olması gerekir. Benzer şekilde, birden fazla istemci tutarlı sonuçlar sağlamak için aynı görev çalıştırmanız gerekebilir. Sunucular bu tür bir istemci koordinasyon çalıştırabilirsiniz, ancak burada bir görev bağımsız olarak alan istemcilerin görev geçici sunucu gereklilikleri ve bu görevin nasıl tamamlanacağını belirlemek için bir işlem kafes kullanın bir eşler arası çözüm oluşturabilirsiniz.  
  
## <a name="gaming"></a>Oyun  
 Eş kanal kullanarak, uygulama geliştiricilerinin burada oyun taşır için aktarılan ve diğer oyuncularla bir eşler arası mekanizması yerine bir merkezi sunucu üzerinden eşitlenen kendi oyunlar sunucusuz sürümlerini oluşturabilirsiniz. Küçük ISV'ler için bu dağıtma, sürdürme ve merkezi sunucuların bakımı ile ilişkili işlem maliyetlerini kaldırma yardımcı olur. Bir eşler arası mimarisi kullanılarak yazılmış oyunlar Internet üzerinden ya da kablolu veya kablosuz yerel ağlarda çalınabilir. Giriş ve oyun sohbet gibi ikincil oyun etkinlikleri bir eşler arası ağ kullanılarak geliştirilebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eş Kanal Kavramları](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md)
