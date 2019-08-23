---
title: 'Como: Determinar qual painel no controle StatusBar do Windows Forms foi clicado'
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
ms.openlocfilehash: 6229d8965949641105cd0e9708474c3249d52d1d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965716"
---
# <a name="how-to-determine-which-panel-in-the-windows-forms-statusbar-control-was-clicked"></a>Como: Determinar qual painel no controle StatusBar do Windows Forms foi clicado
> [!IMPORTANT]
> Os <xref:System.Windows.Forms.StatusStrip> controles <xref:System.Windows.Forms.ToolStripStatusLabel> e <xref:System.Windows.Forms.StatusBar> substituem e adicionam funcionalidade aos <xref:System.Windows.Forms.StatusBarPanel> controles e; no entanto <xref:System.Windows.Forms.StatusBarPanel> , os <xref:System.Windows.Forms.StatusBar> controles e são mantidos para compatibilidade com versões anteriores e uso futuro, se você escolha.  
  
 Para programar o controle [StatusBar](statusbar-control-windows-forms.md) Control para responder aos cliques do usuário, use uma instrução Case <xref:System.Windows.Forms.StatusBar.PanelClick> dentro do evento. O evento contém um argumento (o argumento de painel), que contém uma referência para o <xref:System.Windows.Forms.StatusBarPanel>clicado. Usando essa referência, determine o índice do painel clicado e programe adequadamente.  
  
> [!NOTE]
> Verifique se a <xref:System.Windows.Forms.StatusBar> Propriedade do <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> controle está definida como `true`.  
  
### <a name="to-determine-which-panel-was-clicked"></a>Para determinar qual painel foi clicado  
  
1. `switch case` `Select Case` C# C++No manipulador de eventos,useumainstrução(naVisualBasic)ou(VisualouVisual)paradeterminarqualpainelfoiclicadoexaminandooíndicedopainelclicadonosargumentosdoevento.<xref:System.Windows.Forms.StatusBar.PanelClick>  
  
     O exemplo de código a seguir requer a presença, no formulário, de <xref:System.Windows.Forms.StatusBar> um controle `StatusBar1`, e dois <xref:System.Windows.Forms.StatusBarPanel> objetos, `StatusBarPanel1` e `StatusBarPanel2`.  
  
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
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Como: Definir o tamanho dos painéis da barra de status](how-to-set-the-size-of-status-bar-panels.md)
- [Passo a passo: Atualizando informações da barra de status em tempo de execução](walkthrough-updating-status-bar-information-at-run-time.md)
- [Visão geral do controle StatusBar](statusbar-control-overview-windows-forms.md)
