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
# <a name="how-to-respond-to-windows-forms-button-clicks"></a>Como: Responder a cliques de botão do Windows Forms
O uso mais básico de um Windows Forms <xref:System.Windows.Forms.Button> controle é executar algum código quando o botão é clicado.  
  
 Clicar em um <xref:System.Windows.Forms.Button> controle também gera um número de outros eventos, como o <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>, e <xref:System.Windows.Forms.Control.MouseUp> eventos. Se você pretende anexar manipuladores de eventos para esses eventos relacionados, verifique se suas ações não entrem em conflito. Por exemplo, se clicar no botão limpa as informações que o usuário digitou na caixa de texto, pausar o ponteiro do mouse sobre o botão não deverá exibir uma dica de ferramenta com essas informações agora inexistentes.  
  
 Se o usuário tentar clicar duas vezes o <xref:System.Windows.Forms.Button> controle, cada clique será processado separadamente; ou seja, o controle não dá suporte para o evento de clique duplo.  
  
### <a name="to-respond-to-a-button-click"></a>Para responder a um clique de botão  
  
-   O botão `Click` <xref:System.EventHandler> escrever o código seja executado. `Button1_Click` deve ser associado ao controle. Para obter mais informações, confira [Como: Criar manipuladores de eventos em tempo de execução para formulários do Windows](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
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
- [Visão geral do controle de botão](button-control-overview-windows-forms.md)
- [Formas de selecionar um controle de botão dos Windows Forms](ways-to-select-a-windows-forms-button-control.md)
- [Controle de botão](button-control-windows-forms.md)
