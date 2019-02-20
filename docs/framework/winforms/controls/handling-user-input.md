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
ms.openlocfilehash: 8c6319929d4b419cc0a2e1cfd097bfae7d997120
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2019
ms.locfileid: "56442992"
---
# <a name="handling-user-input"></a><span data-ttu-id="1a04c-102">Identificando a entrada do usuário</span><span class="sxs-lookup"><span data-stu-id="1a04c-102">Handling User Input</span></span>
<span data-ttu-id="1a04c-103">Este tópico descreve os principais eventos de teclado e mouse fornecidos pelo <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1a04c-103">This topic describes the main keyboard and mouse events provided by <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1a04c-104">Ao manipular um evento, os autores do controle devem substituir o método `On`*EventName* protegido em vez de associar um delegado ao evento.</span><span class="sxs-lookup"><span data-stu-id="1a04c-104">When handling an event, control authors should override the protected `On`*EventName* method rather than attaching a delegate to the event.</span></span> <span data-ttu-id="1a04c-105">Para ver uma análise de eventos, consulte [Gerando eventos de um componente](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="1a04c-105">For a review of events, see [Raising Events from a Component](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1a04c-106">Se não há nenhum dado associado a um evento, uma instância da classe base <xref:System.EventArgs> é passado como um argumento para o `On` *EventName* método.</span><span class="sxs-lookup"><span data-stu-id="1a04c-106">If there is no data associated with an event, an instance of the base class <xref:System.EventArgs> is passed as an argument to the `On`*EventName* method.</span></span>  
  
## <a name="keyboard-events"></a><span data-ttu-id="1a04c-107">Eventos de teclado</span><span class="sxs-lookup"><span data-stu-id="1a04c-107">Keyboard Events</span></span>  
 <span data-ttu-id="1a04c-108">Os eventos de teclado comuns que seu controle pode manipular são <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, e <xref:System.Windows.Forms.Control.KeyUp>.</span><span class="sxs-lookup"><span data-stu-id="1a04c-108">The common keyboard events that your control can handle are <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, and <xref:System.Windows.Forms.Control.KeyUp>.</span></span>  
  
|<span data-ttu-id="1a04c-109">Nome do Evento</span><span class="sxs-lookup"><span data-stu-id="1a04c-109">Event Name</span></span>|<span data-ttu-id="1a04c-110">Método a ser substituído</span><span class="sxs-lookup"><span data-stu-id="1a04c-110">Method to Override</span></span>|<span data-ttu-id="1a04c-111">Descrição do evento</span><span class="sxs-lookup"><span data-stu-id="1a04c-111">Description of Event</span></span>|  
|----------------|------------------------|--------------------------|  
|`KeyDown`|`void OnKeyDown(KeyEventArgs)`|<span data-ttu-id="1a04c-112">Gerado somente quando uma tecla é pressionada pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="1a04c-112">Raised only when a key is initially pressed.</span></span>|  
|`KeyPress`|`void OnKeyPress`<br /><br /> `(KeyPressEventArgs)`|<span data-ttu-id="1a04c-113">Gerado sempre que uma tecla é pressionada.</span><span class="sxs-lookup"><span data-stu-id="1a04c-113">Raised every time a key is pressed.</span></span> <span data-ttu-id="1a04c-114">Se uma tecla é pressionada, um <xref:System.Windows.Forms.Control.KeyPress> é gerado com a taxa de repetição definida pelo sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="1a04c-114">If a key is held down, a <xref:System.Windows.Forms.Control.KeyPress> event is raised at the repeat rate defined by the operating system.</span></span>|  
|`KeyUp`|`void OnKeyUp(KeyEventArgs)`|<span data-ttu-id="1a04c-115">Gerado quando uma tecla é liberada.</span><span class="sxs-lookup"><span data-stu-id="1a04c-115">Raised when a key is released.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="1a04c-116">Manipular a entrada do teclado é consideravelmente mais complexo que substituir os eventos na tabela anterior e está além do escopo deste tópico.</span><span class="sxs-lookup"><span data-stu-id="1a04c-116">Handling keyboard input is considerably more complex than overriding the events in the preceding table and is beyond the scope of this topic.</span></span> <span data-ttu-id="1a04c-117">Para obter mais informações, consulte [Entrada do usuário no Windows Forms](../../../../docs/framework/winforms/user-input-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="1a04c-117">For more information, see [User Input in Windows Forms](../../../../docs/framework/winforms/user-input-in-windows-forms.md).</span></span>  
  
## <a name="mouse-events"></a><span data-ttu-id="1a04c-118">Eventos de mouse</span><span class="sxs-lookup"><span data-stu-id="1a04c-118">Mouse Events</span></span>  
 <span data-ttu-id="1a04c-119">Os eventos de mouse que seu controle pode manipular são <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave>, <xref:System.Windows.Forms.Control.MouseMove>, e <xref:System.Windows.Forms.Control.MouseUp>.</span><span class="sxs-lookup"><span data-stu-id="1a04c-119">The mouse events that your control can handle are <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave>, <xref:System.Windows.Forms.Control.MouseMove>, and <xref:System.Windows.Forms.Control.MouseUp>.</span></span>  
  
|<span data-ttu-id="1a04c-120">Nome do Evento</span><span class="sxs-lookup"><span data-stu-id="1a04c-120">Event Name</span></span>|<span data-ttu-id="1a04c-121">Método a ser substituído</span><span class="sxs-lookup"><span data-stu-id="1a04c-121">Method to Override</span></span>|<span data-ttu-id="1a04c-122">Descrição do evento</span><span class="sxs-lookup"><span data-stu-id="1a04c-122">Description of Event</span></span>|  
|----------------|------------------------|--------------------------|  
|`MouseDown`|`void OnMouseDown(MouseEventArgs)`|<span data-ttu-id="1a04c-123">Gerado quando o botão do mouse é pressionado enquanto o ponteiro está sobre o controle.</span><span class="sxs-lookup"><span data-stu-id="1a04c-123">Raised when the mouse button is pressed while the pointer is over the control.</span></span>|  
|`MouseEnter`|`void OnMouseEnter(EventArgs)`|<span data-ttu-id="1a04c-124">Gerado quando o ponteiro entra pela primeira vez na região do controle.</span><span class="sxs-lookup"><span data-stu-id="1a04c-124">Raised when the pointer first enters the region of the control.</span></span>|  
|`MouseHover`|`void OnMouseHover(EventArgs)`|<span data-ttu-id="1a04c-125">Gerado quando o ponteiro do mouse focaliza o controle.</span><span class="sxs-lookup"><span data-stu-id="1a04c-125">Raised when the pointer hovers over the control.</span></span>|  
|`MouseLeave`|`void OnMouseLeave(EventArgs)`|<span data-ttu-id="1a04c-126">Gerado quando o ponteiro do mouse deixa a região do controle.</span><span class="sxs-lookup"><span data-stu-id="1a04c-126">Raised when the pointer leaves the region of the control.</span></span>|  
|`MouseMove`|`void OnMouseMove(MouseEventArgs)`|<span data-ttu-id="1a04c-127">Gerado quando o ponteiro do mouse se move na região do controle.</span><span class="sxs-lookup"><span data-stu-id="1a04c-127">Raised when the pointer moves in the region of the control.</span></span>|  
|`MouseUp`|`void OnMouseUp(MouseEventArgs)`|<span data-ttu-id="1a04c-128">Gerado quando o botão do mouse é liberado enquanto o ponteiro está sobre o controle ou o ponteiro sai da região do controle.</span><span class="sxs-lookup"><span data-stu-id="1a04c-128">Raised when the mouse button is released while the pointer is over the control or the pointer leaves the region of the control.</span></span>|  
  
 <span data-ttu-id="1a04c-129">O fragmento de código a seguir mostra um exemplo de substituição a <xref:System.Windows.Forms.Control.MouseDown> eventos.</span><span class="sxs-lookup"><span data-stu-id="1a04c-129">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseDown> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#7)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#7)]  
  
 <span data-ttu-id="1a04c-130">O fragmento de código a seguir mostra um exemplo de substituição a <xref:System.Windows.Forms.Control.MouseMove> eventos.</span><span class="sxs-lookup"><span data-stu-id="1a04c-130">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseMove> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#8)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#8)]  
  
 <span data-ttu-id="1a04c-131">O fragmento de código a seguir mostra um exemplo de substituição a <xref:System.Windows.Forms.Control.MouseUp> eventos.</span><span class="sxs-lookup"><span data-stu-id="1a04c-131">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseUp> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#9)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#9)]  
  
 <span data-ttu-id="1a04c-132">Para o código-fonte completo para o `FlashTrackBar` de exemplo, consulte [como: Criar um controle de formulários do Windows que mostre o progresso](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span><span class="sxs-lookup"><span data-stu-id="1a04c-132">For the complete source code for the `FlashTrackBar` sample, see [How to: Create a Windows Forms Control That Shows Progress](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a04c-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1a04c-133">See also</span></span>
- [<span data-ttu-id="1a04c-134">Eventos em controles do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1a04c-134">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)
- [<span data-ttu-id="1a04c-135">Definindo um evento</span><span class="sxs-lookup"><span data-stu-id="1a04c-135">Defining an Event</span></span>](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)
- [<span data-ttu-id="1a04c-136">Eventos</span><span class="sxs-lookup"><span data-stu-id="1a04c-136">Events</span></span>](../../../../docs/standard/events/index.md)
- [<span data-ttu-id="1a04c-137">Entrada do usuário nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1a04c-137">User Input in Windows Forms</span></span>](../../../../docs/framework/winforms/user-input-in-windows-forms.md)
