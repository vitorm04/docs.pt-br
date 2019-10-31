---
title: 'Instruções passo a passo: atualizando informações da barra de status em tempo de execução'
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
ms.openlocfilehash: f1d22079dfa3a6452efb74ef57530bb43e059a4a
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197107"
---
# <a name="walkthrough-updating-status-bar-information-at-run-time"></a>Instruções passo a passo: atualizando informações da barra de status em tempo de execução
> [!IMPORTANT]
> Os controles <xref:System.Windows.Forms.StatusStrip> e <xref:System.Windows.Forms.ToolStripStatusLabel> substituem e adicionam funcionalidade aos controles <xref:System.Windows.Forms.StatusBar> e <xref:System.Windows.Forms.StatusBarPanel>; no entanto, os controles <xref:System.Windows.Forms.StatusBar> e <xref:System.Windows.Forms.StatusBarPanel> são mantidos para compatibilidade com versões anteriores e uso futuro, se você escolher.  
  
 Geralmente, um programa solicitará que você atualize o conteúdo dos painéis da barra de status dinamicamente no tempo de execução, dependendo das alterações de estado do aplicativo ou outra interação do usuário. Essa é uma maneira comum de indicar aos usuários que teclas como CAPS LOCK, NUM LOCK ou SCROLL LOCK estão habilitadas ou de fornecer uma data ou um relógio como uma referência conveniente.  
  
 No exemplo a seguir, você usará uma instância da classe <xref:System.Windows.Forms.StatusBarPanel> para hospedar um relógio.  
  
### <a name="to-get-the-status-bar-ready-for-updating"></a>Preparar a barra de status para atualização  
  
1. Crie um novo formulário do Windows.  
  
2. Adicione um controle <xref:System.Windows.Forms.StatusBar> ao seu formulário. Para ver mais detalhes, consulte [Como adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md).  
  
3. Adicione um painel de barras de status ao controle de <xref:System.Windows.Forms.StatusBar>. Para ver mais detalhes, consulte [Como adicionar painéis a um controle StatusBar](how-to-add-panels-to-a-statusbar-control.md).  
  
4. Para o controle de <xref:System.Windows.Forms.StatusBar> adicionado ao formulário, defina a propriedade <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> como `true`.  
  
5. Adicione um Windows Forms <xref:System.Windows.Forms.Timer> componente ao formulário.  
  
    > [!NOTE]
    > O componente Windows Forms <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> foi projetado para um ambiente Windows Forms. Se você precisar de um temporizador que seja adequado para um ambiente de servidor, consulte [Introdução a temporizadores baseados em servidor](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).  
  
6. Defina a propriedade <xref:System.Windows.Forms.Timer.Enabled%2A> como `true`.  
  
7. Defina a propriedade <xref:System.Windows.Forms.Timer.Interval%2A> do <xref:System.Windows.Forms.Timer> como 30000.  
  
    > [!NOTE]
    > A propriedade <xref:System.Windows.Forms.Timer.Interval%2A> do componente <xref:System.Windows.Forms.Timer> é definida como 30 segundos (30.000 milissegundos) para garantir que um tempo preciso seja refletido no tempo exibido.  
  
### <a name="to-implement-the-timer-to-update-the-status-bar"></a>Implementar o temporizador para atualizar a barra de status  
  
1. Insira o código a seguir no manipulador de eventos do componente <xref:System.Windows.Forms.Timer> para atualizar o painel do controle de <xref:System.Windows.Forms.StatusBar>.  
  
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
  
1. Depure o aplicativo e pressione F5 para executá-lo. Para ver mais detalhes sobre depuração, consulte [Depuração no Visual Studio](/visualstudio/debugger/debugger-feature-tour).  
  
    > [!NOTE]
    > Levará cerca de 30 segundos para o relógio aparecer na barra de status. Isso serve para obter a hora mais precisa possível. Por outro lado, para que o relógio pareça mais cedo, você pode reduzir o valor da propriedade <xref:System.Windows.Forms.Timer.Interval%2A> definida na etapa 7 no procedimento anterior.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Como adicionar painéis a um controle StatusBar](how-to-add-panels-to-a-statusbar-control.md)
- [Como determinar qual painel no controle StatusBar dos Windows Forms foi clicado](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [Visão geral do controle StatusBar](statusbar-control-overview-windows-forms.md)
