---
title: Como definir ToolTips para controles em um Windows Form no momento do design
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: 7f698a517fbf72ceafde4a117b4d92dd9d352834
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45597518"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a><span data-ttu-id="985be-102">Como definir ToolTips para controles em um Windows Form no momento do design</span><span class="sxs-lookup"><span data-stu-id="985be-102">How to: Set ToolTips for Controls on a Windows Form at Design Time</span></span>
<span data-ttu-id="985be-103">Você pode definir um <xref:System.Windows.Forms.ToolTip> cadeia de caracteres no código ou no Designer de formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="985be-103">You can set a <xref:System.Windows.Forms.ToolTip> string in code or in the Windows Forms Designer.</span></span> <span data-ttu-id="985be-104">Para obter mais informações sobre o <xref:System.Windows.Forms.ToolTip> componente, consulte [visão geral do componente ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="985be-104">For more information about the <xref:System.Windows.Forms.ToolTip> component, see [ToolTip Component Overview](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="985be-105">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="985be-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="985be-106">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="985be-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="985be-107">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="985be-107">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-set-a-tooltip-programmatically"></a><span data-ttu-id="985be-108">Para definir uma dica de ferramenta de forma programática</span><span class="sxs-lookup"><span data-stu-id="985be-108">To set a ToolTip programmatically</span></span>  
  
1.  <span data-ttu-id="985be-109">Adicione o controle que exibirá a dica de ferramenta.</span><span class="sxs-lookup"><span data-stu-id="985be-109">Add the control that will display the ToolTip.</span></span>  
  
2.  <span data-ttu-id="985be-110">Use o <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> método da <xref:System.Windows.Forms.ToolTip> componente.</span><span class="sxs-lookup"><span data-stu-id="985be-110">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>  
  
    ```vb  
    ' In this example, Button1 is the control to display the ToolTip.  
    ToolTip1.SetToolTip(Button1, "Save changes")  
    ```  
  
    ```csharp  
    // In this example, button1 is the control to display the ToolTip.  
    toolTip1.SetToolTip(button1, "Save changes");  
    ```  
  
    ```cpp  
    // In this example, button1 is the control to display the ToolTip.  
    toolTip1->SetToolTip(button1, "Save changes");  
    ```  
  
### <a name="to-set-a-tooltip-in-the-designer"></a><span data-ttu-id="985be-111">Para definir uma dica de ferramenta no designer</span><span class="sxs-lookup"><span data-stu-id="985be-111">To set a ToolTip in the designer</span></span>  
  
1.  <span data-ttu-id="985be-112">Adicionar um <xref:System.Windows.Forms.ToolTip> componente para o formulário.</span><span class="sxs-lookup"><span data-stu-id="985be-112">Add a <xref:System.Windows.Forms.ToolTip> component to the form.</span></span>  
  
2.  <span data-ttu-id="985be-113">Selecione o controle que será exibir a dica de ferramenta ou adicioná-lo ao formulário.</span><span class="sxs-lookup"><span data-stu-id="985be-113">Select the control that will display the ToolTip, or add it to the form.</span></span>  
  
3.  <span data-ttu-id="985be-114">No **propriedades** janela, defina as **dica de ferramenta no ToolTip1** valor a ser uma cadeia de caracteres apropriada de texto.</span><span class="sxs-lookup"><span data-stu-id="985be-114">In the **Properties** window, set the **ToolTip on ToolTip1** value to an appropriate string of text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="985be-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="985be-115">See Also</span></span>  
 [<span data-ttu-id="985be-116">Visão geral do componente ToolTip</span><span class="sxs-lookup"><span data-stu-id="985be-116">ToolTip Component Overview</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)  
 [<span data-ttu-id="985be-117">Como alterar o atraso do componente ToolTip dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="985be-117">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)  
 [<span data-ttu-id="985be-118">Componente ToolTip</span><span class="sxs-lookup"><span data-stu-id="985be-118">ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)
