---
title: "Instruções passo a passo: atualizando informações da barra de status em tempo de execução"
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
- status bars [Windows Forms], updating at run time
- status bars [Windows Forms], refreshing panels
- StatusBar control [Windows Forms], refreshing panels
- panels [Windows Forms], refreshing status bar
ms.assetid: cc2abb06-c082-49f7-a5a3-2fd1bbcb58d1
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6c67aa303f375734408201ce15d1c3db3dc32c8e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-updating-status-bar-information-at-run-time"></a>Instruções passo a passo: atualizando informações da barra de status em tempo de execução
> [!IMPORTANT]
>  O <xref:System.Windows.Forms.StatusStrip> e <xref:System.Windows.Forms.ToolStripStatusLabel> controles substituir e adiciona a funcionalidade para o <xref:System.Windows.Forms.StatusBar> e <xref:System.Windows.Forms.StatusBarPanel> controla; no entanto, o <xref:System.Windows.Forms.StatusBar> e <xref:System.Windows.Forms.StatusBarPanel> controles são mantidos para compatibilidade com versões anteriores e o uso futuro, se você Escolha.  
  
 Geralmente, um programa solicitará que você atualize o conteúdo dos painéis da barra de status dinamicamente no tempo de execução, dependendo das alterações de estado do aplicativo ou outra interação do usuário. Essa é uma maneira comum de indicar aos usuários que teclas como CAPS LOCK, NUM LOCK ou SCROLL LOCK estão habilitadas ou de fornecer uma data ou um relógio como uma referência conveniente.  
  
 O exemplo a seguir, você usará uma instância do <xref:System.Windows.Forms.StatusBarPanel> classe para hospedar um relógio.  
  
### <a name="to-get-the-status-bar-ready-for-updating"></a>Preparar a barra de status para atualização  
  
1.  Crie um novo formulário do Windows.  
  
2.  Adicione um controle <xref:System.Windows.Forms.StatusBar> ao seu formulário. Para ver mais detalhes, consulte [Como adicionar controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
3.  Adicionar um painel da barra de status para o <xref:System.Windows.Forms.StatusBar> controle. Para ver mais detalhes, consulte [Como adicionar painéis a um controle StatusBar](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md).  
  
4.  Para o <xref:System.Windows.Forms.StatusBar> controle adicionado ao formulário, defina o <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> propriedade `true`.  
  
5.  Adicione um Windows Forms <xref:System.Windows.Forms.Timer> componente para o formulário.  
  
    > [!NOTE]
    >  Windows Forms <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> componente é criado para um ambiente de Windows Forms. Se você precisar de um temporizador que seja adequado para um ambiente de servidor, consulte [Introdução a temporizadores baseados em servidor](http://msdn.microsoft.com/en-us/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).  
  
6.  Defina a propriedade <xref:System.Windows.Forms.Timer.Enabled%2A> como `true`.  
  
7.  Definir o <xref:System.Windows.Forms.Timer.Interval%2A> propriedade o <xref:System.Windows.Forms.Timer> como 30000.  
  
    > [!NOTE]
    >  O <xref:System.Windows.Forms.Timer.Interval%2A> propriedade o <xref:System.Windows.Forms.Timer> componente é definido como 30 segundos (30.000 milissegundos) para garantir que precisa do tempo é refletida no horário exibido.  
  
### <a name="to-implement-the-timer-to-update-the-status-bar"></a>Implementar o temporizador para atualizar a barra de status  
  
1.  Insira o seguinte código no manipulador de eventos do <xref:System.Windows.Forms.Timer> componente para atualizar o painel do <xref:System.Windows.Forms.StatusBar> controle.  
  
    ```vb  
    Private Sub Timer1_Tick(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Timer1.Tick  
       StatusBar1.Panels(0).Text = Now.ToShortTimeString  
    End Sub  
    ```  
  
    ```csharp  
    private void timer1_Tick(object sender, System.EventArgs e)  
    {  
       statusBar1.Panels[0].Text = DateTime.Now.ToShortTimeString();  
    }  
    ```  
  
    ```cpp  
    private:  
      System::Void timer1_Tick(System::Object ^ sender,  
        System::EventArgs ^ e)  
      {  
        statusBar1->Panels[0]->Text =  
          DateTime::Now.ToShortTimeString();  
      }  
    ```  
  
     Neste ponto, você está pronto para executar o aplicativo e observar o relógio em execução no painel da barra de status.  
  
### <a name="to-test-the-application"></a>Para testar o aplicativo  
  
1.  Depure o aplicativo e pressione F5 para executá-lo. Para ver mais detalhes sobre depuração, consulte [Depuração no Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).  
  
    > [!NOTE]
    >  Levará cerca de 30 segundos para o relógio aparecer na barra de status. Isso serve para obter a hora mais precisa possível. Por outro lado, para fazer com que o relógio apareça antes, você pode reduzir o valor de <xref:System.Windows.Forms.Timer.Interval%2A> propriedade definida na etapa 7 no procedimento anterior.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [Como adicionar painéis a um controle StatusBar](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md)  
 [Como determinar qual painel no controle StatusBar dos Windows Forms foi clicado](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)  
 [Visão geral do controle StatusBar](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)
