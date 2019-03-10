---
title: 'Como: Responder a cliques de botão do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], responding to Click events
- events [Windows Forms], Click events
- Click event [Windows Forms], Button control
- MouseDown event
- Button control [Windows Forms], click response
- double-clicks
- examples [Windows Forms], controls
- Click event [Windows Forms], responding to
ms.assetid: 7a4951bd-369c-4662-b246-28ad83eda484
ms.openlocfilehash: e6e6d041422a79171ec4b6159f0789b8aa6a50d5
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724980"
---
# <a name="how-to-respond-to-windows-forms-button-clicks"></a><span data-ttu-id="78fb4-102">Como: Responder a cliques de botão do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="78fb4-102">How to: Respond to Windows Forms Button Clicks</span></span>
<span data-ttu-id="78fb4-103">O uso mais básico de um Windows Forms <xref:System.Windows.Forms.Button> controle é executar algum código quando o botão é clicado.</span><span class="sxs-lookup"><span data-stu-id="78fb4-103">The most basic use of a Windows Forms <xref:System.Windows.Forms.Button> control is to run some code when the button is clicked.</span></span>  
  
 <span data-ttu-id="78fb4-104">Clicar em um <xref:System.Windows.Forms.Button> controle também gera um número de outros eventos, como o <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>, e <xref:System.Windows.Forms.Control.MouseUp> eventos.</span><span class="sxs-lookup"><span data-stu-id="78fb4-104">Clicking a <xref:System.Windows.Forms.Button> control also generates a number of other events, such as the <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>, and <xref:System.Windows.Forms.Control.MouseUp> events.</span></span> <span data-ttu-id="78fb4-105">Se você pretende anexar manipuladores de eventos para esses eventos relacionados, verifique se suas ações não entrem em conflito.</span><span class="sxs-lookup"><span data-stu-id="78fb4-105">If you intend to attach event handlers for these related events, be sure that their actions do not conflict.</span></span> <span data-ttu-id="78fb4-106">Por exemplo, se clicar no botão limpa as informações que o usuário digitou na caixa de texto, pausar o ponteiro do mouse sobre o botão não deverá exibir uma dica de ferramenta com essas informações agora inexistentes.</span><span class="sxs-lookup"><span data-stu-id="78fb4-106">For example, if clicking the button clears information that the user has typed in a text box, pausing the mouse pointer over the button should not display a tool tip with that now-nonexistent information.</span></span>  
  
 <span data-ttu-id="78fb4-107">Se o usuário tentar clicar duas vezes o <xref:System.Windows.Forms.Button> controle, cada clique será processado separadamente; ou seja, o controle não dá suporte para o evento de clique duplo.</span><span class="sxs-lookup"><span data-stu-id="78fb4-107">If the user attempts to double-click the <xref:System.Windows.Forms.Button> control, each click will be processed separately; that is, the control does not support the double-click event.</span></span>  
  
### <a name="to-respond-to-a-button-click"></a><span data-ttu-id="78fb4-108">Para responder a um clique de botão</span><span class="sxs-lookup"><span data-stu-id="78fb4-108">To respond to a button click</span></span>  
  
-   <span data-ttu-id="78fb4-109">O botão `Click` <xref:System.EventHandler> escrever o código seja executado.</span><span class="sxs-lookup"><span data-stu-id="78fb4-109">In the button's `Click` <xref:System.EventHandler> write the code to run.</span></span> <span data-ttu-id="78fb4-110">`Button1_Click` deve ser associado ao controle.</span><span class="sxs-lookup"><span data-stu-id="78fb4-110">`Button1_Click` must be bound to the control.</span></span> <span data-ttu-id="78fb4-111">Para obter mais informações, confira [Como: Criar manipuladores de eventos em tempo de execução para formulários do Windows](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="78fb4-111">For more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       MessageBox.Show("Button1 was clicked")  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       MessageBox.Show("button1 was clicked");  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          MessageBox::Show("button1 was clicked");  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="78fb4-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="78fb4-112">See also</span></span>
- [<span data-ttu-id="78fb4-113">Visão geral do controle de botão</span><span class="sxs-lookup"><span data-stu-id="78fb4-113">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="78fb4-114">Formas de selecionar um controle de botão dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="78fb4-114">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="78fb4-115">Controle de botão</span><span class="sxs-lookup"><span data-stu-id="78fb4-115">Button Control</span></span>](button-control-windows-forms.md)
