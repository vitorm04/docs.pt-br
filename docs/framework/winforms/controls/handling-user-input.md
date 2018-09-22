---
title: Identificando a entrada do usuário
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], user input using code
- custom controls [Windows Forms], keyboard events using code
- custom controls [Windows Forms], mouse events using code
ms.assetid: d9b12787-86f6-4022-8e0f-e12d312c4af2
ms.openlocfilehash: 19bb494d6f478c8cb7adda770f441470c4b2d19f
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46699203"
---
# <a name="handling-user-input"></a><span data-ttu-id="49149-102">Identificando a entrada do usuário</span><span class="sxs-lookup"><span data-stu-id="49149-102">Handling User Input</span></span>
<span data-ttu-id="49149-103">Este tópico descreve os principais eventos de teclado e mouse fornecidos pelo <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="49149-103">This topic describes the main keyboard and mouse events provided by <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="49149-104">Ao manipular um evento, os autores do controle devem substituir o método `On`*EventName* protegido em vez de associar um delegado ao evento.</span><span class="sxs-lookup"><span data-stu-id="49149-104">When handling an event, control authors should override the protected `On`*EventName* method rather than attaching a delegate to the event.</span></span> <span data-ttu-id="49149-105">Para ver uma análise de eventos, consulte [Gerando eventos de um componente](https://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).</span><span class="sxs-lookup"><span data-stu-id="49149-105">For a review of events, see [Raising Events from a Component](https://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49149-106">Se não há nenhum dado associado a um evento, uma instância da classe base <xref:System.EventArgs> é passado como um argumento para o `On` *EventName* método.</span><span class="sxs-lookup"><span data-stu-id="49149-106">If there is no data associated with an event, an instance of the base class <xref:System.EventArgs> is passed as an argument to the `On`*EventName* method.</span></span>  
  
## <a name="keyboard-events"></a><span data-ttu-id="49149-107">Eventos de teclado</span><span class="sxs-lookup"><span data-stu-id="49149-107">Keyboard Events</span></span>  
 <span data-ttu-id="49149-108">Os eventos de teclado comuns que seu controle pode manipular são <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, e <xref:System.Windows.Forms.Control.KeyUp>.</span><span class="sxs-lookup"><span data-stu-id="49149-108">The common keyboard events that your control can handle are <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, and <xref:System.Windows.Forms.Control.KeyUp>.</span></span>  
  
|<span data-ttu-id="49149-109">Nome do Evento</span><span class="sxs-lookup"><span data-stu-id="49149-109">Event Name</span></span>|<span data-ttu-id="49149-110">Método a ser substituído</span><span class="sxs-lookup"><span data-stu-id="49149-110">Method to Override</span></span>|<span data-ttu-id="49149-111">Descrição do evento</span><span class="sxs-lookup"><span data-stu-id="49149-111">Description of Event</span></span>|  
|----------------|------------------------|--------------------------|  
|`KeyDown`|`void OnKeyDown(KeyEventArgs)`|<span data-ttu-id="49149-112">Gerado somente quando uma tecla é pressionada pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="49149-112">Raised only when a key is initially pressed.</span></span>|  
|`KeyPress`|`void OnKeyPress`<br /><br /> `(KeyPressEventArgs)`|<span data-ttu-id="49149-113">Gerado sempre que uma tecla é pressionada.</span><span class="sxs-lookup"><span data-stu-id="49149-113">Raised every time a key is pressed.</span></span> <span data-ttu-id="49149-114">Se uma tecla é pressionada, um <xref:System.Windows.Forms.Control.KeyPress> é gerado com a taxa de repetição definida pelo sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="49149-114">If a key is held down, a <xref:System.Windows.Forms.Control.KeyPress> event is raised at the repeat rate defined by the operating system.</span></span>|  
|`KeyUp`|`void OnKeyUp(KeyEventArgs)`|<span data-ttu-id="49149-115">Gerado quando uma tecla é liberada.</span><span class="sxs-lookup"><span data-stu-id="49149-115">Raised when a key is released.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="49149-116">Manipular a entrada do teclado é consideravelmente mais complexo que substituir os eventos na tabela anterior e está além do escopo deste tópico.</span><span class="sxs-lookup"><span data-stu-id="49149-116">Handling keyboard input is considerably more complex than overriding the events in the preceding table and is beyond the scope of this topic.</span></span> <span data-ttu-id="49149-117">Para obter mais informações, consulte [Entrada do usuário no Windows Forms](../../../../docs/framework/winforms/user-input-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="49149-117">For more information, see [User Input in Windows Forms](../../../../docs/framework/winforms/user-input-in-windows-forms.md).</span></span>  
  
## <a name="mouse-events"></a><span data-ttu-id="49149-118">Eventos de mouse</span><span class="sxs-lookup"><span data-stu-id="49149-118">Mouse Events</span></span>  
 <span data-ttu-id="49149-119">Os eventos de mouse que seu controle pode manipular são <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave>, <xref:System.Windows.Forms.Control.MouseMove>, e <xref:System.Windows.Forms.Control.MouseUp>.</span><span class="sxs-lookup"><span data-stu-id="49149-119">The mouse events that your control can handle are <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave>, <xref:System.Windows.Forms.Control.MouseMove>, and <xref:System.Windows.Forms.Control.MouseUp>.</span></span>  
  
|<span data-ttu-id="49149-120">Nome do Evento</span><span class="sxs-lookup"><span data-stu-id="49149-120">Event Name</span></span>|<span data-ttu-id="49149-121">Método a ser substituído</span><span class="sxs-lookup"><span data-stu-id="49149-121">Method to Override</span></span>|<span data-ttu-id="49149-122">Descrição do evento</span><span class="sxs-lookup"><span data-stu-id="49149-122">Description of Event</span></span>|  
|----------------|------------------------|--------------------------|  
|`MouseDown`|`void OnMouseDown(MouseEventArgs)`|<span data-ttu-id="49149-123">Gerado quando o botão do mouse é pressionado enquanto o ponteiro está sobre o controle.</span><span class="sxs-lookup"><span data-stu-id="49149-123">Raised when the mouse button is pressed while the pointer is over the control.</span></span>|  
|`MouseEnter`|`void OnMouseEnter(EventArgs)`|<span data-ttu-id="49149-124">Gerado quando o ponteiro entra pela primeira vez na região do controle.</span><span class="sxs-lookup"><span data-stu-id="49149-124">Raised when the pointer first enters the region of the control.</span></span>|  
|`MouseHover`|`void OnMouseHover(EventArgs)`|<span data-ttu-id="49149-125">Gerado quando o ponteiro do mouse focaliza o controle.</span><span class="sxs-lookup"><span data-stu-id="49149-125">Raised when the pointer hovers over the control.</span></span>|  
|`MouseLeave`|`void OnMouseLeave(EventArgs)`|<span data-ttu-id="49149-126">Gerado quando o ponteiro do mouse deixa a região do controle.</span><span class="sxs-lookup"><span data-stu-id="49149-126">Raised when the pointer leaves the region of the control.</span></span>|  
|`MouseMove`|`void OnMouseMove(MouseEventArgs)`|<span data-ttu-id="49149-127">Gerado quando o ponteiro do mouse se move na região do controle.</span><span class="sxs-lookup"><span data-stu-id="49149-127">Raised when the pointer moves in the region of the control.</span></span>|  
|`MouseUp`|`void OnMouseUp(MouseEventArgs)`|<span data-ttu-id="49149-128">Gerado quando o botão do mouse é liberado enquanto o ponteiro está sobre o controle ou o ponteiro sai da região do controle.</span><span class="sxs-lookup"><span data-stu-id="49149-128">Raised when the mouse button is released while the pointer is over the control or the pointer leaves the region of the control.</span></span>|  
  
 <span data-ttu-id="49149-129">O fragmento de código a seguir mostra um exemplo de substituição a <xref:System.Windows.Forms.Control.MouseDown> eventos.</span><span class="sxs-lookup"><span data-stu-id="49149-129">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseDown> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#7)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#7)]  
  
 <span data-ttu-id="49149-130">O fragmento de código a seguir mostra um exemplo de substituição a <xref:System.Windows.Forms.Control.MouseMove> eventos.</span><span class="sxs-lookup"><span data-stu-id="49149-130">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseMove> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#8)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#8)]  
  
 <span data-ttu-id="49149-131">O fragmento de código a seguir mostra um exemplo de substituição a <xref:System.Windows.Forms.Control.MouseUp> eventos.</span><span class="sxs-lookup"><span data-stu-id="49149-131">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseUp> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#9)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#9)]  
  
 <span data-ttu-id="49149-132">Para ver o código-fonte completo para o exemplo `FlashTrackBar`, consulte [Como criar um controle do Windows Forms que mostra o progresso](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span><span class="sxs-lookup"><span data-stu-id="49149-132">For the complete source code for the `FlashTrackBar` sample, see [How to: Create a Windows Forms Control That Shows Progress](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49149-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="49149-133">See Also</span></span>  
 [<span data-ttu-id="49149-134">Eventos em controles do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="49149-134">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 [<span data-ttu-id="49149-135">Definindo um evento</span><span class="sxs-lookup"><span data-stu-id="49149-135">Defining an Event</span></span>](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)  
 [<span data-ttu-id="49149-136">Eventos</span><span class="sxs-lookup"><span data-stu-id="49149-136">Events</span></span>](../../../../docs/standard/events/index.md)  
 [<span data-ttu-id="49149-137">Entrada do usuário nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="49149-137">User Input in Windows Forms</span></span>](../../../../docs/framework/winforms/user-input-in-windows-forms.md)
