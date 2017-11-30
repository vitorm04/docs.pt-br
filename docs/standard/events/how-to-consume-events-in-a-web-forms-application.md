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
# <a name="how-to-consume-events-in-a-web-forms-application"></a>Como consumir eventos em um aplicativo Web Forms
É um cenário comum em aplicativos de Web Forms do ASP.NET preencher uma página da Web com controles e, em seguida, executar uma ação específica com base no controle em que o usuário clica. Por exemplo, um <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> controle gera um evento quando o usuário clica na página da Web. Ao manipular o evento, seu aplicativo pode executar a lógica do aplicativo apropriado para esse clique do botão.  
  
### <a name="to-handle-a-button-click-event-on-a-webpage"></a>Para tratar um evento de clique de botão em um página da Web  
  
1.  Criar uma página de Web Forms do ASP.NET (página da Web) que tem um <xref:System.Web.UI.WebControls.Button> controlar com o `OnClick` valor definido para o nome do método que você definirá na próxima etapa.  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2.  Definir um manipulador de eventos que corresponde a <xref:System.Web.UI.WebControls.Button.Click> assinatura do delegado de evento e que tem o nome que você definiu para o `OnClick` valor.  
  
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
  
     O <xref:System.Web.UI.WebControls.Button.Click> evento usa o <xref:System.EventHandler> classe para o tipo de delegado e o <xref:System.EventArgs> classe para os dados do evento. A estrutura da página ASP.NET gera automaticamente o código que cria uma instância de <xref:System.EventHandler> e adiciona essa instância para o <xref:System.Web.UI.WebControls.Button.Click> evento o <xref:System.Web.UI.WebControls.Button> instância.  
  
3.  No evento método do manipulador que você definiu na etapa 2, adicione código para executar as ações que são necessárias quando o evento ocorre.  
  
## <a name="see-also"></a>Consulte também  
 [Eventos](../../../docs/standard/events/index.md)
