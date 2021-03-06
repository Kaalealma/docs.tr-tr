---
title: DatePicker stilleri ve şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], DatePicker
- DatePicker [WPF], styles and templates
- templates [WPF], DatePicker
- parts [WPF], DatePicker
- styles [WPF], DatePicker
- states [WPF], DatePicker
ms.assetid: c430a657-692f-44bd-a549-2341f92d6115
ms.openlocfilehash: b50716cc83114fea5120b12659668437ac9bd6da
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2018
---
# <a name="datepicker-styles-and-templates"></a>DatePicker stilleri ve şablonları
Stilleri ve şablonları için bu konuda açıklanmaktadır <xref:System.Windows.Controls.DatePicker> denetim. Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetimi benzersiz bir görünüm vermek için. Daha fazla bilgi için bkz: [ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="datepicker-parts"></a>DatePicker bölümleri  
 Adlandırılmış bölümleri için aşağıdaki tabloda listelenmektedir <xref:System.Windows.Controls.DatePicker> denetim.  
  
|Bölümü|Tür|Açıklama|  
|-|-|-|  
|PART_Root|<xref:System.Windows.Controls.Grid>|Denetim kökü.|  
|PART_Button|<xref:System.Windows.Controls.Button>|Açar ve kapatır düğmesi <xref:System.Windows.Controls.Calendar>.|  
|PART_TextBox|<xref:System.Windows.Controls.Primitives.DatePickerTextBox>|Tarih girişi sayesinde metin kutusu.|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|İçin açılan <xref:System.Windows.Controls.DatePicker> denetim.|  
  
## <a name="datepicker-states"></a>DatePicker durumları  
 Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.DatePicker> denetim.  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Normal|CommonStates|Varsayılan durumu.|  
|Devre dışı|CommonStates|<xref:System.Windows.Controls.DatePicker> Devre dışı bırakılır.|  
|Geçerli|ValidationStates|Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.|  
  
## <a name="datepickertextbox-parts"></a>DatePickerTextBox bölümleri  
 Adlandırılmış bölümleri için aşağıdaki tabloda listelenmektedir <xref:System.Windows.Controls.Primitives.DatePickerTextBox> denetim.  
  
|Bölümü|Tür|Açıklama|  
|-|-|-|  
|PART_Watermark|<xref:System.Windows.Controls.ContentControl>|İlk metin içeren öğeyi <xref:System.Windows.Controls.DatePicker>.|  
|PART_ContentElement|<xref:System.Windows.FrameworkElement>|İçerebilir bir görsel öğe bir <xref:System.Windows.FrameworkElement>. Metnin <xref:System.Windows.Controls.TextBox> bu öğesinde görüntülenir.|  
  
## <a name="datepickertextbox-states"></a>DatePickerTextBox durumları  
 Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.Primitives.DatePickerTextBox> denetim.  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Normal|CommonStates|Varsayılan durumu.|  
|Devre dışı|CommonStates|<xref:System.Windows.Controls.Primitives.DatePickerTextBox> Devre dışı bırakılır.|  
|Fare üzerinde|CommonStates|Fare işaretçisini üzerine getirildiği <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.|  
|ReadOnly|CommonStates|Kullanıcı metni değiştiremez <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.|  
|Odaklanmış|FocusStates|Denetimi odağa sahip.|  
|Odaksız|FocusStates|Denetim odağı yok.|  
|Filigran|WatermarkStates|Denetim ilk metin görüntüler.  <xref:System.Windows.Controls.Primitives.DatePickerTextBox> Durumda kullanıcı olmayan metin girildiğinde veya bir tarih seçtiniz.|  
|Unwatermarked|WatermarkStates|Metne kullanıcının girdiği <xref:System.Windows.Controls.Primitives.DatePickerTextBox> veya bir tarih olarak seçilen <xref:System.Windows.Controls.DatePicker>.|  
|Geçerli|ValidationStates|Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.|  
  
## <a name="datepicker-controltemplate-example"></a>DatePicker ControlTemplate Örneği  
 Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.DatePicker> denetim.  
  
 [!code-xaml[ControlTemplateExamples#DatePicker](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datepicker.xaml#datepicker)]  
  
 Önceki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Tam bir örnek için bkz: [ControlTemplates örneği ile stil oluşturma](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [Denetim Stilleri ve Şablonları](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [Denetim Özelleştirme](../../../../docs/framework/wpf/controls/control-customization.md)  
 [Stil ve Şablon Oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
