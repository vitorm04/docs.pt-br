---
title: Como definir ToolTips para controles em um Windows Form no momento do design
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28a83a623329a7bf0162bb9feb0dc21bb73611cf
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a><span data-ttu-id="e5882-102">Como definir ToolTips para controles em um Windows Form no momento do design</span><span class="sxs-lookup"><span data-stu-id="e5882-102">How to: Set ToolTips for Controls on a Windows Form at Design Time</span></span>
<span data-ttu-id="e5882-103">Você pode definir um <xref:System.Windows.Forms.ToolTip> cadeia de caracteres no código ou no Designer de formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="e5882-103">You can set a <xref:System.Windows.Forms.ToolTip> string in code or in the Windows Forms Designer.</span></span> <span data-ttu-id="e5882-104">Para obter mais informações sobre o <xref:System.Windows.Forms.ToolTip> componente, consulte [visão geral do componente ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="e5882-104">For more information about the <xref:System.Windows.Forms.ToolTip> component, see [ToolTip Component Overview](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5882-105">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="e5882-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="e5882-106">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="e5882-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="e5882-107">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="e5882-107">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-set-a-tooltip-programmatically"></a><span data-ttu-id="e5882-108">Para definir uma dica de ferramenta programaticamente</span><span class="sxs-lookup"><span data-stu-id="e5882-108">To set a ToolTip programmatically</span></span>  
  
1.  <span data-ttu-id="e5882-109">Adicione o controle que exibirá a dica de ferramenta.</span><span class="sxs-lookup"><span data-stu-id="e5882-109">Add the control that will display the ToolTip.</span></span>  
  
2.  <span data-ttu-id="e5882-110">Use o <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> método o <xref:System.Windows.Forms.ToolTip> componente.</span><span class="sxs-lookup"><span data-stu-id="e5882-110">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>  
  
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
  
### <a name="to-set-a-tooltip-in-the-designer"></a><span data-ttu-id="e5882-111">Para definir uma dica de ferramenta no designer</span><span class="sxs-lookup"><span data-stu-id="e5882-111">To set a ToolTip in the designer</span></span>  
  
1.  <span data-ttu-id="e5882-112">Adicionar um <xref:System.Windows.Forms.ToolTip> componente para o formulário.</span><span class="sxs-lookup"><span data-stu-id="e5882-112">Add a <xref:System.Windows.Forms.ToolTip> component to the form.</span></span>  
  
2.  <span data-ttu-id="e5882-113">Selecione o controle que exibe a dica de ferramenta ou adicioná-lo ao formulário.</span><span class="sxs-lookup"><span data-stu-id="e5882-113">Select the control that will display the ToolTip, or add it to the form.</span></span>  
  
3.  <span data-ttu-id="e5882-114">No **propriedades** janela, defina o **dica de ferramenta em ToolTip1** valor para uma cadeia de caracteres de texto apropriada.</span><span class="sxs-lookup"><span data-stu-id="e5882-114">In the **Properties** window, set the **ToolTip on ToolTip1** value to an appropriate string of text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5882-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5882-115">See Also</span></span>  
 [<span data-ttu-id="e5882-116">Visão geral do componente ToolTip</span><span class="sxs-lookup"><span data-stu-id="e5882-116">ToolTip Component Overview</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)  
 [<span data-ttu-id="e5882-117">Como alterar o atraso do componente ToolTip dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e5882-117">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)  
 [<span data-ttu-id="e5882-118">Componente ToolTip</span><span class="sxs-lookup"><span data-stu-id="e5882-118">ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)
