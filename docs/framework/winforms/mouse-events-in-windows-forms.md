---
title: Eventos do mouse no Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- MouseLeave event [Windows Forms]
- events [Windows Forms], mouse
- Click event [Windows Forms], raising order
- Windows Forms controls, click events
- MouseDoubleClick event [Windows Forms]
- MouseEnter event [Windows Forms]
- MouseHover event [Windows Forms]
- MouseDown event [Windows Forms]
- MouseClick event [Windows Forms]
- MouseMove event [Windows Forms]
- mouse [Windows Forms], events
- MouseUp event
ms.assetid: 8cf0070d-793b-4876-b09e-d20d28280fab
ms.openlocfilehash: 818364ceddb03df51ed656c8ff7b69fd433ac86a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64750881"
---
# <a name="mouse-events-in-windows-forms"></a><span data-ttu-id="520ca-102">Eventos do mouse no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="520ca-102">Mouse Events in Windows Forms</span></span>

<span data-ttu-id="520ca-103">Quando manipula entradas de mouse, você geralmente deseja conhecer a localização do ponteiro do mouse e o estado dos botões do mouse.</span><span class="sxs-lookup"><span data-stu-id="520ca-103">When you handle mouse input, you usually want to know the location of the mouse pointer and the state of the mouse buttons.</span></span> <span data-ttu-id="520ca-104">Este tópico fornece detalhes sobre como obter essas informações de eventos do mouse e explica a ordem em que eventos de clique do mouse são gerados em controles dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="520ca-104">This topic provides details on how to get this information from mouse events, and explains the order in which mouse click events are raised in Windows Forms controls.</span></span> <span data-ttu-id="520ca-105">Para obter uma lista e uma descrição de todos os eventos de mouse, consulte [Como a entrada do mouse funciona nos Windows Forms](how-mouse-input-works-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="520ca-105">For a list and description of all of the mouse events, see [How Mouse Input Works in Windows Forms](how-mouse-input-works-in-windows-forms.md).</span></span>  <span data-ttu-id="520ca-106">Consulte também [visão geral de manipuladores de eventos (Windows Forms)](event-handlers-overview-windows-forms.md) e [visão geral de eventos (Windows Forms)](events-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="520ca-106">Also see [Event Handlers Overview (Windows Forms)](event-handlers-overview-windows-forms.md) and [Events Overview (Windows Forms)](events-overview-windows-forms.md).</span></span>

## <a name="mouse-information"></a><span data-ttu-id="520ca-107">Informações sobre o mouse</span><span class="sxs-lookup"><span data-stu-id="520ca-107">Mouse Information</span></span>

<span data-ttu-id="520ca-108">Um <xref:System.Windows.Forms.MouseEventArgs> é enviado aos manipuladores de eventos do mouse relacionados a clicar em um botão do mouse e acompanhar os movimentos do mouse.</span><span class="sxs-lookup"><span data-stu-id="520ca-108">A <xref:System.Windows.Forms.MouseEventArgs> is sent to the handlers of mouse events related to clicking a mouse button and tracking mouse movements.</span></span> <span data-ttu-id="520ca-109"><xref:System.Windows.Forms.MouseEventArgs> Fornece informações sobre o estado atual do mouse, incluindo a localização do ponteiro do mouse em coordenadas do cliente, quais botões do mouse estão pressionados e se a roda do mouse foi rolado.</span><span class="sxs-lookup"><span data-stu-id="520ca-109"><xref:System.Windows.Forms.MouseEventArgs> provides information about the current state of the mouse, including the location of the mouse pointer in client coordinates, which mouse buttons are pressed, and whether the mouse wheel has scrolled.</span></span> <span data-ttu-id="520ca-110">Muitos eventos do mouse, como aqueles que simplesmente avisam quando o ponteiro do mouse entrou ou saiu dos limites de um controle, envie um <xref:System.EventArgs> ao manipulador de eventos sem mais informações.</span><span class="sxs-lookup"><span data-stu-id="520ca-110">Several mouse events, such as those that simply notify when the mouse pointer has entered or left the bounds of a control, send an <xref:System.EventArgs> to the event handler with no further information.</span></span>

<span data-ttu-id="520ca-111">Se você quiser saber o estado atual dos botões do mouse ou o local do ponteiro do mouse e você quiser evitar manipular um evento de mouse, você também pode usar o <xref:System.Windows.Forms.Control.MouseButtons%2A> e <xref:System.Windows.Forms.Control.MousePosition%2A> propriedades do <xref:System.Windows.Forms.Control> classe.</span><span class="sxs-lookup"><span data-stu-id="520ca-111">If you want to know the current state of the mouse buttons or the location of the mouse pointer, and you want to avoid handling a mouse event, you can also use the <xref:System.Windows.Forms.Control.MouseButtons%2A> and <xref:System.Windows.Forms.Control.MousePosition%2A> properties of the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="520ca-112"><xref:System.Windows.Forms.Control.MouseButtons%2A> Retorna informações sobre quais botões do mouse estão pressionados no momento.</span><span class="sxs-lookup"><span data-stu-id="520ca-112"><xref:System.Windows.Forms.Control.MouseButtons%2A> returns information about which mouse buttons are currently pressed.</span></span> <span data-ttu-id="520ca-113">O <xref:System.Windows.Forms.Control.MousePosition%2A> retorna as coordenadas de tela do ponteiro do mouse e é equivalente ao valor retornado por <xref:System.Windows.Forms.Cursor.Position%2A>.</span><span class="sxs-lookup"><span data-stu-id="520ca-113">The <xref:System.Windows.Forms.Control.MousePosition%2A> returns the screen coordinates of the mouse pointer and is equivalent to the value returned by <xref:System.Windows.Forms.Cursor.Position%2A>.</span></span>

## <a name="converting-between-screen-and-client-coordinates"></a><span data-ttu-id="520ca-114">Convertendo entre coordenadas de cliente e da tela</span><span class="sxs-lookup"><span data-stu-id="520ca-114">Converting Between Screen and Client Coordinates</span></span>

<span data-ttu-id="520ca-115">Como algumas informações de localização do mouse estão em coordenadas de cliente e algumas estão em coordenadas de tela, talvez seja necessário converter um ponto de um sistema de coordenadas para outro.</span><span class="sxs-lookup"><span data-stu-id="520ca-115">Because some mouse location information is in client coordinates and some is in screen coordinates, you may need to convert a point from one coordinate system to the other.</span></span> <span data-ttu-id="520ca-116">Você pode fazer isso facilmente usando o <xref:System.Windows.Forms.Control.PointToClient%2A> e <xref:System.Windows.Forms.Control.PointToScreen%2A> métodos disponíveis no <xref:System.Windows.Forms.Control> classe.</span><span class="sxs-lookup"><span data-stu-id="520ca-116">You can do this easily by using the <xref:System.Windows.Forms.Control.PointToClient%2A> and <xref:System.Windows.Forms.Control.PointToScreen%2A> methods available on the <xref:System.Windows.Forms.Control> class.</span></span>

## <a name="standard-click-event-behavior"></a><span data-ttu-id="520ca-117">Comportamento do evento de clique</span><span class="sxs-lookup"><span data-stu-id="520ca-117">Standard Click Event Behavior</span></span>

<span data-ttu-id="520ca-118">Se quiser manipular eventos de clique do mouse na ordem correta, você precisará conhecer a ordem em que os eventos de clique são gerados em controles dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="520ca-118">If you want to handle mouse click events in the proper order, you need to know the order in which click events are raised in Windows Forms controls.</span></span> <span data-ttu-id="520ca-119">Todos os controles dos Windows Forms geram eventos de clique na mesma ordem quando um botão do mouse é pressionado e liberado (independentemente de qual botão do mouse), exceto onde é indicado na lista a seguir de controles individuais.</span><span class="sxs-lookup"><span data-stu-id="520ca-119">All Windows Forms controls raise click events in the same order when a mouse button is pressed and released (regardless of which mouse button), except where noted in the following list for individual controls.</span></span> <span data-ttu-id="520ca-120">A lista a seguir mostra a ordem dos eventos gerados por um único clique do botão do mouse:</span><span class="sxs-lookup"><span data-stu-id="520ca-120">The following list shows the order of events raised for a single mouse-button click:</span></span>

1. <span data-ttu-id="520ca-121"><xref:System.Windows.Forms.Control.MouseDown> evento.</span><span class="sxs-lookup"><span data-stu-id="520ca-121"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

2. <span data-ttu-id="520ca-122"><xref:System.Windows.Forms.Control.Click> evento.</span><span class="sxs-lookup"><span data-stu-id="520ca-122"><xref:System.Windows.Forms.Control.Click> event.</span></span>

3. <span data-ttu-id="520ca-123"><xref:System.Windows.Forms.Control.MouseClick> evento.</span><span class="sxs-lookup"><span data-stu-id="520ca-123"><xref:System.Windows.Forms.Control.MouseClick> event.</span></span>

4. <span data-ttu-id="520ca-124"><xref:System.Windows.Forms.Control.MouseUp> evento.</span><span class="sxs-lookup"><span data-stu-id="520ca-124"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

<span data-ttu-id="520ca-125">A seguir, temos a ordem dos eventos gerados por um clique duplo do botão do mouse:</span><span class="sxs-lookup"><span data-stu-id="520ca-125">Following is the order of events raised for a double mouse-button click:</span></span>

1. <span data-ttu-id="520ca-126"><xref:System.Windows.Forms.Control.MouseDown> evento.</span><span class="sxs-lookup"><span data-stu-id="520ca-126"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

2. <span data-ttu-id="520ca-127"><xref:System.Windows.Forms.Control.Click> evento.</span><span class="sxs-lookup"><span data-stu-id="520ca-127"><xref:System.Windows.Forms.Control.Click> event.</span></span>

3. <span data-ttu-id="520ca-128"><xref:System.Windows.Forms.Control.MouseClick> evento.</span><span class="sxs-lookup"><span data-stu-id="520ca-128"><xref:System.Windows.Forms.Control.MouseClick> event.</span></span>

4. <span data-ttu-id="520ca-129"><xref:System.Windows.Forms.Control.MouseUp> evento.</span><span class="sxs-lookup"><span data-stu-id="520ca-129"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

5. <span data-ttu-id="520ca-130"><xref:System.Windows.Forms.Control.MouseDown> evento.</span><span class="sxs-lookup"><span data-stu-id="520ca-130"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

6. <span data-ttu-id="520ca-131"><xref:System.Windows.Forms.Control.DoubleClick> evento.</span><span class="sxs-lookup"><span data-stu-id="520ca-131"><xref:System.Windows.Forms.Control.DoubleClick> event.</span></span> <span data-ttu-id="520ca-132">(Isso pode variar, dependendo se o controle em questão tem o <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> definido como bit de estilo `true`.</span><span class="sxs-lookup"><span data-stu-id="520ca-132">(This can vary, depending on whether the control in question has the <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> style bit set to `true`.</span></span> <span data-ttu-id="520ca-133">Para obter mais informações sobre como definir um <xref:System.Windows.Forms.ControlStyles> bit, consulte o <xref:System.Windows.Forms.Control.SetStyle%2A> método.)</span><span class="sxs-lookup"><span data-stu-id="520ca-133">For more information about how to set a <xref:System.Windows.Forms.ControlStyles> bit, see the <xref:System.Windows.Forms.Control.SetStyle%2A> method.)</span></span>

7. <span data-ttu-id="520ca-134"><xref:System.Windows.Forms.Control.MouseDoubleClick> evento.</span><span class="sxs-lookup"><span data-stu-id="520ca-134"><xref:System.Windows.Forms.Control.MouseDoubleClick> event.</span></span>

8. <span data-ttu-id="520ca-135"><xref:System.Windows.Forms.Control.MouseUp> evento.</span><span class="sxs-lookup"><span data-stu-id="520ca-135"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

<span data-ttu-id="520ca-136">Para obter um exemplo de código que mostra a ordem do mouse, clique em eventos, consulte [como: Entrada do usuário de identificador de eventos nos Windows Forms a controles](how-to-handle-user-input-events-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="520ca-136">For a code example that demonstrates the order of the mouse click events, see [How to: Handle User Input Events in Windows Forms Controls](how-to-handle-user-input-events-in-windows-forms-controls.md).</span></span>

### <a name="individual-controls"></a><span data-ttu-id="520ca-137">Controles individuais</span><span class="sxs-lookup"><span data-stu-id="520ca-137">Individual Controls</span></span>

<span data-ttu-id="520ca-138">Os controles a seguir não estão em conformidade com o comportamento padrão dos eventos de clique do mouse:</span><span class="sxs-lookup"><span data-stu-id="520ca-138">The following controls do not conform to the standard mouse click event behavior:</span></span>

- <span data-ttu-id="520ca-139"><xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.ComboBox>, e <xref:System.Windows.Forms.RadioButton> controles</span><span class="sxs-lookup"><span data-stu-id="520ca-139"><xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.ComboBox>, and <xref:System.Windows.Forms.RadioButton> controls</span></span>

  > [!NOTE]
  > <span data-ttu-id="520ca-140">Para o <xref:System.Windows.Forms.ComboBox> controle, o comportamento do evento detalhado a seguir ocorre se o usuário clicar no campo de edição, o botão, ou em um item dentro da lista.</span><span class="sxs-lookup"><span data-stu-id="520ca-140">For the <xref:System.Windows.Forms.ComboBox> control, the event behavior detailed later occurs if the user clicks on the edit field, the button, or on an item within the list.</span></span>

  - <span data-ttu-id="520ca-141">Com o botão esquerdo: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="520ca-141">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="520ca-142">Clique com botão direito: Nenhum evento de clique gerado</span><span class="sxs-lookup"><span data-stu-id="520ca-142">Right click: No click events raised</span></span>

  - <span data-ttu-id="520ca-143">Clique duas vezes à esquerda: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="520ca-143">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="520ca-144">Clique duas vezes à direita: Nenhum evento de clique gerado</span><span class="sxs-lookup"><span data-stu-id="520ca-144">Right double-click: No click events raised</span></span>

- <span data-ttu-id="520ca-145"><xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox>, e <xref:System.Windows.Forms.CheckedListBox> controles</span><span class="sxs-lookup"><span data-stu-id="520ca-145"><xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox>, and <xref:System.Windows.Forms.CheckedListBox> controls</span></span>

  > [!NOTE]
  > <span data-ttu-id="520ca-146">O comportamento do evento detalhado a seguir ocorre quando o usuário clica em qualquer lugar desses controles.</span><span class="sxs-lookup"><span data-stu-id="520ca-146">The event behavior detailed later occurs when the user clicks anywhere within these controls.</span></span>

  - <span data-ttu-id="520ca-147">Com o botão esquerdo: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="520ca-147">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="520ca-148">Clique com botão direito: Nenhum evento de clique gerado</span><span class="sxs-lookup"><span data-stu-id="520ca-148">Right click: No click events raised</span></span>

  - <span data-ttu-id="520ca-149">Clique duas vezes à esquerda: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="520ca-149">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="520ca-150">Clique duas vezes à direita: Nenhum evento de clique gerado</span><span class="sxs-lookup"><span data-stu-id="520ca-150">Right double-click: No click events raised</span></span>

- <span data-ttu-id="520ca-151">Controle <xref:System.Windows.Forms.ListView></span><span class="sxs-lookup"><span data-stu-id="520ca-151"><xref:System.Windows.Forms.ListView> control</span></span>

  > [!NOTE]
  > <span data-ttu-id="520ca-152">O comportamento do evento detalhado a seguir ocorre apenas quando o usuário clica nos itens a <xref:System.Windows.Forms.ListView> controle.</span><span class="sxs-lookup"><span data-stu-id="520ca-152">The event behavior detailed later occurs only when the user clicks on the items in the <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="520ca-153">Nenhum evento é gerado para cliques em qualquer outro lugar no controle.</span><span class="sxs-lookup"><span data-stu-id="520ca-153">No events are raised for clicks anywhere else on the control.</span></span> <span data-ttu-id="520ca-154">Além dos eventos descritos mais adiante, existem os <xref:System.Windows.Forms.ListView.BeforeLabelEdit> e <xref:System.Windows.Forms.ListView.AfterLabelEdit> eventos, que podem ser de seu interesse se você quiser usar a validação com o <xref:System.Windows.Forms.ListView> controle.</span><span class="sxs-lookup"><span data-stu-id="520ca-154">In addition to the events described later, there are the <xref:System.Windows.Forms.ListView.BeforeLabelEdit> and <xref:System.Windows.Forms.ListView.AfterLabelEdit> events, which may be of interest to you if you want to use validation with the <xref:System.Windows.Forms.ListView> control.</span></span>

  - <span data-ttu-id="520ca-155">Com o botão esquerdo: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="520ca-155">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="520ca-156">Clique com botão direito: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="520ca-156">Right click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="520ca-157">Clique duas vezes à esquerda: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="520ca-157">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="520ca-158">À direita, clique duas vezes: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="520ca-158">Right double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

- <span data-ttu-id="520ca-159">Controle <xref:System.Windows.Forms.TreeView></span><span class="sxs-lookup"><span data-stu-id="520ca-159"><xref:System.Windows.Forms.TreeView> control</span></span>

  > [!NOTE]
  > <span data-ttu-id="520ca-160">O comportamento do evento detalhado a seguir ocorre apenas quando o usuário clica nos próprios itens ou à direita dos itens no <xref:System.Windows.Forms.TreeView> controle.</span><span class="sxs-lookup"><span data-stu-id="520ca-160">The event behavior detailed later occurs only when the user clicks on the items themselves or to the right of the items in the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="520ca-161">Nenhum evento é gerado para cliques em qualquer outro lugar no controle.</span><span class="sxs-lookup"><span data-stu-id="520ca-161">No events are raised for clicks anywhere else on the control.</span></span> <span data-ttu-id="520ca-162">Além dos descritos mais adiante, há o <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck>, e <xref:System.Windows.Forms.TreeView.AfterLabelEdit> eventos, que podem ser de seu interesse se você quiser usar a validação com o <xref:System.Windows.Forms.TreeView> controle .</span><span class="sxs-lookup"><span data-stu-id="520ca-162">In addition to those described later, there are the <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck>, and <xref:System.Windows.Forms.TreeView.AfterLabelEdit> events, which may be of interest to you if you want to use validation with the <xref:System.Windows.Forms.TreeView> control.</span></span>

  - <span data-ttu-id="520ca-163">Com o botão esquerdo: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="520ca-163">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="520ca-164">Clique com botão direito: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="520ca-164">Right click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="520ca-165">Clique duas vezes à esquerda: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="520ca-165">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="520ca-166">À direita, clique duas vezes: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="520ca-166">Right double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

### <a name="painting-behavior-of-toggle-controls"></a><span data-ttu-id="520ca-167">Comportamento de pintura dos controles de alternância</span><span class="sxs-lookup"><span data-stu-id="520ca-167">Painting Behavior of Toggle Controls</span></span>

<span data-ttu-id="520ca-168">Ativar/desativar controles, como os controles que derivam de <xref:System.Windows.Forms.ButtonBase> de classe, ter o seguinte comportamento de pintura distinto em combinação com o mouse eventos de clique:</span><span class="sxs-lookup"><span data-stu-id="520ca-168">Toggle controls, such as the controls deriving from the <xref:System.Windows.Forms.ButtonBase> class, have the following distinctive painting behavior in combination with mouse click events:</span></span>

1. <span data-ttu-id="520ca-169">O usuário pressiona o botão do mouse.</span><span class="sxs-lookup"><span data-stu-id="520ca-169">The user presses the mouse button.</span></span>

2. <span data-ttu-id="520ca-170">O controle pinta no estado pressionado.</span><span class="sxs-lookup"><span data-stu-id="520ca-170">The control paints in the pressed state.</span></span>

3. <span data-ttu-id="520ca-171">O <xref:System.Windows.Forms.Control.MouseDown> é gerado.</span><span class="sxs-lookup"><span data-stu-id="520ca-171">The <xref:System.Windows.Forms.Control.MouseDown> event is raised.</span></span>

4. <span data-ttu-id="520ca-172">O usuário libera o botão do mouse.</span><span class="sxs-lookup"><span data-stu-id="520ca-172">The user releases the mouse button.</span></span>

5. <span data-ttu-id="520ca-173">O controle pinta no estado elevado.</span><span class="sxs-lookup"><span data-stu-id="520ca-173">The control paints in the raised state.</span></span>

6. <span data-ttu-id="520ca-174">O <xref:System.Windows.Forms.Control.Click> é gerado.</span><span class="sxs-lookup"><span data-stu-id="520ca-174">The <xref:System.Windows.Forms.Control.Click> event is raised.</span></span>

7. <span data-ttu-id="520ca-175">O <xref:System.Windows.Forms.Control.MouseClick> é gerado.</span><span class="sxs-lookup"><span data-stu-id="520ca-175">The <xref:System.Windows.Forms.Control.MouseClick> event is raised.</span></span>

8. <span data-ttu-id="520ca-176">O <xref:System.Windows.Forms.Control.MouseUp> é gerado.</span><span class="sxs-lookup"><span data-stu-id="520ca-176">The <xref:System.Windows.Forms.Control.MouseUp> event is raised.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="520ca-177">Se o usuário move o ponteiro para fora do controle de alternância enquanto o botão do mouse está pressionado (como mover o mouse o <xref:System.Windows.Forms.Button> controlar enquanto ele está pressionado), o controle de alternância pintará no solto estado e somente o <xref:System.Windows.Forms.Control.MouseUp> evento ocorre.</span><span class="sxs-lookup"><span data-stu-id="520ca-177">If the user moves the pointer out of the toggle control while the mouse button is down (such as moving the mouse off the <xref:System.Windows.Forms.Button> control while it is pressed), the toggle control will paint in the raised state and only the <xref:System.Windows.Forms.Control.MouseUp> event occurs.</span></span> <span data-ttu-id="520ca-178">O <xref:System.Windows.Forms.Control.Click> ou <xref:System.Windows.Forms.Control.MouseClick> eventos não ocorrerão nesta situação.</span><span class="sxs-lookup"><span data-stu-id="520ca-178">The <xref:System.Windows.Forms.Control.Click> or <xref:System.Windows.Forms.Control.MouseClick> events will not occur in this situation.</span></span>

## <a name="see-also"></a><span data-ttu-id="520ca-179">Consulte também</span><span class="sxs-lookup"><span data-stu-id="520ca-179">See also</span></span>

- [<span data-ttu-id="520ca-180">Entrada do mouse em um Aplicativo do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="520ca-180">Mouse Input in a Windows Forms Application</span></span>](mouse-input-in-a-windows-forms-application.md)
