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
ms.openlocfilehash: 1c28f8eaba5c35f762d6fc57ebbddbbb71769c81
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972309"
---
# <a name="how-to-determine-which-panel-in-the-windows-forms-statusbar-control-was-clicked"></a>Como: Determinar qual painel no controle StatusBar do Windows Forms foi clicado
> [!IMPORTANT]
>  O <xref:System.Windows.Forms.StatusStrip> e <xref:System.Windows.Forms.ToolStripStatusLabel> controles substituam e adicionem funcionalidade para o <xref:System.Windows.Forms.StatusBar> e <xref:System.Windows.Forms.StatusBarPanel> controla; no entanto, o <xref:System.Windows.Forms.StatusBar> e <xref:System.Windows.Forms.StatusBarPanel> controles sejam mantidos para compatibilidade com versões anteriores e uso futuro, se você Escolha.  
  
 Para o programa a [controle StatusBar](statusbar-control-windows-forms.md) controle para responder a cliques do usuário, use uma instrução case dentro a <xref:System.Windows.Forms.StatusBar.PanelClick> eventos. O evento contém um argumento (o argumento do painel), que contém uma referência para o clicado <xref:System.Windows.Forms.StatusBarPanel>. Usando essa referência, determine o índice do painel clicado e programe adequadamente.  
  
> [!NOTE]
>  Certifique-se de que o <xref:System.Windows.Forms.StatusBar> do controle <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> estiver definida como `true`.  
  
### <a name="to-determine-which-panel-was-clicked"></a>Para determinar qual painel foi clicado  
  
1. No <xref:System.Windows.Forms.StatusBar.PanelClick> manipulador de eventos, use uma `Select Case` (no Visual Basic) ou `switch case` (Visual C# ou [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) instrução para determinar qual painel foi clicado examinando o índice do painel clicado nos argumentos do evento.  
  
     O exemplo de código a seguir exige a presença, no formulário, de um <xref:System.Windows.Forms.StatusBar> controle, `StatusBar1`e dois <xref:System.Windows.Forms.StatusBarPanel> objetos `StatusBarPanel1` e `StatusBarPanel2`.  
  
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
  
     (Visual c#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.  
  
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
- [Como: Definir o tamanho de painéis da barra de Status](how-to-set-the-size-of-status-bar-panels.md)
- [Passo a passo: Atualizando informações da barra de Status em tempo de execução](walkthrough-updating-status-bar-information-at-run-time.md)
- [Visão geral do controle StatusBar](statusbar-control-overview-windows-forms.md)
