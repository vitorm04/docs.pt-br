---
title: 'Como: Definir o tamanho de painéis da barra de status'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- StatusBar control [Windows Forms], panel size
- status bars [Windows Forms], setting panel size
- panels [Windows Forms], setting size in status bars
ms.assetid: a01bee43-d9eb-4954-84e6-45a93532d08d
ms.openlocfilehash: 4ba0f7f02b548a5d9ea1a99605a668f449b3e4a9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923620"
---
# <a name="how-to-set-the-size-of-status-bar-panels"></a><span data-ttu-id="49dfb-102">Como: Definir o tamanho de painéis da barra de status</span><span class="sxs-lookup"><span data-stu-id="49dfb-102">How to: Set the Size of Status-Bar Panels</span></span>
> [!NOTE]
> <span data-ttu-id="49dfb-103">O controle <xref:System.Windows.Forms.ToolStripStatusLabel> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.StatusBar>, no entanto, o controle <xref:System.Windows.Forms.StatusBar> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.</span><span class="sxs-lookup"><span data-stu-id="49dfb-103">The <xref:System.Windows.Forms.ToolStripStatusLabel> control replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control; however, the <xref:System.Windows.Forms.StatusBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="49dfb-104">Cada instância da <xref:System.Windows.Forms.StatusBarPanel> classe dentro de um controle [StatusBar](statusbar-control-windows-forms.md) tem um número de propriedades dinâmicas que determinam seu comportamento de largura e redimensionamento em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="49dfb-104">Each instance of the <xref:System.Windows.Forms.StatusBarPanel> class within a [StatusBar Control](statusbar-control-windows-forms.md) control has a number of dynamic properties that determine its width and resize behavior at run time.</span></span>  
  
### <a name="to-set-the-size-of-a-panel"></a><span data-ttu-id="49dfb-105">Para definir o tamanho de um painel</span><span class="sxs-lookup"><span data-stu-id="49dfb-105">To set the size of a panel</span></span>  
  
1. <span data-ttu-id="49dfb-106">Em um procedimento, defina as <xref:System.Windows.Forms.StatusBarPanel.AutoSize%2A>propriedades <xref:System.Windows.Forms.StatusBarPanel.MinWidth%2A>, e <xref:System.Windows.Forms.StatusBarPanel.Width%2A> (ou qualquer subconjunto nele) para os painéis da <xref:System.Windows.Forms.StatusBar.Panels%2A> barra de status usando <xref:System.Windows.Forms.StatusBarPanel> seu índice passado pela propriedade da coleção.</span><span class="sxs-lookup"><span data-stu-id="49dfb-106">In a procedure, set the <xref:System.Windows.Forms.StatusBarPanel.AutoSize%2A>, <xref:System.Windows.Forms.StatusBarPanel.MinWidth%2A>, and <xref:System.Windows.Forms.StatusBarPanel.Width%2A> properties (or any subset therein) for the status-bar panels using their index passed through the <xref:System.Windows.Forms.StatusBar.Panels%2A> property of the <xref:System.Windows.Forms.StatusBarPanel> collection.</span></span>  
  
    ```vb  
    Public Sub SetStatusBarPanelSize()  
    ' Create panel and set text property.  
       StatusBar1.Panels.Add("One")  
    ' Set properties of panels.  
       StatusBar1.Panels(0).AutoSize = StatusBarPanelAutoSize.Spring  
       StatusBar1.Panels(0).Width = 200  
    ' Enable the StatusBar control to display panels.  
       StatusBar1.ShowPanels = True  
        End Sub  
    ```  
  
    ```csharp  
    public void SetStatusBarPanelSize()  
    {  
       // Create panel and set text property.  
       statusBar1.Panels.Add("One");  
       // Set properties of panels.  
       statusBar1.Panels[0].AutoSize = StatusBarPanelAutoSize.Spring;  
       statusBar1.Panels[0].Width = 200;  
       statusBar1.ShowPanels = true;  
    }  
    ```  
  
    ```cpp  
    public:  
       void SetStatusBarPanelSize()  
       {  
          // Create panel and set text property.  
          statusBar1->Panels->Add("One");  
          // Set properties of panels.  
          statusBar1->Panels[0]->AutoSize =  
             StatusBarPanelAutoSize::Spring;  
          statusBar1->Panels[0]->Width = 200;  
          statusBar1->ShowPanels = true;  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="49dfb-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="49dfb-107">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="49dfb-108">Passo a passo: Atualizando informações da barra de status em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="49dfb-108">Walkthrough: Updating Status Bar Information at Run Time</span></span>](walkthrough-updating-status-bar-information-at-run-time.md)
- [<span data-ttu-id="49dfb-109">Como: Determine em qual painel no controle StatusBar Windows Forms foi clicado</span><span class="sxs-lookup"><span data-stu-id="49dfb-109">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [<span data-ttu-id="49dfb-110">Visão geral do controle StatusBar</span><span class="sxs-lookup"><span data-stu-id="49dfb-110">StatusBar Control Overview</span></span>](statusbar-control-overview-windows-forms.md)
