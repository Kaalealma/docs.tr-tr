---
title: 'Nasıl yapılır: Düğme Oluşturmak için Otomatik Düzeni Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- Button controls [WPF], creating with automatic layout
- automatic layout [WPF], creating buttons
ms.assetid: 96c206d0-9e77-4784-9d2d-5045aed2021c
ms.openlocfilehash: 34b372e886b31e801b5598da90299f9815c47620
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-automatic-layout-to-create-a-button"></a>Nasıl yapılır: Düğme Oluşturmak için Otomatik Düzeni Kullanma
Bu örnek, otomatik düzen yaklaşımı yerelleştirilebilir bir uygulamada bir düğme oluşturmak için nasıl kullanılacağını açıklar.  
  
 Yerelleştirme bir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] uzun süren bir işlem olabilir. Yeniden boyutlandırma ve metin çevirme yanı sıra öğeleri yeniden konumlandırmak genellikle çevirmenlerin gerekir. Geçmişte her dil, bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] için gerekli ayarlama uyarlandığı. Şimdi özelliklerini ile [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ayarlama gereksinimini azaltan öğeler tasarlayabilirsiniz. Daha kolay yeniden boyutlandırılan ve konumlandırılabilir uygulamaları yazma yaklaşımına adlı `automatic layout`.  
  
 Aşağıdaki iki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnekler bir düğme; İngilizce metinle diğeri İspanyolca metinle örneği uygulamalar oluşturun. Kod metni dışında aynı olduğuna dikkat edin; Düğme metni uyacak şekilde ayarlar.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[LocalizationBtn_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 [!code-xaml[LocalizationBtn#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 Aşağıdaki grafikte kod örnekleri çıktısını gösterir.  
  
 ![Farklı dillerde aynı düğmenin](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")  
Otomatik yeniden boyutlandırılabilir düğmesi  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Otomatik Düzen Kullanımına Genel Bakış](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)  
 [Otomatik Düzen için Kılavuz Kullanma](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)
