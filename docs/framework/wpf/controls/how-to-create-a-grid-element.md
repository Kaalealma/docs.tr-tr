---
title: 'Nasıl yapılır: Kılavuz Öğesi Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], creating [WPF], grid instance
ms.assetid: b2f07626-9df8-43b8-8d36-492f3cb42837
ms.openlocfilehash: 9fc70b8f15c4ecb4844c9c2ff4f7eeab94e7b906
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-grid-element"></a>Nasıl yapılır: Kılavuz Öğesi Oluşturma
## <a name="example"></a>Örnek  
 Aşağıdaki örnek oluşturma ve kullanma örneği gösterilmiştir <xref:System.Windows.Controls.Grid> kullanarak ya da [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] veya kod. Bu örnek üç kullanır <xref:System.Windows.Controls.ColumnDefinition> nesneleri ve üç <xref:System.Windows.Controls.RowDefinition> dokuz sahip bir kılavuz oluşturmak için hücreleri çalışma olduğu gibi nesneleri. Her hücre içeren bir <xref:System.Windows.Controls.TextBlock> veri ve en üst sıra temsil eden öğesi içeren bir <xref:System.Windows.Controls.TextBlock> ile <xref:System.Windows.Controls.Grid.ColumnSpan%2A> uygulanan özelliği. Her hücrenin sınırlarını göstermek için <xref:System.Windows.Controls.Grid.ShowGridLines%2A> özelliği etkin hale getirilir.  
  
 [!code-csharp[Grid#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Grid/CSharp/Grid_Code.cs#3)]
 [!code-vb[Grid#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Grid/VisualBasic/grid_vb.vb#3)]
 [!code-xaml[Grid#3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Grid/XAML/default.xaml#3)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.Grid>  
 [Panellere Genel Bakış](../../../../docs/framework/wpf/controls/panels-overview.md)
