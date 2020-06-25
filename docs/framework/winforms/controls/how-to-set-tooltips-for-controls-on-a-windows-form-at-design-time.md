---
title: Como definir ToolTips para controles em um Windows Form no momento do design
description: Saiba como definir dicas de ferramenta para controles programaticamente ou na Designer de Formulários do Windows no Visual Studio.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: 15134b38d11de30d0e6a2f998f6ea266affc40d7
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325973"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a><span data-ttu-id="3d720-103">Como definir dicas de ferramentas para controles em um formulário do Windows em tempo de design</span><span class="sxs-lookup"><span data-stu-id="3d720-103">How to: Set ToolTips for controls on a Windows Form at design time</span></span>

<span data-ttu-id="3d720-104">Você pode definir uma <xref:System.Windows.Forms.ToolTip> cadeia de caracteres no código ou na Designer de formulários do Windows no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3d720-104">You can set a <xref:System.Windows.Forms.ToolTip> string in code or in the Windows Forms Designer in Visual Studio.</span></span> <span data-ttu-id="3d720-105">Para obter mais informações sobre o <xref:System.Windows.Forms.ToolTip> componente, consulte [visão geral do componente de dica de ferramenta](tooltip-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="3d720-105">For more information about the <xref:System.Windows.Forms.ToolTip> component, see [ToolTip Component Overview](tooltip-component-overview-windows-forms.md).</span></span>

## <a name="set-a-tooltip-programmatically"></a><span data-ttu-id="3d720-106">Definir uma dica de ferramenta programaticamente</span><span class="sxs-lookup"><span data-stu-id="3d720-106">Set a ToolTip programmatically</span></span>

1. <span data-ttu-id="3d720-107">Adicione o controle que exibirá a dica de ferramenta.</span><span class="sxs-lookup"><span data-stu-id="3d720-107">Add the control that will display the ToolTip.</span></span>

2. <span data-ttu-id="3d720-108">Use o <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> método do <xref:System.Windows.Forms.ToolTip> componente.</span><span class="sxs-lookup"><span data-stu-id="3d720-108">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>

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

## <a name="set-a-tooltip-in-the-designer"></a><span data-ttu-id="3d720-109">Definir uma dica de ferramenta no designer</span><span class="sxs-lookup"><span data-stu-id="3d720-109">Set a ToolTip in the designer</span></span>

1. <span data-ttu-id="3d720-110">No Visual Studio, adicione um <xref:System.Windows.Forms.ToolTip> componente ao formulário.</span><span class="sxs-lookup"><span data-stu-id="3d720-110">In Visual Studio, add a <xref:System.Windows.Forms.ToolTip> component to the form.</span></span>

2. <span data-ttu-id="3d720-111">Selecione o controle que exibirá a dica de ferramenta ou adicione-a ao formulário.</span><span class="sxs-lookup"><span data-stu-id="3d720-111">Select the control that will display the ToolTip, or add it to the form.</span></span>

3. <span data-ttu-id="3d720-112">Na janela **Propriedades** , defina a **dica de ferramenta no valor ToolTip1** como uma cadeia de texto apropriada.</span><span class="sxs-lookup"><span data-stu-id="3d720-112">In the **Properties** window, set the **ToolTip on ToolTip1** value to an appropriate string of text.</span></span>

### <a name="to-remove-a-tooltip-programmatically"></a><span data-ttu-id="3d720-113">Para remover uma dica de ferramenta programaticamente</span><span class="sxs-lookup"><span data-stu-id="3d720-113">To remove a ToolTip programmatically</span></span>

1. <span data-ttu-id="3d720-114">Use o <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> método do <xref:System.Windows.Forms.ToolTip> componente.</span><span class="sxs-lookup"><span data-stu-id="3d720-114">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>

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

## <a name="remove-a-tooltip-in-the-designer"></a><span data-ttu-id="3d720-115">Remover uma dica de ferramenta no designer</span><span class="sxs-lookup"><span data-stu-id="3d720-115">Remove a ToolTip in the designer</span></span>

1. <span data-ttu-id="3d720-116">No Visual Studio, selecione o controle que está exibindo a dica de ferramenta.</span><span class="sxs-lookup"><span data-stu-id="3d720-116">In Visual Studio, select the control that is displaying the ToolTip.</span></span>

2. <span data-ttu-id="3d720-117">Na janela **Propriedades** , exclua o texto na **dica de ferramenta em ToolTip1**.</span><span class="sxs-lookup"><span data-stu-id="3d720-117">In the **Properties** window, delete the text in the **ToolTip on ToolTip1**.</span></span>

## <a name="see-also"></a><span data-ttu-id="3d720-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="3d720-118">See also</span></span>

- [<span data-ttu-id="3d720-119">Visão geral do componente ToolTip</span><span class="sxs-lookup"><span data-stu-id="3d720-119">ToolTip Component Overview</span></span>](tooltip-component-overview-windows-forms.md)
- [<span data-ttu-id="3d720-120">Como alterar o atraso do componente ToolTip dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3d720-120">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
- [<span data-ttu-id="3d720-121">Componente ToolTip</span><span class="sxs-lookup"><span data-stu-id="3d720-121">ToolTip Component</span></span>](tooltip-component-windows-forms.md)
