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
ms.openlocfilehash: f92b742c3f6feec72e5b3150204d7d984636281d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934088"
---
# <a name="handling-user-input"></a><span data-ttu-id="71f6b-102">Identificando a entrada do usuário</span><span class="sxs-lookup"><span data-stu-id="71f6b-102">Handling User Input</span></span>
<span data-ttu-id="71f6b-103">Este tópico descreve os principais eventos de teclado e mouse fornecidos <xref:System.Windows.Forms.Control?displayProperty=nameWithType>pelo.</span><span class="sxs-lookup"><span data-stu-id="71f6b-103">This topic describes the main keyboard and mouse events provided by <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="71f6b-104">Ao manipular um evento, os autores do controle devem substituir o método `On`*EventName* protegido em vez de associar um delegado ao evento.</span><span class="sxs-lookup"><span data-stu-id="71f6b-104">When handling an event, control authors should override the protected `On`*EventName* method rather than attaching a delegate to the event.</span></span> <span data-ttu-id="71f6b-105">Para ver uma análise de eventos, consulte [Gerando eventos de um componente](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="71f6b-105">For a review of events, see [Raising Events from a Component](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="71f6b-106">Se não houver dados associados a um evento, uma instância da classe <xref:System.EventArgs> base será passada como um argumento para o `On`método *EventName* .</span><span class="sxs-lookup"><span data-stu-id="71f6b-106">If there is no data associated with an event, an instance of the base class <xref:System.EventArgs> is passed as an argument to the `On`*EventName* method.</span></span>  
  
## <a name="keyboard-events"></a><span data-ttu-id="71f6b-107">Eventos de teclado</span><span class="sxs-lookup"><span data-stu-id="71f6b-107">Keyboard Events</span></span>  
 <span data-ttu-id="71f6b-108">Os eventos comuns de teclado que seu controle pode manipular <xref:System.Windows.Forms.Control.KeyDown>são <xref:System.Windows.Forms.Control.KeyPress>, e <xref:System.Windows.Forms.Control.KeyUp>.</span><span class="sxs-lookup"><span data-stu-id="71f6b-108">The common keyboard events that your control can handle are <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, and <xref:System.Windows.Forms.Control.KeyUp>.</span></span>  
  
|<span data-ttu-id="71f6b-109">Nome do Evento</span><span class="sxs-lookup"><span data-stu-id="71f6b-109">Event Name</span></span>|<span data-ttu-id="71f6b-110">Método a ser substituído</span><span class="sxs-lookup"><span data-stu-id="71f6b-110">Method to Override</span></span>|<span data-ttu-id="71f6b-111">Descrição do evento</span><span class="sxs-lookup"><span data-stu-id="71f6b-111">Description of Event</span></span>|  
|----------------|------------------------|--------------------------|  
|`KeyDown`|`void OnKeyDown(KeyEventArgs)`|<span data-ttu-id="71f6b-112">Gerado somente quando uma tecla é pressionada pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="71f6b-112">Raised only when a key is initially pressed.</span></span>|  
|`KeyPress`|`void OnKeyPress`<br /><br /> `(KeyPressEventArgs)`|<span data-ttu-id="71f6b-113">Gerado sempre que uma tecla é pressionada.</span><span class="sxs-lookup"><span data-stu-id="71f6b-113">Raised every time a key is pressed.</span></span> <span data-ttu-id="71f6b-114">Se uma chave for mantida inativa, <xref:System.Windows.Forms.Control.KeyPress> um evento será gerado na taxa de repetição definida pelo sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="71f6b-114">If a key is held down, a <xref:System.Windows.Forms.Control.KeyPress> event is raised at the repeat rate defined by the operating system.</span></span>|  
|`KeyUp`|`void OnKeyUp(KeyEventArgs)`|<span data-ttu-id="71f6b-115">Gerado quando uma tecla é liberada.</span><span class="sxs-lookup"><span data-stu-id="71f6b-115">Raised when a key is released.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="71f6b-116">Manipular a entrada do teclado é consideravelmente mais complexo que substituir os eventos na tabela anterior e está além do escopo deste tópico.</span><span class="sxs-lookup"><span data-stu-id="71f6b-116">Handling keyboard input is considerably more complex than overriding the events in the preceding table and is beyond the scope of this topic.</span></span> <span data-ttu-id="71f6b-117">Para obter mais informações, consulte [Entrada do usuário no Windows Forms](../user-input-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="71f6b-117">For more information, see [User Input in Windows Forms](../user-input-in-windows-forms.md).</span></span>  
  
## <a name="mouse-events"></a><span data-ttu-id="71f6b-118">Eventos de mouse</span><span class="sxs-lookup"><span data-stu-id="71f6b-118">Mouse Events</span></span>  
 <span data-ttu-id="71f6b-119">Os eventos do mouse que o controle pode manipular <xref:System.Windows.Forms.Control.MouseDown>são <xref:System.Windows.Forms.Control.MouseEnter> <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave> <xref:System.Windows.Forms.Control.MouseMove>,,, e <xref:System.Windows.Forms.Control.MouseUp>.</span><span class="sxs-lookup"><span data-stu-id="71f6b-119">The mouse events that your control can handle are <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave>, <xref:System.Windows.Forms.Control.MouseMove>, and <xref:System.Windows.Forms.Control.MouseUp>.</span></span>  
  
|<span data-ttu-id="71f6b-120">Nome do Evento</span><span class="sxs-lookup"><span data-stu-id="71f6b-120">Event Name</span></span>|<span data-ttu-id="71f6b-121">Método a ser substituído</span><span class="sxs-lookup"><span data-stu-id="71f6b-121">Method to Override</span></span>|<span data-ttu-id="71f6b-122">Descrição do evento</span><span class="sxs-lookup"><span data-stu-id="71f6b-122">Description of Event</span></span>|  
|----------------|------------------------|--------------------------|  
|`MouseDown`|`void OnMouseDown(MouseEventArgs)`|<span data-ttu-id="71f6b-123">Gerado quando o botão do mouse é pressionado enquanto o ponteiro está sobre o controle.</span><span class="sxs-lookup"><span data-stu-id="71f6b-123">Raised when the mouse button is pressed while the pointer is over the control.</span></span>|  
|`MouseEnter`|`void OnMouseEnter(EventArgs)`|<span data-ttu-id="71f6b-124">Gerado quando o ponteiro entra pela primeira vez na região do controle.</span><span class="sxs-lookup"><span data-stu-id="71f6b-124">Raised when the pointer first enters the region of the control.</span></span>|  
|`MouseHover`|`void OnMouseHover(EventArgs)`|<span data-ttu-id="71f6b-125">Gerado quando o ponteiro do mouse focaliza o controle.</span><span class="sxs-lookup"><span data-stu-id="71f6b-125">Raised when the pointer hovers over the control.</span></span>|  
|`MouseLeave`|`void OnMouseLeave(EventArgs)`|<span data-ttu-id="71f6b-126">Gerado quando o ponteiro do mouse deixa a região do controle.</span><span class="sxs-lookup"><span data-stu-id="71f6b-126">Raised when the pointer leaves the region of the control.</span></span>|  
|`MouseMove`|`void OnMouseMove(MouseEventArgs)`|<span data-ttu-id="71f6b-127">Gerado quando o ponteiro do mouse se move na região do controle.</span><span class="sxs-lookup"><span data-stu-id="71f6b-127">Raised when the pointer moves in the region of the control.</span></span>|  
|`MouseUp`|`void OnMouseUp(MouseEventArgs)`|<span data-ttu-id="71f6b-128">Gerado quando o botão do mouse é liberado enquanto o ponteiro está sobre o controle ou o ponteiro sai da região do controle.</span><span class="sxs-lookup"><span data-stu-id="71f6b-128">Raised when the mouse button is released while the pointer is over the control or the pointer leaves the region of the control.</span></span>|  
  
 <span data-ttu-id="71f6b-129">O fragmento de código a seguir mostra um exemplo de <xref:System.Windows.Forms.Control.MouseDown> substituição do evento.</span><span class="sxs-lookup"><span data-stu-id="71f6b-129">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseDown> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#7)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#7)]  
  
 <span data-ttu-id="71f6b-130">O fragmento de código a seguir mostra um exemplo de <xref:System.Windows.Forms.Control.MouseMove> substituição do evento.</span><span class="sxs-lookup"><span data-stu-id="71f6b-130">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseMove> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#8)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#8)]  
  
 <span data-ttu-id="71f6b-131">O fragmento de código a seguir mostra um exemplo de <xref:System.Windows.Forms.Control.MouseUp> substituição do evento.</span><span class="sxs-lookup"><span data-stu-id="71f6b-131">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseUp> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#9)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#9)]  
  
 <span data-ttu-id="71f6b-132">Para obter o código-fonte completo `FlashTrackBar` do exemplo, [consulte Como: Crie um controle de Windows Forms que mostre](how-to-create-a-windows-forms-control-that-shows-progress.md)o progresso.</span><span class="sxs-lookup"><span data-stu-id="71f6b-132">For the complete source code for the `FlashTrackBar` sample, see [How to: Create a Windows Forms Control That Shows Progress](how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71f6b-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71f6b-133">See also</span></span>

- [<span data-ttu-id="71f6b-134">Eventos em controles do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="71f6b-134">Events in Windows Forms Controls</span></span>](events-in-windows-forms-controls.md)
- [<span data-ttu-id="71f6b-135">Definindo um evento</span><span class="sxs-lookup"><span data-stu-id="71f6b-135">Defining an Event</span></span>](defining-an-event-in-windows-forms-controls.md)
- [<span data-ttu-id="71f6b-136">Eventos</span><span class="sxs-lookup"><span data-stu-id="71f6b-136">Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="71f6b-137">Entrada do usuário nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="71f6b-137">User Input in Windows Forms</span></span>](../user-input-in-windows-forms.md)
