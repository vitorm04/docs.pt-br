---
title: Como consumir eventos em um aplicativo Web Forms
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- events [.NET Framework], Web Forms
- Web Forms controls, and events
- event handlers [.NET Framework], Web Forms
- events [.NET Framework], consuming
- Web Forms, event handling
ms.assetid: 73bf8638-c4ec-4069-b0bb-a1dc79b92e32
ms.openlocfilehash: 1f95fd0dcc12f2d4e47ee07e1e6bb15d91000f0f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124779"
---
# <a name="how-to-consume-events-in-a-web-forms-application"></a><span data-ttu-id="51549-102">Como consumir eventos em um aplicativo Web Forms</span><span class="sxs-lookup"><span data-stu-id="51549-102">How to: Consume Events in a Web Forms Application</span></span>
<span data-ttu-id="51549-103">Um cenário comum em aplicativos de Formulários Web do ASP.NET é popular uma página da Web com controles e executar uma ação específica com base no controle em que o usuário clica.</span><span class="sxs-lookup"><span data-stu-id="51549-103">A common scenario in ASP.NET Web Forms applications is to populate a webpage with controls, and then perform a specific action based on which control the user clicks.</span></span> <span data-ttu-id="51549-104">Por exemplo, um controle <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> gera um evento quando o usuário clica na página da Web.</span><span class="sxs-lookup"><span data-stu-id="51549-104">For example, a <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> control raises an event when the user clicks it in the webpage.</span></span> <span data-ttu-id="51549-105">Ao manipular o evento, o aplicativo pode executar a lógica de aplicativo apropriada para esse clique do botão.</span><span class="sxs-lookup"><span data-stu-id="51549-105">By handling the event, your application can perform the appropriate application logic for that button click.</span></span>  
  
### <a name="to-handle-a-button-click-event-on-a-webpage"></a><span data-ttu-id="51549-106">Para tratar um evento de clique de botão em um página da Web</span><span class="sxs-lookup"><span data-stu-id="51549-106">To handle a button click event on a webpage</span></span>  
  
1. <span data-ttu-id="51549-107">Crie uma página de Formulários Web do ASP.NET (página da Web) que tem um controle <xref:System.Web.UI.WebControls.Button> com o valor `OnClick` definido para o nome do método que você definirá na próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="51549-107">Create a ASP.NET Web Forms page (webpage) that has a <xref:System.Web.UI.WebControls.Button> control with the `OnClick` value set to the name of method that you will define in the next step.</span></span>  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2. <span data-ttu-id="51549-108">Defina um manipulador de eventos que corresponda à assinatura de representante de evento <xref:System.Web.UI.WebControls.Button.Click> e que tenha o nome que você definiu para o valor `OnClick`.</span><span class="sxs-lookup"><span data-stu-id="51549-108">Define an event handler that matches the <xref:System.Web.UI.WebControls.Button.Click> event delegate signature and that has the name you defined for the `OnClick` value.</span></span>  
  
    ```csharp  
    protected void Button1_Click(object sender, EventArgs e)  
    {  
        // perform action  
    }  
    ```  
  
    ```vb  
    Protected Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
        ' perform action  
    End Sub  
    ```  
  
     <span data-ttu-id="51549-109">O evento <xref:System.Web.UI.WebControls.Button.Click> usa a classe <xref:System.EventHandler> para o tipo de representante e a classe <xref:System.EventArgs> para os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="51549-109">The <xref:System.Web.UI.WebControls.Button.Click> event uses the <xref:System.EventHandler> class for the delegate type and the <xref:System.EventArgs> class for the event data.</span></span> <span data-ttu-id="51549-110">A estrutura da página ASP.NET gera automaticamente o código que cria uma instância de <xref:System.EventHandler> e adiciona essa instância ao evento <xref:System.Web.UI.WebControls.Button.Click> da instância <xref:System.Web.UI.WebControls.Button>.</span><span class="sxs-lookup"><span data-stu-id="51549-110">The ASP.NET page framework automatically generates code that creates an instance of <xref:System.EventHandler> and adds this delegate instance to the <xref:System.Web.UI.WebControls.Button.Click> event of the <xref:System.Web.UI.WebControls.Button> instance.</span></span>  
  
3. <span data-ttu-id="51549-111">No método do manipulador de eventos que você definiu na etapa 2, adicione código para executar as ações que são necessárias quando o evento ocorre.</span><span class="sxs-lookup"><span data-stu-id="51549-111">In the event handler method that you defined in step 2, add code to perform any actions that are required when the event occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51549-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51549-112">See also</span></span>

- [<span data-ttu-id="51549-113">Eventos</span><span class="sxs-lookup"><span data-stu-id="51549-113">Events</span></span>](../../../docs/standard/events/index.md)
