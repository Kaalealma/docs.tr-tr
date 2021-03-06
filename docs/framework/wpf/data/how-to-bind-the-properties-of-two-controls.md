---
title: 'Nasıl yapılır: İki Denetimin Özelliklerini Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: 02e71bfcc41fc3d256ea95381ed27d36b289b8f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-bind-the-properties-of-two-controls"></a>Nasıl yapılır: İki Denetimin Özelliklerini Bağlama
Bu örnek bir örneklenen denetim özelliği, başka bir bağlama gösterilmektedir <xref:System.Windows.Data.Binding.ElementName%2A> özelliği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl bağlanacağını gösterir <xref:System.Windows.Controls.Panel.Background%2A> özelliği bir <xref:System.Windows.Controls.Canvas> için <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A> özelliği bir <xref:System.Windows.Controls.ComboBox>:  
  
 [!code-xaml[BindDptoDp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 Bu örnek işlendiğinde aşağıdaki gibi görünür:  
  
 ![Yeşil arka plana sahip bir tuval](../../../../docs/framework/wpf/data/media/databindingbindingdpssample.PNG "DataBindingBindingDPsSample")  
  
 **Not** bağlama hedef özelliği (Bu örnekte, <xref:System.Windows.Controls.Panel.Background%2A> özelliği) bir bağımlılık özelliği olmalıdır. Daha fazla bilgi için bkz: [veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağlama Kaynağı Belirtme](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
