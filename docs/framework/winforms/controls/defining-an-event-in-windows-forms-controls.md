---
title: Windows Forms Denetimlerinde Olay Tanımlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- events [Windows Forms], defining within Windows Forms custom controls
- custom controls [Windows Forms], events using code
ms.assetid: d89f1096-8061-42e2-a855-a1f053f1940a
ms.openlocfilehash: 552f2b8441ae5323f55f236fabb9f50f8f8b5ab0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="defining-an-event-in-windows-forms-controls"></a>Windows Forms Denetimlerinde Olay Tanımlama
Özel olaylar tanımlama hakkında daha fazla bilgi için bkz [olayları](../../../../docs/standard/events/index.md). Tüm ilişkili veriler sahip olmayan bir olay tanımlarsanız, olay verileri için temel türü kullanın <xref:System.EventArgs>ve <xref:System.EventHandler> olay temsilci olarak. Yapmak için kalan tek şey bir olay üye ve korumalı bir tanımlamak için `On` *EventName* olayını yöntemi.  
  
 Aşağıdaki kodda gösterildiği parçalara nasıl `FlashTrackBar` özel denetim tanımlayan özel bir olay `ValueChanged`. İçin tam kodu `FlashTrackBar` örnek için bkz: [nasıl yapılır: Windows Forms denetimi olduğunu gösteren ilerlemesi oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
```vb  
Option Explicit  
Option Strict  
  
Imports System  
Imports System.Windows.Forms  
Imports System.Drawing  
  
Public Class FlashTrackBar  
   Inherits Control  
  
   ' The event does not have any data, so EventHandler is adequate   
   ' as the event delegate.          
   ' Define the event member using the event keyword.  
   ' In this case, for efficiency, the event is defined   
   ' using the event property construct.  
   Public Event ValueChanged As EventHandler  
   ' The protected method that raises the ValueChanged   
   ' event when the value has actually   
   ' changed. Derived controls can override this method.    
   Protected Overridable Sub OnValueChanged(e As EventArgs)  
      RaiseEvent ValueChanged(Me, e)  
   End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Windows.Forms;  
using System.Drawing;  
  
public class FlashTrackBar : Control {  
   // The event does not have any data, so EventHandler is adequate   
   // as the event delegate.  
   private EventHandler onValueChanged;  
   // Define the event member using the event keyword.  
   // In this case, for efficiency, the event is defined   
   // using the event property construct.  
   public event EventHandler ValueChanged {  
            add {  
                onValueChanged += value;  
            }  
            remove {  
                onValueChanged -= value;  
            }  
        }  
   // The protected method that raises the ValueChanged  
   // event when the value has actually   
   // changed. Derived controls can override this method.    
   protected virtual void OnValueChanged(EventArgs e) {  
      if (ValueChanged != null) {  
         ValueChanged(this, e);  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms Denetimlerindeki Olaylar](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 [Olaylar](../../../../docs/standard/events/index.md)  
 [Olaylar](../../../../docs/standard/events/index.md)
