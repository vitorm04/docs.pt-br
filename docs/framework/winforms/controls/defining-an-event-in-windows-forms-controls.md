---
title: Definindo um evento em controles dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- events [Windows Forms], defining within Windows Forms custom controls
- custom controls [Windows Forms], events using code
ms.assetid: d89f1096-8061-42e2-a855-a1f053f1940a
ms.openlocfilehash: 60ae01ca63f895bfb1c7aabbe3337596cd13933d
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43867206"
---
# <a name="defining-an-event-in-windows-forms-controls"></a><span data-ttu-id="498a1-102">Definindo um evento em controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="498a1-102">Defining an Event in Windows Forms Controls</span></span>
<span data-ttu-id="498a1-103">Para obter detalhes sobre como definir eventos personalizados, consulte [eventos](../../../../docs/standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="498a1-103">For details about defining custom events, see [Events](../../../../docs/standard/events/index.md).</span></span> <span data-ttu-id="498a1-104">Se você definir um evento que não tenha dados associados, use o tipo de base para dados de eventos, <xref:System.EventArgs> e use <xref:System.EventHandler> como o delegado do evento.</span><span class="sxs-lookup"><span data-stu-id="498a1-104">If you define an event that does not have any associated data, use the base type for event data, <xref:System.EventArgs>, and use <xref:System.EventHandler> as the event delegate.</span></span> <span data-ttu-id="498a1-105">Tudo o que resta a fazer é definir um membro de evento e uma planilha protegida `On` *EventName* método que gera o evento.</span><span class="sxs-lookup"><span data-stu-id="498a1-105">All that remains to do is to define an event member and a protected `On`*EventName* method that raises the event.</span></span>  
  
 <span data-ttu-id="498a1-106">O fragmento de código a seguir mostra como o controle personalizado `FlashTrackBar` define um evento personalizado, `ValueChanged`.</span><span class="sxs-lookup"><span data-stu-id="498a1-106">The following code fragment shows how the `FlashTrackBar` custom control defines a custom event, `ValueChanged`.</span></span> <span data-ttu-id="498a1-107">Para o código completo para o `FlashTrackBar` de exemplo, consulte a [como: criar um Windows Forms controle que mostra o progresso](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span><span class="sxs-lookup"><span data-stu-id="498a1-107">For the complete code for the `FlashTrackBar` sample, see the [How to: Create a Windows Forms Control That Shows Progress](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="498a1-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="498a1-108">See also</span></span>

- [<span data-ttu-id="498a1-109">Eventos em controles do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="498a1-109">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)
- [<span data-ttu-id="498a1-110">Eventos</span><span class="sxs-lookup"><span data-stu-id="498a1-110">Events</span></span>](../../../../docs/standard/events/index.md)
