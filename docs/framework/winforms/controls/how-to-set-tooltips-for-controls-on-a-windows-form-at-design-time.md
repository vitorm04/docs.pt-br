---
title: 'Como: Definir ToolTips para controles em um Windows Form no momento do design'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: 0d6725fc1a00826870e6400bffce63a1788e802c
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211695"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a><span data-ttu-id="3e144-102">Como: Definir ToolTips para controles em um Windows Form no tempo de design</span><span class="sxs-lookup"><span data-stu-id="3e144-102">How to: Set ToolTips for controls on a Windows Form at design time</span></span>

<span data-ttu-id="3e144-103">Você pode definir um <xref:System.Windows.Forms.ToolTip> cadeia de caracteres no código ou no Designer de formulários do Windows no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3e144-103">You can set a <xref:System.Windows.Forms.ToolTip> string in code or in the Windows Forms Designer in Visual Studio.</span></span> <span data-ttu-id="3e144-104">Para obter mais informações sobre o <xref:System.Windows.Forms.ToolTip> componente, consulte [visão geral do componente ToolTip](tooltip-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="3e144-104">For more information about the <xref:System.Windows.Forms.ToolTip> component, see [ToolTip Component Overview](tooltip-component-overview-windows-forms.md).</span></span>

## <a name="set-a-tooltip-programmatically"></a><span data-ttu-id="3e144-105">Definir uma dica de ferramenta de forma programática</span><span class="sxs-lookup"><span data-stu-id="3e144-105">Set a ToolTip programmatically</span></span>

1. <span data-ttu-id="3e144-106">Adicione o controle que exibirá a dica de ferramenta.</span><span class="sxs-lookup"><span data-stu-id="3e144-106">Add the control that will display the ToolTip.</span></span>

2. <span data-ttu-id="3e144-107">Use o <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> método da <xref:System.Windows.Forms.ToolTip> componente.</span><span class="sxs-lookup"><span data-stu-id="3e144-107">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>

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

## <a name="set-a-tooltip-in-the-designer"></a><span data-ttu-id="3e144-108">Definir uma dica de ferramenta no designer</span><span class="sxs-lookup"><span data-stu-id="3e144-108">Set a ToolTip in the designer</span></span>

1. <span data-ttu-id="3e144-109">No Visual Studio, adicione um <xref:System.Windows.Forms.ToolTip> componente para o formulário.</span><span class="sxs-lookup"><span data-stu-id="3e144-109">In Visual Studio, add a <xref:System.Windows.Forms.ToolTip> component to the form.</span></span>

2. <span data-ttu-id="3e144-110">Selecione o controle que será exibir a dica de ferramenta ou adicioná-lo ao formulário.</span><span class="sxs-lookup"><span data-stu-id="3e144-110">Select the control that will display the ToolTip, or add it to the form.</span></span>

3. <span data-ttu-id="3e144-111">No **propriedades** janela, defina as **dica de ferramenta no ToolTip1** valor a ser uma cadeia de caracteres apropriada de texto.</span><span class="sxs-lookup"><span data-stu-id="3e144-111">In the **Properties** window, set the **ToolTip on ToolTip1** value to an appropriate string of text.</span></span>

### <a name="to-remove-a-tooltip-programmatically"></a><span data-ttu-id="3e144-112">Para remover uma dica de ferramenta de forma programática</span><span class="sxs-lookup"><span data-stu-id="3e144-112">To remove a ToolTip programmatically</span></span>

1. <span data-ttu-id="3e144-113">Use o <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> método da <xref:System.Windows.Forms.ToolTip> componente.</span><span class="sxs-lookup"><span data-stu-id="3e144-113">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>

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

## <a name="remove-a-tooltip-in-the-designer"></a><span data-ttu-id="3e144-114">Remover uma dica de ferramenta no designer</span><span class="sxs-lookup"><span data-stu-id="3e144-114">Remove a ToolTip in the designer</span></span>

1. <span data-ttu-id="3e144-115">No Visual Studio, selecione o controle que está exibindo a dica de ferramenta.</span><span class="sxs-lookup"><span data-stu-id="3e144-115">In Visual Studio, select the control that is displaying the ToolTip.</span></span>

2. <span data-ttu-id="3e144-116">No **propriedades** janela, exclua o texto na **dica de ferramenta no ToolTip1**.</span><span class="sxs-lookup"><span data-stu-id="3e144-116">In the **Properties** window, delete the text in the **ToolTip on ToolTip1**.</span></span>

## <a name="see-also"></a><span data-ttu-id="3e144-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e144-117">See also</span></span>

- [<span data-ttu-id="3e144-118">Visão geral do componente ToolTip</span><span class="sxs-lookup"><span data-stu-id="3e144-118">ToolTip Component Overview</span></span>](tooltip-component-overview-windows-forms.md)
- [<span data-ttu-id="3e144-119">Como: Alterar o atraso do componente ToolTip dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3e144-119">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
- [<span data-ttu-id="3e144-120">Componente ToolTip</span><span class="sxs-lookup"><span data-stu-id="3e144-120">ToolTip Component</span></span>](tooltip-component-windows-forms.md)
