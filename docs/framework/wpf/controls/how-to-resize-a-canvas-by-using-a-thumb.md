---
title: Como redimensionar uma tela usando um elevador
ms.date: 03/30/2017
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
ms.openlocfilehash: 84f5ac2b53124b7f4d7c15741e94b40e7ee81526
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124293"
---
# <a name="how-to-resize-a-canvas-by-using-a-thumb"></a><span data-ttu-id="499e0-102">Como redimensionar uma tela usando um elevador</span><span class="sxs-lookup"><span data-stu-id="499e0-102">How to: Resize a Canvas by Using a Thumb</span></span>
<span data-ttu-id="499e0-103">Este exemplo mostra como usar um controle de <xref:System.Windows.Controls.Primitives.Thumb> para redimensionar um controle de <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="499e0-103">This example shows how to use a <xref:System.Windows.Controls.Primitives.Thumb> control to resize a <xref:System.Windows.Controls.Canvas> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="499e0-104">{1&gt;Exemplo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="499e0-104">Example</span></span>  
 <span data-ttu-id="499e0-105">O controle de <xref:System.Windows.Controls.Primitives.Thumb> fornece funcionalidade de arrastar que pode ser usada para mover ou redimensionar controles monitorando os eventos <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>, <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> e <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> do <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="499e0-105">The <xref:System.Windows.Controls.Primitives.Thumb> control provides drag functionality that can be used to move or resize controls by monitoring the <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>, <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> and <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> events of the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
 <span data-ttu-id="499e0-106">O usuário inicia uma operação de arrastar pressionando o botão esquerdo do mouse quando o ponteiro do mouse é pausado no controle de <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="499e0-106">The user begins a drag operation by pressing the left mouse button when the mouse pointer is paused on the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span> <span data-ttu-id="499e0-107">A operação de arrastar continuará enquanto o botão esquerdo do mouse permanecer pressionado.</span><span class="sxs-lookup"><span data-stu-id="499e0-107">The drag operation continues as long as the left mouse button remains pressed.</span></span> <span data-ttu-id="499e0-108">Durante a operação de arrastar, o <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> pode ocorrer mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="499e0-108">During the drag operation, the <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> can occur more than once.</span></span> <span data-ttu-id="499e0-109">Cada vez que ele ocorre, a classe <xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> fornece a alteração na posição que corresponde à alteração na posição do mouse.</span><span class="sxs-lookup"><span data-stu-id="499e0-109">Each time it occurs, the <xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> class provides the change in position that corresponds to the change in mouse position.</span></span> <span data-ttu-id="499e0-110">Quando o usuário libera o botão esquerdo do mouse, a operação de arrastar é concluída.</span><span class="sxs-lookup"><span data-stu-id="499e0-110">When the user releases the left mouse button, the drag operation is finished.</span></span> <span data-ttu-id="499e0-111">A operação de arrastar fornece apenas novas coordenadas; Ele não reposiciona automaticamente o <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="499e0-111">The drag operation only provides new coordinates; it does not automatically reposition the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
 <span data-ttu-id="499e0-112">O exemplo a seguir mostra um controle <xref:System.Windows.Controls.Primitives.Thumb> que é o elemento filho de um controle <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="499e0-112">The following example shows a <xref:System.Windows.Controls.Primitives.Thumb> control that is the child element of a <xref:System.Windows.Controls.Canvas> control.</span></span> <span data-ttu-id="499e0-113">O manipulador de eventos para seu evento de <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> fornece a lógica para mover o <xref:System.Windows.Controls.Primitives.Thumb> e redimensionar o <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="499e0-113">The event handler for its <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> event provides the logic to move the <xref:System.Windows.Controls.Primitives.Thumb> and resize the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="499e0-114">Os manipuladores de eventos para o evento <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> e <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> alteram a cor do <xref:System.Windows.Controls.Primitives.Thumb> durante uma operação de arrastar.</span><span class="sxs-lookup"><span data-stu-id="499e0-114">The event handlers for the <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> and <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> event change the color of the <xref:System.Windows.Controls.Primitives.Thumb> during a drag operation.</span></span> <span data-ttu-id="499e0-115">O exemplo a seguir define o <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="499e0-115">The following example defines the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
 [!code-xaml[Thumb#thumb](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml#thumb)]  
  
 <span data-ttu-id="499e0-116">O exemplo a seguir mostra o manipulador de eventos <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> que move o <xref:System.Windows.Controls.Primitives.Thumb> e redimensiona o <xref:System.Windows.Controls.Canvas> em resposta a um movimento do mouse.</span><span class="sxs-lookup"><span data-stu-id="499e0-116">The following example shows the <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> event handler that moves the <xref:System.Windows.Controls.Primitives.Thumb> and resizes the <xref:System.Windows.Controls.Canvas> in response to a mouse movement.</span></span>  
  
 [!code-csharp[Thumb#2](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#2)]  
  
 <span data-ttu-id="499e0-117">O exemplo a seguir mostra o manipulador de eventos <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>.</span><span class="sxs-lookup"><span data-stu-id="499e0-117">The following example shows the <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> event handler.</span></span>  
  
 [!code-csharp[Thumb#DragStartedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragstartedhandler)]
 [!code-vb[Thumb#DragStartedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragstartedhandler)]  
  
 <span data-ttu-id="499e0-118">O exemplo a seguir mostra o manipulador de eventos <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>.</span><span class="sxs-lookup"><span data-stu-id="499e0-118">The following example shows the <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> event handler.</span></span>  
  
 [!code-csharp[Thumb#DragCompletedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragcompletedhandler)]
 [!code-vb[Thumb#DragCompletedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragcompletedhandler)]  
  
 <span data-ttu-id="499e0-119">Para o exemplo completo, consulte [Exemplo de funcionalidade de arrastar do elevador](https://github.com/Microsoft/WPF-Samples/tree/master/Drag%20and%20Drop/DragDropThumbOps).</span><span class="sxs-lookup"><span data-stu-id="499e0-119">For the complete sample, see [Thumb Drag Functionality Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Drag%20and%20Drop/DragDropThumbOps).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="499e0-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="499e0-120">See also</span></span>

- <xref:System.Windows.Controls.Primitives.Thumb>
- <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>
- <xref:System.Windows.Controls.Primitives.Thumb.DragDelta>
- <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>
