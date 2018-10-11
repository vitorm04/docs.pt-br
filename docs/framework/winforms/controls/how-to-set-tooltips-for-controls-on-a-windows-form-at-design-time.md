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
ms.openlocfilehash: 689b06e8fbebe490f79ab6c12f144546472a95ff
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49087213"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a><span data-ttu-id="d5a94-102">Como definir ToolTips para controles em um Windows Form no momento do design</span><span class="sxs-lookup"><span data-stu-id="d5a94-102">How to: Set ToolTips for Controls on a Windows Form at Design Time</span></span>
<span data-ttu-id="d5a94-103">Você pode definir um <xref:System.Windows.Forms.ToolTip> cadeia de caracteres no código ou no Designer de formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="d5a94-103">You can set a <xref:System.Windows.Forms.ToolTip> string in code or in the Windows Forms Designer.</span></span> <span data-ttu-id="d5a94-104">Para obter mais informações sobre o <xref:System.Windows.Forms.ToolTip> componente, consulte [visão geral do componente ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="d5a94-104">For more information about the <xref:System.Windows.Forms.ToolTip> component, see [ToolTip Component Overview](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5a94-105">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="d5a94-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d5a94-106">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="d5a94-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d5a94-107">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="d5a94-107">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-set-a-tooltip-programmatically"></a><span data-ttu-id="d5a94-108">Para definir uma dica de ferramenta de forma programática</span><span class="sxs-lookup"><span data-stu-id="d5a94-108">To set a ToolTip programmatically</span></span>  
  
1.  <span data-ttu-id="d5a94-109">Adicione o controle que exibirá a dica de ferramenta.</span><span class="sxs-lookup"><span data-stu-id="d5a94-109">Add the control that will display the ToolTip.</span></span>  
  
2.  <span data-ttu-id="d5a94-110">Use o <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> método da <xref:System.Windows.Forms.ToolTip> componente.</span><span class="sxs-lookup"><span data-stu-id="d5a94-110">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>  
  
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
  
### <a name="to-set-a-tooltip-in-the-designer"></a><span data-ttu-id="d5a94-111">Para definir uma dica de ferramenta no designer</span><span class="sxs-lookup"><span data-stu-id="d5a94-111">To set a ToolTip in the designer</span></span>  
  
1.  <span data-ttu-id="d5a94-112">Adicionar um <xref:System.Windows.Forms.ToolTip> componente para o formulário.</span><span class="sxs-lookup"><span data-stu-id="d5a94-112">Add a <xref:System.Windows.Forms.ToolTip> component to the form.</span></span>  
  
2.  <span data-ttu-id="d5a94-113">Selecione o controle que será exibir a dica de ferramenta ou adicioná-lo ao formulário.</span><span class="sxs-lookup"><span data-stu-id="d5a94-113">Select the control that will display the ToolTip, or add it to the form.</span></span>  
  
3.  <span data-ttu-id="d5a94-114">No **propriedades** janela, defina as **dica de ferramenta no ToolTip1** valor a ser uma cadeia de caracteres apropriada de texto.</span><span class="sxs-lookup"><span data-stu-id="d5a94-114">In the **Properties** window, set the **ToolTip on ToolTip1** value to an appropriate string of text.</span></span>  

### <a name="to-remove-a-tooltip-programmatically"></a><span data-ttu-id="d5a94-115">Para remover uma dica de ferramenta de forma programática</span><span class="sxs-lookup"><span data-stu-id="d5a94-115">To remove a ToolTip programmatically</span></span>  
  
1.  <span data-ttu-id="d5a94-116">Use o <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> método da <xref:System.Windows.Forms.ToolTip> componente.</span><span class="sxs-lookup"><span data-stu-id="d5a94-116">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>  
  
    ```vb  
    ' In this example, Button1 is the control displaying the ToolTip.  
    ToolTip1.SetToolTip(Button1, Nothing)  
    ```  
  
    ```csharp  
    // In this example, button1 is the control displaying the ToolTip.  
    toolTip1.SetToolTip(button1, null);  
    ```  
  
    ```cpp  
    // In this example, button1 is the control displaying the ToolTip.  
    toolTip1->SetToolTip(button1, NULL);  
    ```  
  
### <a name="to-remove-a-tooltip-in-the-designer"></a><span data-ttu-id="d5a94-117">Para remover uma dica de ferramenta no designer</span><span class="sxs-lookup"><span data-stu-id="d5a94-117">To remove a ToolTip in the designer</span></span>  
  
1.  <span data-ttu-id="d5a94-118">Selecione o controle que está exibindo a dica de ferramenta.</span><span class="sxs-lookup"><span data-stu-id="d5a94-118">Select the control that is displaying the ToolTip.</span></span>  
  
2.  <span data-ttu-id="d5a94-119">No **propriedades** janela, exclua o texto na **dica de ferramenta no ToolTip1**.</span><span class="sxs-lookup"><span data-stu-id="d5a94-119">In the **Properties** window, delete the text in the **ToolTip on ToolTip1**.</span></span>  

## <a name="see-also"></a><span data-ttu-id="d5a94-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d5a94-120">See Also</span></span>  
- [<span data-ttu-id="d5a94-121">Visão geral do componente ToolTip</span><span class="sxs-lookup"><span data-stu-id="d5a94-121">ToolTip Component Overview</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)  
- [<span data-ttu-id="d5a94-122">Como alterar o atraso do componente ToolTip dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d5a94-122">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)  
- [<span data-ttu-id="d5a94-123">Componente ToolTip</span><span class="sxs-lookup"><span data-stu-id="d5a94-123">ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)
