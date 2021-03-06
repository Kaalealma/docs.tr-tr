---
title: 'Nasıl yapılır: FlowDocument Sütun Ayırıcı Öznitelikleri Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- FlowDocument column-separating attributes
- column-separating attributes
- documents [WPF], FlowDocument column-separating attributes
ms.assetid: c7a822f8-aeca-45bd-a258-2852ff28005c
ms.openlocfilehash: 678e01a35c286ea03f0385291d64f2f900f068c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-flowdocument-column-separating-attributes"></a>Nasıl yapılır: FlowDocument Sütun Ayırıcı Öznitelikleri Kullanma
Bu örnek, sütun ayırıcı özelliklerinin nasıl kullanılacağını gösterir bir <xref:System.Windows.Documents.FlowDocument>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek tanımlayan bir <xref:System.Windows.Documents.FlowDocument>ve ayarlar <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, ve <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> öznitelikleri.  <xref:System.Windows.Documents.FlowDocument> Örnek içeriğin tek bir paragraf içerir.  
  
 [!code-xaml[FlowDocumentSnippets#_FlowDocumentColumnStuffXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml#_flowdocumentcolumnstuffxaml)]  
  
 Aşağıdaki şekilde gösterilmiştir etkilerini <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, ve <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> öznitelikleri işlenmiş <xref:System.Windows.Documents.FlowDocument>.  
  
 ![Ekran görüntüsü: FlowDocument Sütun içi](../../../../docs/framework/wpf/advanced/media/flowdocumentintracolumn.png "FlowDocumentIntraColumn")
