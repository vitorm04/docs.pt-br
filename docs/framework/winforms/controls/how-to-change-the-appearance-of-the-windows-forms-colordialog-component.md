---
title: Alterar a aparência do componente ColorDialog
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
ms.openlocfilehash: 0402d7f3c03a0771512a03ac54e1b093c9fe6e9b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746639"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-colordialog-component"></a><span data-ttu-id="20fa0-102">Como alterar a aparência do componente ColorDialog dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="20fa0-102">How to: Change the Appearance of the Windows Forms ColorDialog Component</span></span>
<span data-ttu-id="20fa0-103">Você pode configurar a aparência do componente Windows Forms <xref:System.Windows.Forms.ColorDialog> com um número de suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="20fa0-103">You can configure the appearance of the Windows Forms <xref:System.Windows.Forms.ColorDialog> component with a number of its properties.</span></span> <span data-ttu-id="20fa0-104">A caixa de diálogo tem duas seções, uma que mostra as cores básicas e outra que permite que o usuário defina cores personalizadas.</span><span class="sxs-lookup"><span data-stu-id="20fa0-104">The dialog box has two sections — one that shows basic colors and one that allows the user to define custom colors.</span></span>  
  
 <span data-ttu-id="20fa0-105">A maioria das propriedades restringe quais cores o usuário pode selecionar da caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="20fa0-105">Most of the properties restrict what colors the user can select from the dialog box.</span></span> <span data-ttu-id="20fa0-106">Se a propriedade <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> for definida como `true`, o usuário poderá definir cores personalizadas.</span><span class="sxs-lookup"><span data-stu-id="20fa0-106">If the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> property is set to `true`, the user is allowed to define custom colors.</span></span> <span data-ttu-id="20fa0-107">A propriedade <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> será `true` se a caixa de diálogo for expandida para definir cores personalizadas; caso contrário, o usuário deverá clicar em um botão "definir cores personalizadas".</span><span class="sxs-lookup"><span data-stu-id="20fa0-107">The <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> property is `true` if the dialog box is expanded to define custom colors; otherwise the user must click a "Define Custom Colors" button.</span></span> <span data-ttu-id="20fa0-108">Quando a propriedade <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> é definida como `true`, a caixa de diálogo exibe todas as cores disponíveis no conjunto de cores básicas.</span><span class="sxs-lookup"><span data-stu-id="20fa0-108">When the <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> property is set to `true`, the dialog box displays all available colors in the set of basic colors.</span></span> <span data-ttu-id="20fa0-109">Se a propriedade <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> for definida como `true`, o usuário não poderá selecionar cores diquerdas; somente as cores sólidas estão disponíveis para seleção.</span><span class="sxs-lookup"><span data-stu-id="20fa0-109">If the <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> property is set to `true`, the user cannot select dithered colors; only solid colors are available to select.</span></span>  
  
 <span data-ttu-id="20fa0-110">Se a propriedade <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> for definida como `true`, um botão ajuda aparecerá na caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="20fa0-110">If the <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> property is set to `true`, a Help button appears on the dialog box.</span></span> <span data-ttu-id="20fa0-111">Quando o usuário clica no botão ajuda, o evento de <xref:System.Windows.Forms.CommonDialog.HelpRequest> do componente de <xref:System.Windows.Forms.ColorDialog> é gerado.</span><span class="sxs-lookup"><span data-stu-id="20fa0-111">When the user clicks the Help button, the <xref:System.Windows.Forms.ColorDialog> component's <xref:System.Windows.Forms.CommonDialog.HelpRequest> event is raised.</span></span>  
  
### <a name="to-configure-the-appearance-of-the-color-dialog-box"></a><span data-ttu-id="20fa0-112">Para configurar a aparência da caixa de diálogo de cor</span><span class="sxs-lookup"><span data-stu-id="20fa0-112">To configure the appearance of the color dialog box</span></span>  
  
1. <span data-ttu-id="20fa0-113">Defina as propriedades <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>e <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> para os valores desejados.</span><span class="sxs-lookup"><span data-stu-id="20fa0-113">Set the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>, and <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> properties to the desired values.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="20fa0-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="20fa0-114">See also</span></span>

- <xref:System.Windows.Forms.ColorDialog>
- [<span data-ttu-id="20fa0-115">Componente ColorDialog</span><span class="sxs-lookup"><span data-stu-id="20fa0-115">ColorDialog Component</span></span>](colordialog-component-windows-forms.md)
- [<span data-ttu-id="20fa0-116">Visão geral do componente ColorDialog</span><span class="sxs-lookup"><span data-stu-id="20fa0-116">ColorDialog Component Overview</span></span>](colordialog-component-overview-windows-forms.md)
