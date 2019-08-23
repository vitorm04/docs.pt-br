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
ms.openlocfilehash: 181d01f6e688b94876f77155bf598aba129e9fbf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949905"
---
# <a name="mouse-events-in-windows-forms"></a><span data-ttu-id="8b78b-102">Eventos do mouse no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8b78b-102">Mouse Events in Windows Forms</span></span>

<span data-ttu-id="8b78b-103">Quando manipula entradas de mouse, você geralmente deseja conhecer a localização do ponteiro do mouse e o estado dos botões do mouse.</span><span class="sxs-lookup"><span data-stu-id="8b78b-103">When you handle mouse input, you usually want to know the location of the mouse pointer and the state of the mouse buttons.</span></span> <span data-ttu-id="8b78b-104">Este tópico fornece detalhes sobre como obter essas informações de eventos do mouse e explica a ordem em que eventos de clique do mouse são gerados em controles dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="8b78b-104">This topic provides details on how to get this information from mouse events, and explains the order in which mouse click events are raised in Windows Forms controls.</span></span> <span data-ttu-id="8b78b-105">Para obter uma lista e uma descrição de todos os eventos de mouse, consulte [Como a entrada do mouse funciona nos Windows Forms](how-mouse-input-works-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="8b78b-105">For a list and description of all of the mouse events, see [How Mouse Input Works in Windows Forms](how-mouse-input-works-in-windows-forms.md).</span></span>  <span data-ttu-id="8b78b-106">Consulte também visão geral de manipuladores de [eventos (Windows Forms)](event-handlers-overview-windows-forms.md) e [visão geral de eventos (Windows Forms)](events-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="8b78b-106">Also see [Event Handlers Overview (Windows Forms)](event-handlers-overview-windows-forms.md) and [Events Overview (Windows Forms)](events-overview-windows-forms.md).</span></span>

## <a name="mouse-information"></a><span data-ttu-id="8b78b-107">Informações sobre o mouse</span><span class="sxs-lookup"><span data-stu-id="8b78b-107">Mouse Information</span></span>

<span data-ttu-id="8b78b-108">Um <xref:System.Windows.Forms.MouseEventArgs> é enviado aos manipuladores de eventos do mouse relacionados ao clique de um botão do mouse e do controle dos movimentos do mouse.</span><span class="sxs-lookup"><span data-stu-id="8b78b-108">A <xref:System.Windows.Forms.MouseEventArgs> is sent to the handlers of mouse events related to clicking a mouse button and tracking mouse movements.</span></span> <span data-ttu-id="8b78b-109"><xref:System.Windows.Forms.MouseEventArgs>fornece informações sobre o estado atual do mouse, incluindo o local do ponteiro do mouse em coordenadas do cliente, quais botões do mouse são pressionados e se a roda do mouse foi rolada.</span><span class="sxs-lookup"><span data-stu-id="8b78b-109"><xref:System.Windows.Forms.MouseEventArgs> provides information about the current state of the mouse, including the location of the mouse pointer in client coordinates, which mouse buttons are pressed, and whether the mouse wheel has scrolled.</span></span> <span data-ttu-id="8b78b-110">Vários eventos de mouse, como aqueles que simplesmente notificam quando o ponteiro do mouse inseriu ou deixaram os limites de um controle, enviam um <xref:System.EventArgs> para o manipulador de eventos sem informações adicionais.</span><span class="sxs-lookup"><span data-stu-id="8b78b-110">Several mouse events, such as those that simply notify when the mouse pointer has entered or left the bounds of a control, send an <xref:System.EventArgs> to the event handler with no further information.</span></span>

<span data-ttu-id="8b78b-111">Se você quiser saber o estado atual dos botões do mouse ou o local do ponteiro do mouse e desejar evitar manipular um evento do mouse, também poderá usar as <xref:System.Windows.Forms.Control.MouseButtons%2A> Propriedades e <xref:System.Windows.Forms.Control.MousePosition%2A> da <xref:System.Windows.Forms.Control> classe.</span><span class="sxs-lookup"><span data-stu-id="8b78b-111">If you want to know the current state of the mouse buttons or the location of the mouse pointer, and you want to avoid handling a mouse event, you can also use the <xref:System.Windows.Forms.Control.MouseButtons%2A> and <xref:System.Windows.Forms.Control.MousePosition%2A> properties of the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="8b78b-112"><xref:System.Windows.Forms.Control.MouseButtons%2A>Retorna informações sobre quais botões do mouse estão pressionados no momento.</span><span class="sxs-lookup"><span data-stu-id="8b78b-112"><xref:System.Windows.Forms.Control.MouseButtons%2A> returns information about which mouse buttons are currently pressed.</span></span> <span data-ttu-id="8b78b-113">O <xref:System.Windows.Forms.Control.MousePosition%2A> retorna as coordenadas de tela do ponteiro do mouse e é equivalente ao valor retornado por <xref:System.Windows.Forms.Cursor.Position%2A>.</span><span class="sxs-lookup"><span data-stu-id="8b78b-113">The <xref:System.Windows.Forms.Control.MousePosition%2A> returns the screen coordinates of the mouse pointer and is equivalent to the value returned by <xref:System.Windows.Forms.Cursor.Position%2A>.</span></span>

## <a name="converting-between-screen-and-client-coordinates"></a><span data-ttu-id="8b78b-114">Convertendo entre coordenadas de cliente e da tela</span><span class="sxs-lookup"><span data-stu-id="8b78b-114">Converting Between Screen and Client Coordinates</span></span>

<span data-ttu-id="8b78b-115">Como algumas informações de localização do mouse estão em coordenadas de cliente e algumas estão em coordenadas de tela, talvez seja necessário converter um ponto de um sistema de coordenadas para outro.</span><span class="sxs-lookup"><span data-stu-id="8b78b-115">Because some mouse location information is in client coordinates and some is in screen coordinates, you may need to convert a point from one coordinate system to the other.</span></span> <span data-ttu-id="8b78b-116">Você pode fazer isso facilmente usando os <xref:System.Windows.Forms.Control.PointToClient%2A> métodos e <xref:System.Windows.Forms.Control.PointToScreen%2A> disponíveis na <xref:System.Windows.Forms.Control> classe.</span><span class="sxs-lookup"><span data-stu-id="8b78b-116">You can do this easily by using the <xref:System.Windows.Forms.Control.PointToClient%2A> and <xref:System.Windows.Forms.Control.PointToScreen%2A> methods available on the <xref:System.Windows.Forms.Control> class.</span></span>

## <a name="standard-click-event-behavior"></a><span data-ttu-id="8b78b-117">Comportamento do evento de clique</span><span class="sxs-lookup"><span data-stu-id="8b78b-117">Standard Click Event Behavior</span></span>

<span data-ttu-id="8b78b-118">Se quiser manipular eventos de clique do mouse na ordem correta, você precisará conhecer a ordem em que os eventos de clique são gerados em controles dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="8b78b-118">If you want to handle mouse click events in the proper order, you need to know the order in which click events are raised in Windows Forms controls.</span></span> <span data-ttu-id="8b78b-119">Todos os controles dos Windows Forms geram eventos de clique na mesma ordem quando um botão do mouse é pressionado e liberado (independentemente de qual botão do mouse), exceto onde é indicado na lista a seguir de controles individuais.</span><span class="sxs-lookup"><span data-stu-id="8b78b-119">All Windows Forms controls raise click events in the same order when a mouse button is pressed and released (regardless of which mouse button), except where noted in the following list for individual controls.</span></span> <span data-ttu-id="8b78b-120">A lista a seguir mostra a ordem dos eventos gerados por um único clique do botão do mouse:</span><span class="sxs-lookup"><span data-stu-id="8b78b-120">The following list shows the order of events raised for a single mouse-button click:</span></span>

1. <span data-ttu-id="8b78b-121"><xref:System.Windows.Forms.Control.MouseDown>circunstância.</span><span class="sxs-lookup"><span data-stu-id="8b78b-121"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

2. <span data-ttu-id="8b78b-122"><xref:System.Windows.Forms.Control.Click>circunstância.</span><span class="sxs-lookup"><span data-stu-id="8b78b-122"><xref:System.Windows.Forms.Control.Click> event.</span></span>

3. <span data-ttu-id="8b78b-123"><xref:System.Windows.Forms.Control.MouseClick>circunstância.</span><span class="sxs-lookup"><span data-stu-id="8b78b-123"><xref:System.Windows.Forms.Control.MouseClick> event.</span></span>

4. <span data-ttu-id="8b78b-124"><xref:System.Windows.Forms.Control.MouseUp>circunstância.</span><span class="sxs-lookup"><span data-stu-id="8b78b-124"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

<span data-ttu-id="8b78b-125">A seguir, temos a ordem dos eventos gerados por um clique duplo do botão do mouse:</span><span class="sxs-lookup"><span data-stu-id="8b78b-125">Following is the order of events raised for a double mouse-button click:</span></span>

1. <span data-ttu-id="8b78b-126"><xref:System.Windows.Forms.Control.MouseDown>circunstância.</span><span class="sxs-lookup"><span data-stu-id="8b78b-126"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

2. <span data-ttu-id="8b78b-127"><xref:System.Windows.Forms.Control.Click>circunstância.</span><span class="sxs-lookup"><span data-stu-id="8b78b-127"><xref:System.Windows.Forms.Control.Click> event.</span></span>

3. <span data-ttu-id="8b78b-128"><xref:System.Windows.Forms.Control.MouseClick>circunstância.</span><span class="sxs-lookup"><span data-stu-id="8b78b-128"><xref:System.Windows.Forms.Control.MouseClick> event.</span></span>

4. <span data-ttu-id="8b78b-129"><xref:System.Windows.Forms.Control.MouseUp>circunstância.</span><span class="sxs-lookup"><span data-stu-id="8b78b-129"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

5. <span data-ttu-id="8b78b-130"><xref:System.Windows.Forms.Control.MouseDown>circunstância.</span><span class="sxs-lookup"><span data-stu-id="8b78b-130"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

6. <span data-ttu-id="8b78b-131"><xref:System.Windows.Forms.Control.DoubleClick>circunstância.</span><span class="sxs-lookup"><span data-stu-id="8b78b-131"><xref:System.Windows.Forms.Control.DoubleClick> event.</span></span> <span data-ttu-id="8b78b-132">(Isso pode variar, dependendo se o controle em questão tem o <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> bit de estilo definido como. `true`</span><span class="sxs-lookup"><span data-stu-id="8b78b-132">(This can vary, depending on whether the control in question has the <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> style bit set to `true`.</span></span> <span data-ttu-id="8b78b-133">Para obter mais informações sobre como definir um <xref:System.Windows.Forms.ControlStyles> bit, consulte o <xref:System.Windows.Forms.Control.SetStyle%2A> método.)</span><span class="sxs-lookup"><span data-stu-id="8b78b-133">For more information about how to set a <xref:System.Windows.Forms.ControlStyles> bit, see the <xref:System.Windows.Forms.Control.SetStyle%2A> method.)</span></span>

7. <span data-ttu-id="8b78b-134"><xref:System.Windows.Forms.Control.MouseDoubleClick>circunstância.</span><span class="sxs-lookup"><span data-stu-id="8b78b-134"><xref:System.Windows.Forms.Control.MouseDoubleClick> event.</span></span>

8. <span data-ttu-id="8b78b-135"><xref:System.Windows.Forms.Control.MouseUp>circunstância.</span><span class="sxs-lookup"><span data-stu-id="8b78b-135"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

<span data-ttu-id="8b78b-136">Para obter um exemplo de código que demonstra a ordem dos eventos de clique do [mouse, consulte Como: Manipular eventos de entrada do usuário em](how-to-handle-user-input-events-in-windows-forms-controls.md)controles Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="8b78b-136">For a code example that demonstrates the order of the mouse click events, see [How to: Handle User Input Events in Windows Forms Controls](how-to-handle-user-input-events-in-windows-forms-controls.md).</span></span>

### <a name="individual-controls"></a><span data-ttu-id="8b78b-137">Controles individuais</span><span class="sxs-lookup"><span data-stu-id="8b78b-137">Individual Controls</span></span>

<span data-ttu-id="8b78b-138">Os controles a seguir não estão em conformidade com o comportamento padrão dos eventos de clique do mouse:</span><span class="sxs-lookup"><span data-stu-id="8b78b-138">The following controls do not conform to the standard mouse click event behavior:</span></span>

- <span data-ttu-id="8b78b-139"><xref:System.Windows.Forms.Button>controles, <xref:System.Windows.Forms.CheckBox>, e<xref:System.Windows.Forms.RadioButton> <xref:System.Windows.Forms.ComboBox></span><span class="sxs-lookup"><span data-stu-id="8b78b-139"><xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.ComboBox>, and <xref:System.Windows.Forms.RadioButton> controls</span></span>

  > [!NOTE]
  > <span data-ttu-id="8b78b-140">Para o <xref:System.Windows.Forms.ComboBox> controle, o comportamento de evento detalhado posteriormente ocorrerá se o usuário clicar no campo de edição, no botão ou em um item dentro da lista.</span><span class="sxs-lookup"><span data-stu-id="8b78b-140">For the <xref:System.Windows.Forms.ComboBox> control, the event behavior detailed later occurs if the user clicks on the edit field, the button, or on an item within the list.</span></span>

  - <span data-ttu-id="8b78b-141">Clique com o <xref:System.Windows.Forms.Control.Click>botão esquerdo:,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="8b78b-141">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="8b78b-142">Clique com o botão direito do mouse: Nenhum evento de clique gerado</span><span class="sxs-lookup"><span data-stu-id="8b78b-142">Right click: No click events raised</span></span>

  - <span data-ttu-id="8b78b-143">Clique duas vezes com o <xref:System.Windows.Forms.Control.Click>botão <xref:System.Windows.Forms.Control.MouseClick>esquerdo:,; <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="8b78b-143">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="8b78b-144">Clique duas vezes com o botão direito: Nenhum evento de clique gerado</span><span class="sxs-lookup"><span data-stu-id="8b78b-144">Right double-click: No click events raised</span></span>

- <span data-ttu-id="8b78b-145"><xref:System.Windows.Forms.TextBox>controles, <xref:System.Windows.Forms.RichTextBox>,, e<xref:System.Windows.Forms.CheckedListBox> <xref:System.Windows.Forms.ListBox> <xref:System.Windows.Forms.MaskedTextBox></span><span class="sxs-lookup"><span data-stu-id="8b78b-145"><xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox>, and <xref:System.Windows.Forms.CheckedListBox> controls</span></span>

  > [!NOTE]
  > <span data-ttu-id="8b78b-146">O comportamento do evento detalhado a seguir ocorre quando o usuário clica em qualquer lugar desses controles.</span><span class="sxs-lookup"><span data-stu-id="8b78b-146">The event behavior detailed later occurs when the user clicks anywhere within these controls.</span></span>

  - <span data-ttu-id="8b78b-147">Clique com o <xref:System.Windows.Forms.Control.Click>botão esquerdo:,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="8b78b-147">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="8b78b-148">Clique com o botão direito do mouse: Nenhum evento de clique gerado</span><span class="sxs-lookup"><span data-stu-id="8b78b-148">Right click: No click events raised</span></span>

  - <span data-ttu-id="8b78b-149">Clique duas vezes com o <xref:System.Windows.Forms.Control.Click>botão <xref:System.Windows.Forms.Control.MouseClick>esquerdo <xref:System.Windows.Forms.Control.DoubleClick>:,,,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="8b78b-149">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="8b78b-150">Clique duas vezes com o botão direito: Nenhum evento de clique gerado</span><span class="sxs-lookup"><span data-stu-id="8b78b-150">Right double-click: No click events raised</span></span>

- <span data-ttu-id="8b78b-151">Controle <xref:System.Windows.Forms.ListView></span><span class="sxs-lookup"><span data-stu-id="8b78b-151"><xref:System.Windows.Forms.ListView> control</span></span>

  > [!NOTE]
  > <span data-ttu-id="8b78b-152">O comportamento de evento detalhado posteriormente ocorre somente quando o usuário clica nos itens no <xref:System.Windows.Forms.ListView> controle.</span><span class="sxs-lookup"><span data-stu-id="8b78b-152">The event behavior detailed later occurs only when the user clicks on the items in the <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="8b78b-153">Nenhum evento é gerado para cliques em qualquer outro lugar no controle.</span><span class="sxs-lookup"><span data-stu-id="8b78b-153">No events are raised for clicks anywhere else on the control.</span></span> <span data-ttu-id="8b78b-154">Além dos eventos descritos posteriormente, há os <xref:System.Windows.Forms.ListView.BeforeLabelEdit> eventos e <xref:System.Windows.Forms.ListView.AfterLabelEdit> , que podem ser de seu interesse se você quiser usar a validação com o <xref:System.Windows.Forms.ListView> controle.</span><span class="sxs-lookup"><span data-stu-id="8b78b-154">In addition to the events described later, there are the <xref:System.Windows.Forms.ListView.BeforeLabelEdit> and <xref:System.Windows.Forms.ListView.AfterLabelEdit> events, which may be of interest to you if you want to use validation with the <xref:System.Windows.Forms.ListView> control.</span></span>

  - <span data-ttu-id="8b78b-155">Clique com o <xref:System.Windows.Forms.Control.Click>botão esquerdo:,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="8b78b-155">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="8b78b-156">Clique com o <xref:System.Windows.Forms.Control.Click>botão direito do mouse em:<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="8b78b-156">Right click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="8b78b-157">Clique duas vezes com o <xref:System.Windows.Forms.Control.Click>botão <xref:System.Windows.Forms.Control.MouseClick>esquerdo:,; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="8b78b-157">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="8b78b-158">Clique duas vezes com o <xref:System.Windows.Forms.Control.Click>botão <xref:System.Windows.Forms.Control.MouseClick>direito do mouse:,; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="8b78b-158">Right double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

- <span data-ttu-id="8b78b-159">Controle <xref:System.Windows.Forms.TreeView></span><span class="sxs-lookup"><span data-stu-id="8b78b-159"><xref:System.Windows.Forms.TreeView> control</span></span>

  > [!NOTE]
  > <span data-ttu-id="8b78b-160">O comportamento de evento detalhado posteriormente ocorre somente quando o usuário clica nos itens em si ou à direita dos itens no <xref:System.Windows.Forms.TreeView> controle.</span><span class="sxs-lookup"><span data-stu-id="8b78b-160">The event behavior detailed later occurs only when the user clicks on the items themselves or to the right of the items in the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="8b78b-161">Nenhum evento é gerado para cliques em qualquer outro lugar no controle.</span><span class="sxs-lookup"><span data-stu-id="8b78b-161">No events are raised for clicks anywhere else on the control.</span></span> <span data-ttu-id="8b78b-162">Além daqueles descritos posteriormente <xref:System.Windows.Forms.TreeView.BeforeCheck>, há os eventos <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterCheck> <xref:System.Windows.Forms.TreeView.AfterSelect> <xref:System.Windows.Forms.TreeView.BeforeSelect>,,, e <xref:System.Windows.Forms.TreeView.AfterLabelEdit> , que podem ser de seu interesse se você quiser usar a validação com o <xref:System.Windows.Forms.TreeView> controle .</span><span class="sxs-lookup"><span data-stu-id="8b78b-162">In addition to those described later, there are the <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck>, and <xref:System.Windows.Forms.TreeView.AfterLabelEdit> events, which may be of interest to you if you want to use validation with the <xref:System.Windows.Forms.TreeView> control.</span></span>

  - <span data-ttu-id="8b78b-163">Clique com o <xref:System.Windows.Forms.Control.Click>botão esquerdo:,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="8b78b-163">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="8b78b-164">Clique com o <xref:System.Windows.Forms.Control.Click>botão direito do mouse em:<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="8b78b-164">Right click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="8b78b-165">Clique duas vezes com o <xref:System.Windows.Forms.Control.Click>botão <xref:System.Windows.Forms.Control.MouseClick>esquerdo:,; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="8b78b-165">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="8b78b-166">Clique duas vezes com o <xref:System.Windows.Forms.Control.Click>botão <xref:System.Windows.Forms.Control.MouseClick>direito do mouse:,; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="8b78b-166">Right double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

### <a name="painting-behavior-of-toggle-controls"></a><span data-ttu-id="8b78b-167">Comportamento de pintura dos controles de alternância</span><span class="sxs-lookup"><span data-stu-id="8b78b-167">Painting Behavior of Toggle Controls</span></span>

<span data-ttu-id="8b78b-168">Os controles de alternância, como os controles derivados da <xref:System.Windows.Forms.ButtonBase> classe, têm o seguinte comportamento de pintura distinto em combinação com eventos de clique do mouse:</span><span class="sxs-lookup"><span data-stu-id="8b78b-168">Toggle controls, such as the controls deriving from the <xref:System.Windows.Forms.ButtonBase> class, have the following distinctive painting behavior in combination with mouse click events:</span></span>

1. <span data-ttu-id="8b78b-169">O usuário pressiona o botão do mouse.</span><span class="sxs-lookup"><span data-stu-id="8b78b-169">The user presses the mouse button.</span></span>

2. <span data-ttu-id="8b78b-170">O controle pinta no estado pressionado.</span><span class="sxs-lookup"><span data-stu-id="8b78b-170">The control paints in the pressed state.</span></span>

3. <span data-ttu-id="8b78b-171">O <xref:System.Windows.Forms.Control.MouseDown> evento é gerado.</span><span class="sxs-lookup"><span data-stu-id="8b78b-171">The <xref:System.Windows.Forms.Control.MouseDown> event is raised.</span></span>

4. <span data-ttu-id="8b78b-172">O usuário libera o botão do mouse.</span><span class="sxs-lookup"><span data-stu-id="8b78b-172">The user releases the mouse button.</span></span>

5. <span data-ttu-id="8b78b-173">O controle pinta no estado elevado.</span><span class="sxs-lookup"><span data-stu-id="8b78b-173">The control paints in the raised state.</span></span>

6. <span data-ttu-id="8b78b-174">O <xref:System.Windows.Forms.Control.Click> evento é gerado.</span><span class="sxs-lookup"><span data-stu-id="8b78b-174">The <xref:System.Windows.Forms.Control.Click> event is raised.</span></span>

7. <span data-ttu-id="8b78b-175">O <xref:System.Windows.Forms.Control.MouseClick> evento é gerado.</span><span class="sxs-lookup"><span data-stu-id="8b78b-175">The <xref:System.Windows.Forms.Control.MouseClick> event is raised.</span></span>

8. <span data-ttu-id="8b78b-176">O <xref:System.Windows.Forms.Control.MouseUp> evento é gerado.</span><span class="sxs-lookup"><span data-stu-id="8b78b-176">The <xref:System.Windows.Forms.Control.MouseUp> event is raised.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8b78b-177">Se o usuário mover o ponteiro para fora do controle de alternância enquanto o botão do mouse estiver inoperante (como mover o mouse para <xref:System.Windows.Forms.Button> fora do controle enquanto ele é pressionado), o controle de alternância será pintado no estado gerado e <xref:System.Windows.Forms.Control.MouseUp> apenas o evento ocorrerá.</span><span class="sxs-lookup"><span data-stu-id="8b78b-177">If the user moves the pointer out of the toggle control while the mouse button is down (such as moving the mouse off the <xref:System.Windows.Forms.Button> control while it is pressed), the toggle control will paint in the raised state and only the <xref:System.Windows.Forms.Control.MouseUp> event occurs.</span></span> <span data-ttu-id="8b78b-178">Os <xref:System.Windows.Forms.Control.Click> eventos <xref:System.Windows.Forms.Control.MouseClick> ou não ocorrerão nessa situação.</span><span class="sxs-lookup"><span data-stu-id="8b78b-178">The <xref:System.Windows.Forms.Control.Click> or <xref:System.Windows.Forms.Control.MouseClick> events will not occur in this situation.</span></span>

## <a name="see-also"></a><span data-ttu-id="8b78b-179">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8b78b-179">See also</span></span>

- [<span data-ttu-id="8b78b-180">Entrada do mouse em um Aplicativo do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8b78b-180">Mouse Input in a Windows Forms Application</span></span>](mouse-input-in-a-windows-forms-application.md)
