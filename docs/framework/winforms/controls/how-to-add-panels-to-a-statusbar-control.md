---
title: Como adicionar painéis a um controle StatusBar
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- panels [Windows Forms], status bars
- status bars [Windows Forms], adding panels
- StatusBar control [Windows Forms], adding panels
ms.assetid: 835e3902-288c-4c38-9d69-0696d8695009
ms.openlocfilehash: 386c8cae425c458ddf4c446a454ae4213761e651
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142193"
---
# <a name="how-to-add-panels-to-a-statusbar-control"></a>Como adicionar painéis a um controle StatusBar
> [!IMPORTANT]
> Os <xref:System.Windows.Forms.StatusStrip> <xref:System.Windows.Forms.ToolStripStatusLabel> controles e controles substituem <xref:System.Windows.Forms.StatusBar> e <xref:System.Windows.Forms.StatusBarPanel> adicionam funcionalidade aos controles; no entanto, os <xref:System.Windows.Forms.StatusBar> controles e controles <xref:System.Windows.Forms.StatusBarPanel> são retidos tanto para compatibilidade retrógrada quanto para uso futuro, se você escolher.  
  
 A área programável dentro de um controle de <xref:System.Windows.Forms.StatusBarPanel> controle de [statusbar](statusbar-control-windows-forms.md) consiste em instâncias da classe. Estes são adicionados <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> através de adições à classe.  
  
### <a name="to-add-panels-to-a-status-bar"></a>Para adicionar painéis a uma barra de status  
  
1. Em um procedimento, crie painéis de <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>barras de status adicionando-os ao . Especifique as configurações de propriedade <xref:System.Windows.Forms.StatusBar.Panels%2A> para painéis individuais usando seu índice passado pela propriedade.  
  
     No exemplo de código a seguir, o caminho definido para o local do ícone é a pasta **Meus Documentos**. Esse local é usado porque você pode supor que a maioria dos computadores que executam o sistema operacional Windows incluem essa pasta. Escolher esse local também permite que os usuários com níveis mínimos de acesso ao sistema executem com mais segurança o aplicativo. O exemplo a seguir <xref:System.Windows.Forms.StatusBar> requer um formulário com um controle já adicionado.  
  
    > [!NOTE]
    > A <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> coleção é baseada em zero, então o código deve proceder em conformidade.  
  
    ```vb  
    Public Sub CreateStatusBarPanels()  
    ' Create panels and set text property.  
       StatusBar1.Panels.Add("One")  
       StatusBar1.Panels.Add("Two")  
       StatusBar1.Panels.Add("Three")  
    ' Set properties of StatusBar panels.  
    ' Set AutoSize property of panels.  
       StatusBar1.Panels(0).AutoSize = StatusBarPanelAutoSize.Spring  
       StatusBar1.Panels(1).AutoSize = StatusBarPanelAutoSize.Contents  
       StatusBar1.Panels(2).AutoSize = StatusBarPanelAutoSize.Contents  
    ' Set BorderStyle property of panels.  
       StatusBar1.Panels(0).BorderStyle = StatusBarPanelBorderStyle.Raised  
       StatusBar1.Panels(1).BorderStyle = StatusBarPanelBorderStyle.Sunken  
       StatusBar1.Panels(2).BorderStyle = StatusBarPanelBorderStyle.Raised  
    ' Set Icon property of third panel. You should replace the bolded  
    ' icon in the sample below with an icon of your own choosing.  
       StatusBar1.Panels(2).Icon = New _
       System.Drawing.Icon(System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Icon.ico")  
       StatusBar1.ShowPanels = True  
    End Sub  
    ```  
  
    ```csharp  
    public void CreateStatusBarPanels()  
    {  
       // Create panels and set text property.  
       statusBar1.Panels.Add("One");  
       statusBar1.Panels.Add("Two");  
       statusBar1.Panels.Add("Three");  
       // Set properties of StatusBar panels.  
       // Set AutoSize property of panels.  
       statusBar1.Panels[0].AutoSize = StatusBarPanelAutoSize.Spring;  
       statusBar1.Panels[1].AutoSize = StatusBarPanelAutoSize.Contents;  
       statusBar1.Panels[2].AutoSize = StatusBarPanelAutoSize.Contents;  
       // Set BorderStyle property of panels.  
       statusBar1.Panels[0].BorderStyle =  
          StatusBarPanelBorderStyle.Raised;  
       statusBar1.Panels[1].BorderStyle = StatusBarPanelBorderStyle.Sunken;  
       statusBar1.Panels[2].BorderStyle = StatusBarPanelBorderStyle.Raised;  
       // Set Icon property of third panel. You should replace the bolded  
       // icon in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       statusBar1.Panels[2].Icon =
          new System.Drawing.Icon (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       + @"\Icon.ico");  
       statusBar1.ShowPanels = true;  
    }  
    ```  
  
    ```cpp  
    public:  
       void CreateStatusBarPanels()  
       {  
          // Create panels and set text property.  
          statusBar1->Panels->Add("One");  
          statusBar1->Panels->Add("Two");  
          statusBar1->Panels->Add("Three");  
          // Set properties of StatusBar panels.  
          // Set AutoSize property of panels.  
          statusBar1->Panels[0]->AutoSize =  
             StatusBarPanelAutoSize::Spring;  
          statusBar1->Panels[1]->AutoSize =  
             StatusBarPanelAutoSize::Contents;  
          statusBar1->Panels[2]->AutoSize =  
             StatusBarPanelAutoSize::Contents;  
          // Set BorderStyle property of panels.  
          statusBar1->Panels[0]->BorderStyle =  
             StatusBarPanelBorderStyle::Raised;  
          statusBar1->Panels[1]->BorderStyle =  
             StatusBarPanelBorderStyle::Sunken;  
          statusBar1->Panels[2]->BorderStyle =  
             StatusBarPanelBorderStyle::Raised;  
          // Set Icon property of third panel.  
          // You should replace the bolded image
          // in the sample below with an icon of your own choosing.  
          statusBar1->Panels[2]->Icon =  
             gcnew System::Drawing::Icon(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Icon.ico"));  
          statusBar1->ShowPanels = true;  
       }  
    ```  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Caixa de diálogo Editor de Coleção](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/xc4yyekt(v=vs.100))
- [Como definir o tamanho de painéis da barra de status](how-to-set-the-size-of-status-bar-panels.md)
- [Instruções passo a passo: atualizando informações da barra de status em tempo de execução](walkthrough-updating-status-bar-information-at-run-time.md)
- [Como determinar qual painel no controle StatusBar do Windows Forms foi clicado](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [Visão geral do controle StatusBar](statusbar-control-overview-windows-forms.md)
