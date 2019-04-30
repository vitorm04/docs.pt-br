---
title: Visão geral de manipuladores de eventos (Windows Forms)
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
ms.openlocfilehash: 05acbfaf427060d015c2445360a7d73ebe97d070
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61966823"
---
# <a name="event-handlers-overview-windows-forms"></a><span data-ttu-id="e698a-102">Visão geral de manipuladores de eventos (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="e698a-102">Event Handlers Overview (Windows Forms)</span></span>
<span data-ttu-id="e698a-103">Um manipulador de eventos é um método que está associado a um evento.</span><span class="sxs-lookup"><span data-stu-id="e698a-103">An event handler is a method that is bound to an event.</span></span> <span data-ttu-id="e698a-104">Quando o evento é gerado, o código no manipulador de eventos é executado.</span><span class="sxs-lookup"><span data-stu-id="e698a-104">When the event is raised, the code within the event handler is executed.</span></span> <span data-ttu-id="e698a-105">Cada manipulador de eventos fornece dois parâmetros que permitem manipular o evento corretamente.</span><span class="sxs-lookup"><span data-stu-id="e698a-105">Each event handler provides two parameters that allow you to handle the event properly.</span></span> <span data-ttu-id="e698a-106">O exemplo a seguir mostra um manipulador de eventos para um <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Click> eventos.</span><span class="sxs-lookup"><span data-stu-id="e698a-106">The following example shows an event handler for a <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event.</span></span>  
  
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
  
 <span data-ttu-id="e698a-107">No primeiro parâmetro, `sender`, fornece uma referência ao objeto que gerou o evento.</span><span class="sxs-lookup"><span data-stu-id="e698a-107">The first parameter,`sender`, provides a reference to the object that raised the event.</span></span> <span data-ttu-id="e698a-108">No exemplo acima, o segundo parâmetro, `e`, passa um objeto específico para o evento que está sendo manipulado.</span><span class="sxs-lookup"><span data-stu-id="e698a-108">The second parameter, `e`, in the example above, passes an object specific to the event that is being handled.</span></span> <span data-ttu-id="e698a-109">Consultando as propriedades do objeto (e, às vezes, seus métodos), é possível obter informações como o local do mouse para eventos de mouse ou dados que estão sendo transferidos em eventos do tipo "arrastar e soltar".</span><span class="sxs-lookup"><span data-stu-id="e698a-109">By referencing the object's properties (and, sometimes, its methods), you can obtain information such as the location of the mouse for mouse events or data being transferred in drag-and-drop events.</span></span>  
  
 <span data-ttu-id="e698a-110">Normalmente, cada evento produz um manipulador de eventos com um tipo de objeto de evento diferente para o segundo parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e698a-110">Typically each event produces an event handler with a different event-object type for the second parameter.</span></span> <span data-ttu-id="e698a-111">Alguns manipuladores de eventos, como aquelas para o <xref:System.Windows.Forms.Control.MouseDown> e <xref:System.Windows.Forms.Control.MouseUp> eventos, têm o mesmo tipo de objeto para o segundo parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e698a-111">Some event handlers, such as those for the <xref:System.Windows.Forms.Control.MouseDown> and <xref:System.Windows.Forms.Control.MouseUp> events, have the same object type for their second parameter.</span></span> <span data-ttu-id="e698a-112">Para esses tipos de eventos, você pode usar o mesmo manipulador de eventos para manipular ambos os eventos.</span><span class="sxs-lookup"><span data-stu-id="e698a-112">For these types of events, you can use the same event handler to handle both events.</span></span>  
  
 <span data-ttu-id="e698a-113">Você também pode usar o mesmo manipulador de eventos para manipular o mesmo evento em controles diferentes.</span><span class="sxs-lookup"><span data-stu-id="e698a-113">You can also use the same event handler to handle the same event for different controls.</span></span> <span data-ttu-id="e698a-114">Por exemplo, se você tiver um grupo de <xref:System.Windows.Forms.RadioButton> controles em um formulário, você pode criar um único manipulador de eventos para o <xref:System.Windows.Forms.Control.Click> eventos e ter cada controle <xref:System.Windows.Forms.Control.Click> evento associado ao manipulador de eventos único.</span><span class="sxs-lookup"><span data-stu-id="e698a-114">For example, if you have a group of <xref:System.Windows.Forms.RadioButton> controls on a form, you could create a single event handler for the <xref:System.Windows.Forms.Control.Click> event and have each control's <xref:System.Windows.Forms.Control.Click> event bound to the single event handler.</span></span> <span data-ttu-id="e698a-115">Para obter mais informações, confira [Como: Conectar vários eventos a um único manipulador de eventos nos Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="e698a-115">For more information, see [How to: Connect Multiple Events to a Single Event Handler in Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e698a-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e698a-116">See also</span></span>

- [<span data-ttu-id="e698a-117">Criando manipuladores de eventos no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e698a-117">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="e698a-118">Visão geral de eventos</span><span class="sxs-lookup"><span data-stu-id="e698a-118">Events Overview</span></span>](events-overview-windows-forms.md)
