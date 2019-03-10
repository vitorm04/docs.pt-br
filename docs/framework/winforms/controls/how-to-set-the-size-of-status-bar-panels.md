---
title: 'Como: Definir o tamanho de painéis da barra de Status'
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
ms.openlocfilehash: 5b78463ca273f089f036166f5339977be435ccc9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711935"
---
# <a name="how-to-set-the-size-of-status-bar-panels"></a><span data-ttu-id="acd8b-102">Como: Definir o tamanho de painéis da barra de Status</span><span class="sxs-lookup"><span data-stu-id="acd8b-102">How to: Set the Size of Status-Bar Panels</span></span>
> [!NOTE]
>  <span data-ttu-id="acd8b-103">O controle <xref:System.Windows.Forms.ToolStripStatusLabel> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.StatusBar>, no entanto, o controle <xref:System.Windows.Forms.StatusBar> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.</span><span class="sxs-lookup"><span data-stu-id="acd8b-103">The <xref:System.Windows.Forms.ToolStripStatusLabel> control replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control; however, the <xref:System.Windows.Forms.StatusBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="acd8b-104">Cada instância das <xref:System.Windows.Forms.StatusBarPanel> classe dentro de uma [controle StatusBar](statusbar-control-windows-forms.md) controle tem um número de propriedades dinâmicas que determinam sua largura e redimensionam o comportamento em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="acd8b-104">Each instance of the <xref:System.Windows.Forms.StatusBarPanel> class within a [StatusBar Control](statusbar-control-windows-forms.md) control has a number of dynamic properties that determine its width and resize behavior at run time.</span></span>  
  
### <a name="to-set-the-size-of-a-panel"></a><span data-ttu-id="acd8b-105">Para definir o tamanho de um painel</span><span class="sxs-lookup"><span data-stu-id="acd8b-105">To set the size of a panel</span></span>  
  
1.  <span data-ttu-id="acd8b-106">Em um procedimento, defina a <xref:System.Windows.Forms.StatusBarPanel.AutoSize%2A>, <xref:System.Windows.Forms.StatusBarPanel.MinWidth%2A>, e <xref:System.Windows.Forms.StatusBarPanel.Width%2A> propriedades (ou qualquer subconjunto nele) para a barra de status painéis usando seu índice passado a <xref:System.Windows.Forms.StatusBar.Panels%2A> propriedade do <xref:System.Windows.Forms.StatusBarPanel> coleção.</span><span class="sxs-lookup"><span data-stu-id="acd8b-106">In a procedure, set the <xref:System.Windows.Forms.StatusBarPanel.AutoSize%2A>, <xref:System.Windows.Forms.StatusBarPanel.MinWidth%2A>, and <xref:System.Windows.Forms.StatusBarPanel.Width%2A> properties (or any subset therein) for the status-bar panels using their index passed through the <xref:System.Windows.Forms.StatusBar.Panels%2A> property of the <xref:System.Windows.Forms.StatusBarPanel> collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="acd8b-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="acd8b-107">See also</span></span>
- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="acd8b-108">Passo a passo: Atualizando informações da barra de Status em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="acd8b-108">Walkthrough: Updating Status Bar Information at Run Time</span></span>](walkthrough-updating-status-bar-information-at-run-time.md)
- [<span data-ttu-id="acd8b-109">Como: Determinar qual painel no controle StatusBar dos Windows Forms foi clicado</span><span class="sxs-lookup"><span data-stu-id="acd8b-109">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [<span data-ttu-id="acd8b-110">Visão geral do controle StatusBar</span><span class="sxs-lookup"><span data-stu-id="acd8b-110">StatusBar Control Overview</span></span>](statusbar-control-overview-windows-forms.md)
