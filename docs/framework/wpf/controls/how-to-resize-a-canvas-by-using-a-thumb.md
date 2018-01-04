---
title: Como redimensionar uma tela usando um elevador
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resizing Canvas control [WPF]
- controls [WPF], Thumb
- controls [WPF], Canvas
- Thumb control [WPF]
- Canvas control [WPF]
ms.assetid: 7dc9f435-726c-4d4d-be41-eb24cfe17bef
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c73509d58112e47f707e82243005bfdf9edca151
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-resize-a-canvas-by-using-a-thumb"></a><span data-ttu-id="141e7-102">Como redimensionar uma tela usando um elevador</span><span class="sxs-lookup"><span data-stu-id="141e7-102">How to: Resize a Canvas by Using a Thumb</span></span>
<span data-ttu-id="141e7-103">Este exemplo mostra como usar um <xref:System.Windows.Controls.Primitives.Thumb> controle para redimensionar um <xref:System.Windows.Controls.Canvas> controle.</span><span class="sxs-lookup"><span data-stu-id="141e7-103">This example shows how to use a <xref:System.Windows.Controls.Primitives.Thumb> control to resize a <xref:System.Windows.Controls.Canvas> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="141e7-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="141e7-104">Example</span></span>  
 <span data-ttu-id="141e7-105">O <xref:System.Windows.Controls.Primitives.Thumb> controle oferece funcionalidade de arrastar que pode ser usada para mover ou redimensionar controles monitorando o <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>, <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> e <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> eventos de <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="141e7-105">The <xref:System.Windows.Controls.Primitives.Thumb> control provides drag functionality that can be used to move or resize controls by monitoring the <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>, <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> and <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> events of the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
 <span data-ttu-id="141e7-106">O usuário começa uma operação de arrastar, pressionando o botão esquerdo do mouse quando o ponteiro do mouse está pausado no <xref:System.Windows.Controls.Primitives.Thumb> controle.</span><span class="sxs-lookup"><span data-stu-id="141e7-106">The user begins a drag operation by pressing the left mouse button when the mouse pointer is paused on the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span> <span data-ttu-id="141e7-107">A operação de arrastar continuará enquanto o botão esquerdo do mouse permanecer pressionado.</span><span class="sxs-lookup"><span data-stu-id="141e7-107">The drag operation continues as long as the left mouse button remains pressed.</span></span> <span data-ttu-id="141e7-108">Durante a operação de arrastar, o <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> pode ocorrer mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="141e7-108">During the drag operation, the <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> can occur more than once.</span></span> <span data-ttu-id="141e7-109">Cada vez que ocorrer, o <xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> classe fornece a mudança de posição que corresponde a mudança na posição do mouse.</span><span class="sxs-lookup"><span data-stu-id="141e7-109">Each time it occurs, the <xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> class provides the change in position that corresponds to the change in mouse position.</span></span> <span data-ttu-id="141e7-110">Quando o usuário libera o botão esquerdo do mouse, a operação de arrastar é concluída.</span><span class="sxs-lookup"><span data-stu-id="141e7-110">When the user releases the left mouse button, the drag operation is finished.</span></span> <span data-ttu-id="141e7-111">A operação de arrastar somente fornece novas coordenadas; ele não reposiciona automaticamente o <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="141e7-111">The drag operation only provides new coordinates; it does not automatically reposition the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
 <span data-ttu-id="141e7-112">A exemplo a seguir mostra um <xref:System.Windows.Controls.Primitives.Thumb> controlar o que é o elemento filho de um <xref:System.Windows.Controls.Canvas> controle.</span><span class="sxs-lookup"><span data-stu-id="141e7-112">The following example shows a <xref:System.Windows.Controls.Primitives.Thumb> control that is the child element of a <xref:System.Windows.Controls.Canvas> control.</span></span> <span data-ttu-id="141e7-113">O manipulador de eventos para sua <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> evento fornece a lógica para mover o <xref:System.Windows.Controls.Primitives.Thumb> e redimensione o <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="141e7-113">The event handler for its <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> event provides the logic to move the <xref:System.Windows.Controls.Primitives.Thumb> and resize the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="141e7-114">Manipuladores de eventos para o <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> e <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> evento alterar a cor do <xref:System.Windows.Controls.Primitives.Thumb> durante uma operação de arrastar.</span><span class="sxs-lookup"><span data-stu-id="141e7-114">The event handlers for the <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> and <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> event change the color of the <xref:System.Windows.Controls.Primitives.Thumb> during a drag operation.</span></span> <span data-ttu-id="141e7-115">O exemplo a seguir define o <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="141e7-115">The following example defines the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
 [!code-xaml[Thumb#thumb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml#thumb)]  
  
 <span data-ttu-id="141e7-116">A exemplo a seguir mostra o <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> manipulador de eventos que move o <xref:System.Windows.Controls.Primitives.Thumb> e redimensiona a <xref:System.Windows.Controls.Canvas> em resposta a um movimento do mouse.</span><span class="sxs-lookup"><span data-stu-id="141e7-116">The following example shows the <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> event handler that moves the <xref:System.Windows.Controls.Primitives.Thumb> and resizes the <xref:System.Windows.Controls.Canvas> in response to a mouse movement.</span></span>  
  
 [!code-csharp[Thumb#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#2)]  
  
 <span data-ttu-id="141e7-117">A exemplo a seguir mostra o <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="141e7-117">The following example shows the <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> event handler.</span></span>  
  
 [!code-csharp[Thumb#DragStartedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragstartedhandler)]
 [!code-vb[Thumb#DragStartedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragstartedhandler)]  
  
 <span data-ttu-id="141e7-118">A exemplo a seguir mostra o <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="141e7-118">The following example shows the <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> event handler.</span></span>  
  
 [!code-csharp[Thumb#DragCompletedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragcompletedhandler)]
 [!code-vb[Thumb#DragCompletedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragcompletedhandler)]  
  
 <span data-ttu-id="141e7-119">Para o exemplo completo, consulte [Exemplo de funcionalidade de arrastar do elevador](http://go.microsoft.com/fwlink/?LinkID=160042).</span><span class="sxs-lookup"><span data-stu-id="141e7-119">For the complete sample, see [Thumb Drag Functionality Sample](http://go.microsoft.com/fwlink/?LinkID=160042).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="141e7-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="141e7-120">See Also</span></span>  
 <xref:System.Windows.Controls.Primitives.Thumb>  
 <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>  
 <xref:System.Windows.Controls.Primitives.Thumb.DragDelta>  
 <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>
