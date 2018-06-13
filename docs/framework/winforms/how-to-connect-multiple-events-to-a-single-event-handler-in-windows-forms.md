---
title: Como conectar vários eventos a um único manipulador de eventos no Windows Forms
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
ms.openlocfilehash: 527a76376a4c1d5ad051f4768ca2bd42c3548b3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538574"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a><span data-ttu-id="12a53-102">Como conectar vários eventos a um único manipulador de eventos no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="12a53-102">How to: Connect Multiple Events to a Single Event Handler in Windows Forms</span></span>
<span data-ttu-id="12a53-103">No projeto do seu aplicativo, talvez seja necessário usar um único manipulador de eventos para vários eventos ou fazer com que vários eventos executem o mesmo procedimento.</span><span class="sxs-lookup"><span data-stu-id="12a53-103">In your application design, you may find it necessary to use a single event handler for multiple events or have multiple events perform the same procedure.</span></span> <span data-ttu-id="12a53-104">Por exemplo, fazer um comando de menu gerar o mesmo evento que um botão no seu formulário geralmente representará uma grande economia de tempo se eles expuserem a mesma funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="12a53-104">For example, it is often a powerful time-saver to have a menu command raise the same event as a button on your form does if they expose the same functionality.</span></span> <span data-ttu-id="12a53-105">Você pode fazer isso usando a exibição Eventos da janela Propriedades em C# ou usando a palavra-chave `Handles` e as caixas suspensas **Nome de Classe** e **Nome do Método** no Editor de Código do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="12a53-105">You can do this by using the Events view of the Properties window in C# or using the `Handles` keyword and the **Class Name** and **Method Name** drop-down boxes in the Visual Basic Code Editor.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a><span data-ttu-id="12a53-106">Conectar vários eventos a um único manipulador de eventos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="12a53-106">To connect multiple events to a single event handler in Visual Basic</span></span>  
  
1.  <span data-ttu-id="12a53-107">Clique com o botão direito do mouse no formulário e escolha **Exibir Código**.</span><span class="sxs-lookup"><span data-stu-id="12a53-107">Right-click the form and choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="12a53-108">Na caixa suspensa **Nome de Classe**, selecione um dos controles que você deseja que o manipulador de eventos trate.</span><span class="sxs-lookup"><span data-stu-id="12a53-108">From the **Class Name** drop-down box, select one of the controls that you want to have the event handler handle.</span></span>  
  
3.  <span data-ttu-id="12a53-109">Na caixa suspensa **Nome de Método**, selecione um dos eventos que você deseja que o manipulador de eventos trate.</span><span class="sxs-lookup"><span data-stu-id="12a53-109">From the **Method Name** drop-down box, select one of the events that you want the event handler to handle.</span></span>  
  
4.  <span data-ttu-id="12a53-110">O Editor de Código insere o manipulador de eventos apropriado e posiciona o ponto de inserção dentro do método.</span><span class="sxs-lookup"><span data-stu-id="12a53-110">The Code Editor inserts the appropriate event handler and positions the insertion point within the method.</span></span> <span data-ttu-id="12a53-111">No exemplo a seguir, é o <xref:System.Windows.Forms.Control.Click> eventos para o <xref:System.Windows.Forms.Button> controle.</span><span class="sxs-lookup"><span data-stu-id="12a53-111">In the example below, it is the <xref:System.Windows.Forms.Control.Click> event for the <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5.  <span data-ttu-id="12a53-112">Acrescente os outros eventos que você deseja que sejam tratados à cláusula `Handles`.</span><span class="sxs-lookup"><span data-stu-id="12a53-112">Append the other events you would like handled to the `Handles` clause.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6.  <span data-ttu-id="12a53-113">Adicione o código apropriado ao manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="12a53-113">Add the appropriate code to the event handler.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a><span data-ttu-id="12a53-114">Para conectar vários eventos a um manipulador de eventos único em c#</span><span class="sxs-lookup"><span data-stu-id="12a53-114">To connect multiple events to a single event handler in C#</span></span>  
  
1.  <span data-ttu-id="12a53-115">Selecione o controle ao qual você deseja conectar um manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="12a53-115">Select the control to which you want to connect an event handler.</span></span>  
  
2.  <span data-ttu-id="12a53-116">Na janela Propriedades, clique no botão **Eventos** (![Botão Eventos](../../../docs/framework/winforms/media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).</span><span class="sxs-lookup"><span data-stu-id="12a53-116">In the Properties window, click the **Events** button (![Events Button](../../../docs/framework/winforms/media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).</span></span>  
  
3.  <span data-ttu-id="12a53-117">Clique no nome do evento que você deseja tratar.</span><span class="sxs-lookup"><span data-stu-id="12a53-117">Click the name of the event that you want to handle.</span></span>  
  
4.  <span data-ttu-id="12a53-118">Na seção de valor ao lado do nome do evento, clique no botão da lista suspensa para exibir uma lista de manipuladores de eventos existentes que correspondem à assinatura do método do evento que você deseja tratar.</span><span class="sxs-lookup"><span data-stu-id="12a53-118">In the value section next to the event name, click the drop-down button to display a list of existing event handlers that match the method signature of the event you want to handle.</span></span>  
  
5.  <span data-ttu-id="12a53-119">Selecione o manipulador de eventos apropriado na lista.</span><span class="sxs-lookup"><span data-stu-id="12a53-119">Select the appropriate event handler from the list.</span></span>  
  
     <span data-ttu-id="12a53-120">O código será adicionado ao formulário para associar o evento ao manipulador de eventos existente.</span><span class="sxs-lookup"><span data-stu-id="12a53-120">Code will be added to the form to bind the event to the existing event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12a53-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="12a53-121">See Also</span></span>  
 [<span data-ttu-id="12a53-122">Criando manipuladores de eventos no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="12a53-122">Creating Event Handlers in Windows Forms</span></span>](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [<span data-ttu-id="12a53-123">Visão geral de manipuladores de eventos</span><span class="sxs-lookup"><span data-stu-id="12a53-123">Event Handlers Overview</span></span>](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)
