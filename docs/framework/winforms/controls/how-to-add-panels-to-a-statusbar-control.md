---
title: 'Como: Adicionar painéis a um controle StatusBar'
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
ms.openlocfilehash: 27d65c07f0a6ec4a25d057e2c16a8b59933bb8fd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925104"
---
# <a name="how-to-add-panels-to-a-statusbar-control"></a><span data-ttu-id="d8d22-102">Como: Adicionar painéis a um controle StatusBar</span><span class="sxs-lookup"><span data-stu-id="d8d22-102">How to: Add Panels to a StatusBar Control</span></span>
> [!IMPORTANT]
> <span data-ttu-id="d8d22-103">Os <xref:System.Windows.Forms.StatusStrip> controles <xref:System.Windows.Forms.ToolStripStatusLabel> e <xref:System.Windows.Forms.StatusBar> substituem e adicionam funcionalidade aos <xref:System.Windows.Forms.StatusBarPanel> controles e; no entanto <xref:System.Windows.Forms.StatusBarPanel> , os <xref:System.Windows.Forms.StatusBar> controles e são mantidos para compatibilidade com versões anteriores e uso futuro, se você escolha.</span><span class="sxs-lookup"><span data-stu-id="d8d22-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="d8d22-104">A área programável dentro de um controle de [controle StatusBar](statusbar-control-windows-forms.md) consiste em instâncias <xref:System.Windows.Forms.StatusBarPanel> da classe.</span><span class="sxs-lookup"><span data-stu-id="d8d22-104">The programmable area within a [StatusBar Control](statusbar-control-windows-forms.md) control consists of instances of the <xref:System.Windows.Forms.StatusBarPanel> class.</span></span> <span data-ttu-id="d8d22-105">Eles são adicionados por meio de adições <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> à classe.</span><span class="sxs-lookup"><span data-stu-id="d8d22-105">These are added through additions to the <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> class.</span></span>  
  
### <a name="to-add-panels-to-a-status-bar"></a><span data-ttu-id="d8d22-106">Para adicionar painéis a uma barra de status</span><span class="sxs-lookup"><span data-stu-id="d8d22-106">To add panels to a status bar</span></span>  
  
1. <span data-ttu-id="d8d22-107">Em um procedimento, crie painéis de barra de status adicionando-os ao <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span><span class="sxs-lookup"><span data-stu-id="d8d22-107">In a procedure, create status-bar panels by adding them to the <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span></span> <span data-ttu-id="d8d22-108">Especifique as configurações de propriedade para painéis individuais usando seu índice passado pela <xref:System.Windows.Forms.StatusBar.Panels%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="d8d22-108">Specify property settings for individual panels by using its index passed through the <xref:System.Windows.Forms.StatusBar.Panels%2A> property.</span></span>  
  
     <span data-ttu-id="d8d22-109">No exemplo de código a seguir, o caminho definido para o local do ícone é a pasta **Meus Documentos**.</span><span class="sxs-lookup"><span data-stu-id="d8d22-109">In the following code example, the path set for the location of the icon is the **My Documents** folder.</span></span> <span data-ttu-id="d8d22-110">Esse local é usado porque você pode supor que a maioria dos computadores que executam o sistema operacional Windows inclui essa pasta.</span><span class="sxs-lookup"><span data-stu-id="d8d22-110">This location is used because you can assume that most computers running the Windows operating system will include this folder.</span></span> <span data-ttu-id="d8d22-111">Escolher esse local também permite que os usuários com níveis mínimos de acesso ao sistema executem com mais segurança o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d8d22-111">Choosing this location also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="d8d22-112">O exemplo a seguir requer um formulário com <xref:System.Windows.Forms.StatusBar> um controle já adicionado.</span><span class="sxs-lookup"><span data-stu-id="d8d22-112">The following example requires a form with a <xref:System.Windows.Forms.StatusBar> control already added.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d8d22-113">O <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> é uma coleção com base em zero, portanto, o código deve continuar de acordo.</span><span class="sxs-lookup"><span data-stu-id="d8d22-113">The <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> is a zero-based collection, so code should proceed accordingly.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d8d22-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8d22-114">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- <span data-ttu-id="d8d22-115">[Caixa de diálogo Editor de coleção](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/xc4yyekt(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d8d22-115">[Collection Editor Dialog Box](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/xc4yyekt(v=vs.100))</span></span>
- [<span data-ttu-id="d8d22-116">Como: Definir o tamanho dos painéis da barra de status</span><span class="sxs-lookup"><span data-stu-id="d8d22-116">How to: Set the Size of Status-Bar Panels</span></span>](how-to-set-the-size-of-status-bar-panels.md)
- [<span data-ttu-id="d8d22-117">Passo a passo: Atualizando informações da barra de status em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="d8d22-117">Walkthrough: Updating Status Bar Information at Run Time</span></span>](walkthrough-updating-status-bar-information-at-run-time.md)
- [<span data-ttu-id="d8d22-118">Como: Determine em qual painel no controle StatusBar Windows Forms foi clicado</span><span class="sxs-lookup"><span data-stu-id="d8d22-118">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [<span data-ttu-id="d8d22-119">Visão geral do controle StatusBar</span><span class="sxs-lookup"><span data-stu-id="d8d22-119">StatusBar Control Overview</span></span>](statusbar-control-overview-windows-forms.md)
