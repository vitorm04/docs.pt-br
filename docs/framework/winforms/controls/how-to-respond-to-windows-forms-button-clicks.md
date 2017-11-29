---
title: "Como responder a cliques no botão dos Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 923eb7d1b1b5b442ce897619253a958019b239a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-respond-to-windows-forms-button-clicks"></a>Como responder a cliques no botão dos Windows Forms
O uso mais básico de um Windows Forms <xref:System.Windows.Forms.Button> controle é executar um código quando o botão é clicado.  
  
 Clicar em um <xref:System.Windows.Forms.Button> controle também gera um número de outros eventos, como o <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>, e <xref:System.Windows.Forms.Control.MouseUp> eventos. Se você pretende anexar manipuladores de eventos para esses eventos relacionados, verifique se suas ações não entrem em conflito. Por exemplo, se clicar no botão limpa as informações que o usuário digitou na caixa de texto, pausar o ponteiro do mouse sobre o botão não deverá exibir uma dica de ferramenta com essas informações agora inexistentes.  
  
 Se o usuário tenta clique duas vezes o <xref:System.Windows.Forms.Button> controle, cada clique será processada separadamente; ou seja, o controle não oferece suporte para o evento de clique duplo.  
  
### <a name="to-respond-to-a-button-click"></a>Para responder a um clique de botão  
  
-   O botão `Click` <xref:System.EventHandler> escrever o código para ser executado. `Button1_Click` deve ser associado ao controle. Para saber mais, veja [Como criar manipuladores de eventos em tempo de execução para formulários dos Windows Forms](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
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
  
## <a name="see-also"></a>Consulte também  
 [Visão geral do controle de botão](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [Formas de selecionar um controle de botão dos Windows Forms](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [Controle de botão](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
