---
title: Visão geral de manipuladores de eventos
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, event handling
- event handling [Windows Forms], Windows Forms
- event handlers [Windows Forms], about event handlers
ms.assetid: 228112e1-1711-42ee-8ffa-ff3555bffe66
ms.openlocfilehash: ffec8a9f8e080dec78152e62e00e2dceefbdaab0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141686"
---
# <a name="event-handlers-overview-windows-forms"></a><span data-ttu-id="5775e-102">Visão geral de manipuladores de eventos (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="5775e-102">Event Handlers Overview (Windows Forms)</span></span>
<span data-ttu-id="5775e-103">Um manipulador de eventos é um método que está associado a um evento.</span><span class="sxs-lookup"><span data-stu-id="5775e-103">An event handler is a method that is bound to an event.</span></span> <span data-ttu-id="5775e-104">Quando o evento é gerado, o código no manipulador de eventos é executado.</span><span class="sxs-lookup"><span data-stu-id="5775e-104">When the event is raised, the code within the event handler is executed.</span></span> <span data-ttu-id="5775e-105">Cada manipulador de eventos fornece dois parâmetros que permitem manipular o evento corretamente.</span><span class="sxs-lookup"><span data-stu-id="5775e-105">Each event handler provides two parameters that allow you to handle the event properly.</span></span> <span data-ttu-id="5775e-106">O exemplo a seguir mostra <xref:System.Windows.Forms.Button> um <xref:System.Windows.Forms.Control.Click> manipulador de eventos para um evento de controle.</span><span class="sxs-lookup"><span data-stu-id="5775e-106">The following example shows an event handler for a <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event.</span></span>  
  
```vb  
Private Sub button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles button1.Click  
  
End Sub  
```  
  
```csharp  
private void button1_Click(object sender, System.EventArgs e)
{  
  
}  
```  
  
```cpp  
private:  
  void button1_Click(System::Object ^ sender,  
    System::EventArgs ^ e)  
  {  
  
  }  
```  
  
 <span data-ttu-id="5775e-107">No primeiro parâmetro, `sender`, fornece uma referência ao objeto que gerou o evento.</span><span class="sxs-lookup"><span data-stu-id="5775e-107">The first parameter,`sender`, provides a reference to the object that raised the event.</span></span> <span data-ttu-id="5775e-108">No exemplo acima, o segundo parâmetro, `e`, passa um objeto específico para o evento que está sendo manipulado.</span><span class="sxs-lookup"><span data-stu-id="5775e-108">The second parameter, `e`, in the example above, passes an object specific to the event that is being handled.</span></span> <span data-ttu-id="5775e-109">Consultando as propriedades do objeto (e, às vezes, seus métodos), é possível obter informações como o local do mouse para eventos de mouse ou dados que estão sendo transferidos em eventos do tipo "arrastar e soltar".</span><span class="sxs-lookup"><span data-stu-id="5775e-109">By referencing the object's properties (and, sometimes, its methods), you can obtain information such as the location of the mouse for mouse events or data being transferred in drag-and-drop events.</span></span>  
  
 <span data-ttu-id="5775e-110">Normalmente, cada evento produz um manipulador de eventos com um tipo de objeto de evento diferente para o segundo parâmetro.</span><span class="sxs-lookup"><span data-stu-id="5775e-110">Typically each event produces an event handler with a different event-object type for the second parameter.</span></span> <span data-ttu-id="5775e-111">Alguns manipuladores de eventos, <xref:System.Windows.Forms.Control.MouseDown> <xref:System.Windows.Forms.Control.MouseUp> como aqueles para os eventos e eventos, têm o mesmo tipo de objeto para o segundo parâmetro.</span><span class="sxs-lookup"><span data-stu-id="5775e-111">Some event handlers, such as those for the <xref:System.Windows.Forms.Control.MouseDown> and <xref:System.Windows.Forms.Control.MouseUp> events, have the same object type for their second parameter.</span></span> <span data-ttu-id="5775e-112">Para esses tipos de eventos, você pode usar o mesmo manipulador de eventos para manipular ambos os eventos.</span><span class="sxs-lookup"><span data-stu-id="5775e-112">For these types of events, you can use the same event handler to handle both events.</span></span>  
  
 <span data-ttu-id="5775e-113">Você também pode usar o mesmo manipulador de eventos para manipular o mesmo evento em controles diferentes.</span><span class="sxs-lookup"><span data-stu-id="5775e-113">You can also use the same event handler to handle the same event for different controls.</span></span> <span data-ttu-id="5775e-114">Por exemplo, se você <xref:System.Windows.Forms.RadioButton> tiver um grupo de controles em um formulário, você pode criar um único manipulador de eventos para o evento e ter o <xref:System.Windows.Forms.Control.Click> evento de <xref:System.Windows.Forms.Control.Click> cada controle vinculado ao manipulador de eventos único.</span><span class="sxs-lookup"><span data-stu-id="5775e-114">For example, if you have a group of <xref:System.Windows.Forms.RadioButton> controls on a form, you could create a single event handler for the <xref:System.Windows.Forms.Control.Click> event and have each control's <xref:System.Windows.Forms.Control.Click> event bound to the single event handler.</span></span> <span data-ttu-id="5775e-115">Para obter mais informações, consulte [Como conectar vários eventos a um único manipulador de eventos nos Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="5775e-115">For more information, see [How to: Connect Multiple Events to a Single Event Handler in Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5775e-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="5775e-116">See also</span></span>

- [<span data-ttu-id="5775e-117">Criando manipuladores de eventos no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5775e-117">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="5775e-118">Visão geral de eventos</span><span class="sxs-lookup"><span data-stu-id="5775e-118">Events Overview</span></span>](events-overview-windows-forms.md)
