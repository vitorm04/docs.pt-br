---
title: 'Como: conectar vários eventos a um único manipulador de eventos'
description: Saiba como conectar vários eventos a um único manipulador de eventos no Windows Forms usando a exibição de eventos do janela Propriedades em C#.
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- events [Windows Forms], connecting multiple to single event handler
- event handlers [Windows Forms], connecting events to
- menus [Windows Forms], event-handling methods for multiple menu items
- Windows Forms controls, events
- menu items [Windows Forms], multicasting event-handling methods
ms.assetid: 5a20749a-41b5-4acc-8eb1-9e5040b0a2c4
ms.openlocfilehash: cca85c223b46d9a82dbc3e34e3377fb83c075959
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621880"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a><span data-ttu-id="71618-103">Como: conectar vários eventos a um único manipulador de eventos no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="71618-103">How to: Connect Multiple Events to a Single Event Handler in Windows Forms</span></span>
<span data-ttu-id="71618-104">No projeto do seu aplicativo, talvez seja necessário usar um único manipulador de eventos para vários eventos ou fazer com que vários eventos executem o mesmo procedimento.</span><span class="sxs-lookup"><span data-stu-id="71618-104">In your application design, you may find it necessary to use a single event handler for multiple events or have multiple events perform the same procedure.</span></span> <span data-ttu-id="71618-105">Por exemplo, fazer um comando de menu gerar o mesmo evento que um botão no seu formulário geralmente representará uma grande economia de tempo se eles expuserem a mesma funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="71618-105">For example, it is often a powerful time-saver to have a menu command raise the same event as a button on your form does if they expose the same functionality.</span></span> <span data-ttu-id="71618-106">Você pode fazer isso usando a exibição Eventos da janela Propriedades em C# ou usando a palavra-chave `Handles` e as caixas suspensas **Nome de Classe** e **Nome do Método** no Editor de Código do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="71618-106">You can do this by using the Events view of the Properties window in C# or using the `Handles` keyword and the **Class Name** and **Method Name** drop-down boxes in the Visual Basic Code Editor.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a><span data-ttu-id="71618-107">Conectar vários eventos a um único manipulador de eventos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="71618-107">To connect multiple events to a single event handler in Visual Basic</span></span>  
  
1. <span data-ttu-id="71618-108">Clique com o botão direito do mouse no formulário e escolha **Exibir Código**.</span><span class="sxs-lookup"><span data-stu-id="71618-108">Right-click the form and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="71618-109">Na caixa suspensa **Nome de Classe**, selecione um dos controles que você deseja que o manipulador de eventos trate.</span><span class="sxs-lookup"><span data-stu-id="71618-109">From the **Class Name** drop-down box, select one of the controls that you want to have the event handler handle.</span></span>  
  
3. <span data-ttu-id="71618-110">Na caixa suspensa **Nome de Método**, selecione um dos eventos que você deseja que o manipulador de eventos trate.</span><span class="sxs-lookup"><span data-stu-id="71618-110">From the **Method Name** drop-down box, select one of the events that you want the event handler to handle.</span></span>  
  
4. <span data-ttu-id="71618-111">O Editor de Código insere o manipulador de eventos apropriado e posiciona o ponto de inserção dentro do método.</span><span class="sxs-lookup"><span data-stu-id="71618-111">The Code Editor inserts the appropriate event handler and positions the insertion point within the method.</span></span> <span data-ttu-id="71618-112">No exemplo a seguir, é o <xref:System.Windows.Forms.Control.Click> evento para o <xref:System.Windows.Forms.Button> controle.</span><span class="sxs-lookup"><span data-stu-id="71618-112">In the example below, it is the <xref:System.Windows.Forms.Control.Click> event for the <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5. <span data-ttu-id="71618-113">Acrescente os outros eventos que você deseja que sejam tratados à cláusula `Handles`.</span><span class="sxs-lookup"><span data-stu-id="71618-113">Append the other events you would like handled to the `Handles` clause.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6. <span data-ttu-id="71618-114">Adicione o código apropriado ao manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="71618-114">Add the appropriate code to the event handler.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a><span data-ttu-id="71618-115">Conectar vários eventos a um único manipulador de eventos em C\#</span><span class="sxs-lookup"><span data-stu-id="71618-115">To connect multiple events to a single event handler in C\#</span></span>
  
1. <span data-ttu-id="71618-116">Selecione o controle ao qual você deseja conectar um manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="71618-116">Select the control to which you want to connect an event handler.</span></span>  
  
2. <span data-ttu-id="71618-117">No janela Propriedades, clique no botão **eventos** (![botão eventos](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).</span><span class="sxs-lookup"><span data-stu-id="71618-117">In the Properties window, click the **Events** button (![Events Button](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).</span></span>  
  
3. <span data-ttu-id="71618-118">Clique no nome do evento que você deseja tratar.</span><span class="sxs-lookup"><span data-stu-id="71618-118">Click the name of the event that you want to handle.</span></span>  
  
4. <span data-ttu-id="71618-119">Na seção de valor ao lado do nome do evento, clique no botão da lista suspensa para exibir uma lista de manipuladores de eventos existentes que correspondem à assinatura do método do evento que você deseja tratar.</span><span class="sxs-lookup"><span data-stu-id="71618-119">In the value section next to the event name, click the drop-down button to display a list of existing event handlers that match the method signature of the event you want to handle.</span></span>  
  
5. <span data-ttu-id="71618-120">Selecione o manipulador de eventos apropriado na lista.</span><span class="sxs-lookup"><span data-stu-id="71618-120">Select the appropriate event handler from the list.</span></span>  
  
     <span data-ttu-id="71618-121">O código será adicionado ao formulário para associar o evento ao manipulador de eventos existente.</span><span class="sxs-lookup"><span data-stu-id="71618-121">Code will be added to the form to bind the event to the existing event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71618-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71618-122">See also</span></span>

- [<span data-ttu-id="71618-123">Criando manipuladores de eventos no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="71618-123">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="71618-124">Visão geral de manipuladores de eventos</span><span class="sxs-lookup"><span data-stu-id="71618-124">Event Handlers Overview</span></span>](event-handlers-overview-windows-forms.md)
