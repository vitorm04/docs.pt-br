---
title: 'Passo a passo: Atualizando informações da barra de status em tempo de execução'
ms.date: 03/30/2017
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
ms.openlocfilehash: 670746a1b964a85bc5136d976d831c6848466797
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930981"
---
# <a name="walkthrough-updating-status-bar-information-at-run-time"></a>Passo a passo: Atualizando informações da barra de status em tempo de execução
> [!IMPORTANT]
> Os <xref:System.Windows.Forms.StatusStrip> controles <xref:System.Windows.Forms.ToolStripStatusLabel> e <xref:System.Windows.Forms.StatusBar> substituem e adicionam funcionalidade aos <xref:System.Windows.Forms.StatusBarPanel> controles e; no entanto <xref:System.Windows.Forms.StatusBarPanel> , os <xref:System.Windows.Forms.StatusBar> controles e são mantidos para compatibilidade com versões anteriores e uso futuro, se você escolha.  
  
 Geralmente, um programa solicitará que você atualize o conteúdo dos painéis da barra de status dinamicamente no tempo de execução, dependendo das alterações de estado do aplicativo ou outra interação do usuário. Essa é uma maneira comum de indicar aos usuários que teclas como CAPS LOCK, NUM LOCK ou SCROLL LOCK estão habilitadas ou de fornecer uma data ou um relógio como uma referência conveniente.  
  
 No exemplo a seguir, você usará uma instância da <xref:System.Windows.Forms.StatusBarPanel> classe para hospedar um relógio.  
  
### <a name="to-get-the-status-bar-ready-for-updating"></a>Preparar a barra de status para atualização  
  
1. Crie um novo formulário do Windows.  
  
2. Adicione um controle <xref:System.Windows.Forms.StatusBar> ao seu formulário. Para obter detalhes, confira [Como: Adicione controles a Windows Forms](how-to-add-controls-to-windows-forms.md).  
  
3. Adicione um painel da barra de status <xref:System.Windows.Forms.StatusBar> ao seu controle. Para obter detalhes, confira [Como: Adicione painéis a um controle](how-to-add-panels-to-a-statusbar-control.md)StatusBar.  
  
4. Para o <xref:System.Windows.Forms.StatusBar> controle adicionado ao formulário, defina a <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> Propriedade como `true`.  
  
5. Adicione um componente <xref:System.Windows.Forms.Timer> Windows Forms ao formulário.  
  
    > [!NOTE]
    > O componente <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> Windows Forms é projetado para um ambiente de Windows Forms. Se você precisar de um temporizador que seja adequado para um ambiente de servidor, consulte [Introdução a temporizadores baseados em servidor](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).  
  
6. Defina a propriedade <xref:System.Windows.Forms.Timer.Enabled%2A> como `true`.  
  
7. Defina a <xref:System.Windows.Forms.Timer.Interval%2A> propriedade <xref:System.Windows.Forms.Timer> de como 30000.  
  
    > [!NOTE]
    > A <xref:System.Windows.Forms.Timer.Interval%2A> propriedade<xref:System.Windows.Forms.Timer> do componente é definida como 30 segundos (30.000 milissegundos) para garantir que um tempo preciso seja refletido no tempo exibido.  
  
### <a name="to-implement-the-timer-to-update-the-status-bar"></a>Implementar o temporizador para atualizar a barra de status  
  
1. Insira o código a seguir no manipulador de eventos do <xref:System.Windows.Forms.Timer> componente para atualizar o painel <xref:System.Windows.Forms.StatusBar> do controle.  
  
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
  
1. Depure o aplicativo e pressione F5 para executá-lo. Para ver mais detalhes sobre depuração, consulte [Depuração no Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).  
  
    > [!NOTE]
    > Levará cerca de 30 segundos para o relógio aparecer na barra de status. Isso serve para obter a hora mais precisa possível. Por outro lado, para que o relógio apareça mais cedo, você pode reduzir o valor da <xref:System.Windows.Forms.Timer.Interval%2A> propriedade definida na etapa 7 no procedimento anterior.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Como: Adicionar painéis a um controle StatusBar](how-to-add-panels-to-a-statusbar-control.md)
- [Como: Determine em qual painel no controle StatusBar Windows Forms foi clicado](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [Visão geral do controle StatusBar](statusbar-control-overview-windows-forms.md)
