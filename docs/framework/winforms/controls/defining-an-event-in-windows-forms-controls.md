---
title: Defina um evento em controles
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- events [Windows Forms], defining within Windows Forms custom controls
- custom controls [Windows Forms], events using code
ms.assetid: d89f1096-8061-42e2-a855-a1f053f1940a
ms.openlocfilehash: 6799b229de8e8eb49dd3b8bbaffe0d08a32b7208
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142284"
---
# <a name="defining-an-event-in-windows-forms-controls"></a>Definindo um evento em controles dos Windows Forms
Para obter detalhes sobre a definição de eventos personalizados, consulte [Eventos](../../../standard/events/index.md). Se você definir um evento que não tenha dados associados, use o tipo de base para dados de eventos, <xref:System.EventArgs> e use <xref:System.EventHandler> como o delegado do evento. Tudo o que resta fazer é definir `On`um membro do evento e um método protegido *EventName* que levanta o evento.  
  
 O fragmento de código a seguir mostra como o controle personalizado `FlashTrackBar` define um evento personalizado, `ValueChanged`. Para obter o `FlashTrackBar` código completo para a amostra, consulte [o Controle de Como: Criar um Controle de Formulários do Windows que mostra o progresso](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
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
   protected virtual void OnValueChanged(EventArgs e)
   {  
       ValueChanged?.Invoke(this, e);  
   }  
}  
```  
  
## <a name="see-also"></a>Confira também

- [Eventos em controles do Windows Forms](events-in-windows-forms-controls.md)
- [Eventos](../../../standard/events/index.md)
