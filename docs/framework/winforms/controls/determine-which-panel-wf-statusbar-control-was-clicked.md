---
title: Determine qual painel no controle da barra de status foi clicado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- status bars [Windows Forms], determining panel clicked
- panels [Windows Forms], determining clicked
- StatusBar control [Windows Forms], coding panel click events
- StatusBar control [Windows Forms], determining panel clicked
- PanelClick event [Windows Forms], determining panel clicked
- Panel control [Windows Forms], determining click
ms.assetid: d14c6092-04b2-4a07-8ddf-0dd11277ff5f
ms.openlocfilehash: eb3b10d515ba5b62236594e063ca7f060b34b73e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182357"
---
# <a name="how-to-determine-which-panel-in-the-windows-forms-statusbar-control-was-clicked"></a>Como determinar qual painel no controle StatusBar dos Windows Forms foi clicado
> [!IMPORTANT]
> Os <xref:System.Windows.Forms.StatusStrip> <xref:System.Windows.Forms.ToolStripStatusLabel> controles e controles substituem <xref:System.Windows.Forms.StatusBar> e <xref:System.Windows.Forms.StatusBarPanel> adicionam funcionalidade aos controles; no entanto, os <xref:System.Windows.Forms.StatusBar> controles e controles <xref:System.Windows.Forms.StatusBarPanel> são retidos tanto para compatibilidade retrógrada quanto para uso futuro, se você escolher.  
  
 Para programar o controle [statusbar](statusbar-control-windows-forms.md) para responder aos cliques <xref:System.Windows.Forms.StatusBar.PanelClick> do usuário, use uma declaração de caso dentro do evento. O evento contém um argumento (o argumento do painel), que contém uma referência ao clicado <xref:System.Windows.Forms.StatusBarPanel>. Usando essa referência, determine o índice do painel clicado e programe adequadamente.  
  
> [!NOTE]
> Certifique-se <xref:System.Windows.Forms.StatusBar> de <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> que a `true`propriedade do controle está definida como .  
  
### <a name="to-determine-which-panel-was-clicked"></a>Para determinar qual painel foi clicado  
  
1. No <xref:System.Windows.Forms.StatusBar.PanelClick> manipulador de eventos, use uma `Select Case` `switch case` declaração (visual básica) ou (Visual C# ou Visual C++) para determinar qual painel foi clicado examinando o índice do painel clicado nos argumentos do evento.  
  
     O exemplo de código a seguir requer <xref:System.Windows.Forms.StatusBar> a `StatusBar1`presença, <xref:System.Windows.Forms.StatusBarPanel> na `StatusBarPanel1` forma, de um controle, e dois objetos, e `StatusBarPanel2`.  
  
    ```vb  
    Private Sub StatusBar1_PanelClick(ByVal sender As System.Object, ByVal e As System.Windows.Forms.StatusBarPanelClickEventArgs) Handles StatusBar1.PanelClick  
       Select Case StatusBar1.Panels.IndexOf(e.StatusBarPanel)  
         Case 0  
           MessageBox.Show("You have clicked Panel One.")  
         Case 1  
           MessageBox.Show("You have clicked Panel Two.")  
       End Select  
    End Sub  
    ```  
  
    ```csharp  
    private void statusBar1_PanelClick(object sender,
    System.Windows.Forms.StatusBarPanelClickEventArgs e)  
    {  
       switch (statusBar1.Panels.IndexOf(e.StatusBarPanel))  
       {  
          case 0 :  
             MessageBox.Show("You have clicked Panel One.");  
             break;  
          case 1 :  
             MessageBox.Show("You have clicked Panel Two.");  
             break;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void statusBar1_PanelClick(System::Object ^  sender,  
          System::Windows::Forms::StatusBarPanelClickEventArgs ^  e)  
       {  
          switch (statusBar1->Panels->IndexOf(e->StatusBarPanel))  
          {  
             case 0 :  
                MessageBox::Show("You have clicked Panel One.");  
                break;  
             case 1 :  
                MessageBox::Show("You have clicked Panel Two.");  
                break;  
          }  
       }  
    ```  
  
     (Visual C#, Visual C++) Coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.  
  
    ```csharp  
    this.statusBar1.PanelClick += new
       System.Windows.Forms.StatusBarPanelClickEventHandler
       (this.statusBar1_PanelClick);  
    ```  
  
    ```cpp  
    this->statusBar1->PanelClick += gcnew  
       System::Windows::Forms::StatusBarPanelClickEventHandler  
       (this, &Form1::statusBar1_PanelClick);  
    ```  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Como definir o tamanho de painéis da barra de status](how-to-set-the-size-of-status-bar-panels.md)
- [Instruções passo a passo: atualizando informações da barra de status em tempo de execução](walkthrough-updating-status-bar-information-at-run-time.md)
- [Visão geral do controle StatusBar](statusbar-control-overview-windows-forms.md)
