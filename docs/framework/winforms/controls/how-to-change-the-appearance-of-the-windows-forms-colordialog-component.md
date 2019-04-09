---
title: 'Como: Alterar a aparência do componente ColorDialog do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ColorDialog component [Windows Forms], examples
- ColorDialog component [Windows Forms], formatting appearance
- color dialog box [Windows Forms], configuring appearance
ms.assetid: bba4e262-1cd7-4f63-89cf-330a36f7b539
ms.openlocfilehash: d79139ac3d11d3cd9a7d1bbe1f12e14df83530e0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59094639"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-colordialog-component"></a><span data-ttu-id="ac39d-102">Como: Alterar a aparência do componente ColorDialog do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ac39d-102">How to: Change the Appearance of the Windows Forms ColorDialog Component</span></span>
<span data-ttu-id="ac39d-103">Você pode configurar a aparência dos formulários Windows <xref:System.Windows.Forms.ColorDialog> componente com um número de suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="ac39d-103">You can configure the appearance of the Windows Forms <xref:System.Windows.Forms.ColorDialog> component with a number of its properties.</span></span> <span data-ttu-id="ac39d-104">A caixa de diálogo tem duas seções, uma que mostra as cores básicas e outra que permite que o usuário defina cores personalizadas.</span><span class="sxs-lookup"><span data-stu-id="ac39d-104">The dialog box has two sections — one that shows basic colors and one that allows the user to define custom colors.</span></span>  
  
 <span data-ttu-id="ac39d-105">A maioria das propriedades restringe quais cores o usuário pode selecionar da caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="ac39d-105">Most of the properties restrict what colors the user can select from the dialog box.</span></span> <span data-ttu-id="ac39d-106">Se o <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> estiver definida como `true`, o usuário tem permissão para definir cores personalizadas.</span><span class="sxs-lookup"><span data-stu-id="ac39d-106">If the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> property is set to `true`, the user is allowed to define custom colors.</span></span> <span data-ttu-id="ac39d-107">O <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> é de propriedade `true` se a caixa de diálogo é expandida para definir cores personalizadas; caso contrário, o usuário deve clicar em um botão "Definir cores personalizadas".</span><span class="sxs-lookup"><span data-stu-id="ac39d-107">The <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> property is `true` if the dialog box is expanded to define custom colors; otherwise the user must click a "Define Custom Colors" button.</span></span> <span data-ttu-id="ac39d-108">Quando o <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> estiver definida como `true`, a caixa de diálogo exibe todas as cores disponíveis no conjunto de cores básicas.</span><span class="sxs-lookup"><span data-stu-id="ac39d-108">When the <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> property is set to `true`, the dialog box displays all available colors in the set of basic colors.</span></span> <span data-ttu-id="ac39d-109">Se o <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> estiver definida como `true`, o usuário não poderá selecionar cores pontilhadas; apenas cores sólidas estarão disponíveis para seleção.</span><span class="sxs-lookup"><span data-stu-id="ac39d-109">If the <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> property is set to `true`, the user cannot select dithered colors; only solid colors are available to select.</span></span>  
  
 <span data-ttu-id="ac39d-110">Se o <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> estiver definida como `true`, um botão Ajuda aparece na caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="ac39d-110">If the <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> property is set to `true`, a Help button appears on the dialog box.</span></span> <span data-ttu-id="ac39d-111">Quando o usuário clica no botão de Ajuda, o <xref:System.Windows.Forms.ColorDialog> do componente <xref:System.Windows.Forms.CommonDialog.HelpRequest> é gerado.</span><span class="sxs-lookup"><span data-stu-id="ac39d-111">When the user clicks the Help button, the <xref:System.Windows.Forms.ColorDialog> component's <xref:System.Windows.Forms.CommonDialog.HelpRequest> event is raised.</span></span>  
  
### <a name="to-configure-the-appearance-of-the-color-dialog-box"></a><span data-ttu-id="ac39d-112">Para configurar a aparência da caixa de diálogo de cor</span><span class="sxs-lookup"><span data-stu-id="ac39d-112">To configure the appearance of the color dialog box</span></span>  
  
1.  <span data-ttu-id="ac39d-113">Defina as <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>, e <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> propriedades com os valores desejados.</span><span class="sxs-lookup"><span data-stu-id="ac39d-113">Set the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>, and <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> properties to the desired values.</span></span>  
  
    ```vb  
    ColorDialog1.AllowFullOpen = True  
    ColorDialog1.AnyColor = True  
    ColorDialog1.SolidColorOnly = False  
    ColorDialog1.ShowHelp = True  
    ```  
  
    ```csharp  
    colorDialog1.AllowFullOpen = true;  
    colorDialog1.AnyColor = true;  
    colorDialog1.SolidColorOnly = false;  
    colorDialog1.ShowHelp = true;  
    ```  
  
    ```cpp  
    colorDialog1->AllowFullOpen = true;  
    colorDialog1->AnyColor = true;  
    colorDialog1->SolidColorOnly = false;  
    colorDialog1->ShowHelp = true;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ac39d-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac39d-114">See also</span></span>

- <xref:System.Windows.Forms.ColorDialog>
- [<span data-ttu-id="ac39d-115">Componente ColorDialog</span><span class="sxs-lookup"><span data-stu-id="ac39d-115">ColorDialog Component</span></span>](colordialog-component-windows-forms.md)
- [<span data-ttu-id="ac39d-116">Visão geral do componente ColorDialog</span><span class="sxs-lookup"><span data-stu-id="ac39d-116">ColorDialog Component Overview</span></span>](colordialog-component-overview-windows-forms.md)
