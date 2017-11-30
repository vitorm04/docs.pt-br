---
title: Como consumir eventos em um aplicativo Web Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bdb0a6be309f27348ba13bf93fd5aedd3c66a792
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-consume-events-in-a-web-forms-application"></a><span data-ttu-id="2ffcf-102">Como consumir eventos em um aplicativo Web Forms</span><span class="sxs-lookup"><span data-stu-id="2ffcf-102">How to: Consume Events in a Web Forms Application</span></span>
<span data-ttu-id="2ffcf-103">É um cenário comum em aplicativos de Web Forms do ASP.NET preencher uma página da Web com controles e, em seguida, executar uma ação específica com base no controle em que o usuário clica.</span><span class="sxs-lookup"><span data-stu-id="2ffcf-103">A common scenario in ASP.NET Web Forms applications is to populate a webpage with controls, and then perform a specific action based on which control the user clicks.</span></span> <span data-ttu-id="2ffcf-104">Por exemplo, um <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> controle gera um evento quando o usuário clica na página da Web.</span><span class="sxs-lookup"><span data-stu-id="2ffcf-104">For example, a <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> control raises an event when the user clicks it in the webpage.</span></span> <span data-ttu-id="2ffcf-105">Ao manipular o evento, seu aplicativo pode executar a lógica do aplicativo apropriado para esse clique do botão.</span><span class="sxs-lookup"><span data-stu-id="2ffcf-105">By handling the event, your application can perform the appropriate application logic for that button click.</span></span>  
  
### <a name="to-handle-a-button-click-event-on-a-webpage"></a><span data-ttu-id="2ffcf-106">Para tratar um evento de clique de botão em um página da Web</span><span class="sxs-lookup"><span data-stu-id="2ffcf-106">To handle a button click event on a webpage</span></span>  
  
1.  <span data-ttu-id="2ffcf-107">Criar uma página de Web Forms do ASP.NET (página da Web) que tem um <xref:System.Web.UI.WebControls.Button> controlar com o `OnClick` valor definido para o nome do método que você definirá na próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="2ffcf-107">Create a ASP.NET Web Forms page (webpage) that has a <xref:System.Web.UI.WebControls.Button> control with the `OnClick` value set to the name of method that you will define in the next step.</span></span>  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2.  <span data-ttu-id="2ffcf-108">Definir um manipulador de eventos que corresponde a <xref:System.Web.UI.WebControls.Button.Click> assinatura do delegado de evento e que tem o nome que você definiu para o `OnClick` valor.</span><span class="sxs-lookup"><span data-stu-id="2ffcf-108">Define an event handler that matches the <xref:System.Web.UI.WebControls.Button.Click> event delegate signature and that has the name you defined for the `OnClick` value.</span></span>  
  
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
  
     <span data-ttu-id="2ffcf-109">O <xref:System.Web.UI.WebControls.Button.Click> evento usa o <xref:System.EventHandler> classe para o tipo de delegado e o <xref:System.EventArgs> classe para os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="2ffcf-109">The <xref:System.Web.UI.WebControls.Button.Click> event uses the <xref:System.EventHandler> class for the delegate type and the <xref:System.EventArgs> class for the event data.</span></span> <span data-ttu-id="2ffcf-110">A estrutura da página ASP.NET gera automaticamente o código que cria uma instância de <xref:System.EventHandler> e adiciona essa instância para o <xref:System.Web.UI.WebControls.Button.Click> evento o <xref:System.Web.UI.WebControls.Button> instância.</span><span class="sxs-lookup"><span data-stu-id="2ffcf-110">The ASP.NET page framework automatically generates code that creates an instance of <xref:System.EventHandler> and adds this delegate instance to the <xref:System.Web.UI.WebControls.Button.Click> event of the <xref:System.Web.UI.WebControls.Button> instance.</span></span>  
  
3.  <span data-ttu-id="2ffcf-111">No evento método do manipulador que você definiu na etapa 2, adicione código para executar as ações que são necessárias quando o evento ocorre.</span><span class="sxs-lookup"><span data-stu-id="2ffcf-111">In the event handler method that you defined in step 2, add code to perform any actions that are required when the event occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ffcf-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2ffcf-112">See Also</span></span>  
 [<span data-ttu-id="2ffcf-113">Eventos</span><span class="sxs-lookup"><span data-stu-id="2ffcf-113">Events</span></span>](../../../docs/standard/events/index.md)
