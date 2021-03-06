---
title: 'Nasıl yapılır: Windows Forms MonthCalendar Denetiminde Tarih Aralığı Seçme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- dates [Windows Forms], selecting range in calendar controls
- examples [Windows Forms], calendar controls
- calendars [Windows Forms], selecting date range
- MonthCalendar control [Windows Forms], selecting date range
ms.assetid: 95d9ab95-b0f8-4c19-9f63-b5cd4593a5d0
ms.openlocfilehash: 8b6d64fcffb02c4496cff3f2821861117b0062fd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control"></a>Nasıl yapılır: Windows Forms MonthCalendar Denetiminde Tarih Aralığı Seçme
Windows Forms, önemli özelliklerinden <xref:System.Windows.Forms.MonthCalendar> denetimidir kullanıcı tarih aralığını seçebilirsiniz. Bu özellik bir geliştirme Tarih Seçimi özelliğidir <xref:System.Windows.Forms.DateTimePicker> yalnızca bir tek tarih/saat değeri seçmek kullanıcının sağlayan denetim. Bir tarih aralığı ayarlamak veya özelliklerini kullanarak kullanıcı tarafından ayarlanan bir seçim aralığı alma <xref:System.Windows.Forms.MonthCalendar> denetim. Aşağıdaki kod örneğinde, seçim aralığı ayarlamak gösterilmiştir.  
  
### <a name="to-select-a-range-of-dates"></a>Bir tarih aralığı seçin  
  
1.  Oluşturma <xref:System.DateTime> bir aralıktaki ilk ve son tarihleri gösteren nesne.  
  
    ```vb  
    Dim projectStart As Date = New DateTime(2001, 2, 13)  
    Dim projectEnd As Date = New DateTime(2001, 2, 28)  
    ```  
  
    ```csharp  
    DateTime projectStart = new DateTime(2001, 2, 13);  
    DateTime projectEnd = new DateTime(2001, 2, 28);  
    ```  
  
    ```cpp  
    DateTime projectStart = DateTime(2001, 2, 13);  
    DateTime projectEnd = DateTime(2001, 2, 28);  
    ```  
  
2.  Ayarlama <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> özelliği.  
  
    ```vb  
    MonthCalendar1.SelectionRange = New SelectionRange(projectStart, projectEnd)  
    ```  
  
    ```csharp  
    monthCalendar1.SelectionRange = new SelectionRange(projectStart, projectEnd);  
    ```  
  
    ```cpp  
    monthCalendar1->SelectionRange = gcnew  
       SelectionRange(projectStart, projectEnd);  
    ```  
  
     – veya –  
  
     Ayarlama <xref:System.Windows.Forms.MonthCalendar.SelectionStart%2A> ve <xref:System.Windows.Forms.MonthCalendar.SelectionEnd%2A> özellikleri.  
  
    ```vb  
    MonthCalendar1.SelectionStart = projectStart  
    MonthCalendar1.SelectionEnd = projectEnd  
    ```  
  
    ```csharp  
    monthCalendar1.SelectionStart = projectStart;  
    monthCalendar1.SelectionEnd = projectEnd;  
    ```  
  
    ```cpp  
    monthCalendar1->SelectionStart = projectStart;  
    monthCalendar1->SelectionEnd = projectEnd;  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [MonthCalendar Denetimi](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [Nasıl yapılır: Windows Forms MonthCalendar Denetiminin Görünüşünü Değiştirme](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)  
 [Nasıl yapılır: Windows Forms MonthCalendar Denetimi ile Belirli Günleri Kalın Olarak Görüntüleme](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)  
 [Nasıl yapılır: Windows Forms MonthCalendar Denetiminde Birden Fazla Ay Görüntüleme](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)
