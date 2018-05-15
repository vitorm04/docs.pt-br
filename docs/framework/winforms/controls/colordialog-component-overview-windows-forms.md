---
title: Visão geral do componente ColorDialog (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ColorDialog
helpviewer_keywords:
- color dialog box [Windows Forms], about color dialog box
- ColorDialog component [Windows Forms], about ColorDialog
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
ms.openlocfilehash: 9b4fb545a2ed35a9c7bad5e28c28d3ec42870860
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="colordialog-component-overview-windows-forms"></a><span data-ttu-id="fff5b-102">Visão geral do componente ColorDialog (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="fff5b-102">ColorDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="fff5b-103">Windows Forms <xref:System.Windows.Forms.ColorDialog> componente é uma caixa de diálogo pré-configurado que permite ao usuário selecionar uma cor de uma paleta de e para adicionar cores personalizadas para essa paleta.</span><span class="sxs-lookup"><span data-stu-id="fff5b-103">The Windows Forms <xref:System.Windows.Forms.ColorDialog> component is a pre-configured dialog box that allows the user to select a color from a palette and to add custom colors to that palette.</span></span> <span data-ttu-id="fff5b-104">É a mesma caixa de diálogo que você vê em outros aplicativos baseados no Windows para selecionar cores.</span><span class="sxs-lookup"><span data-stu-id="fff5b-104">It is the same dialog box that you see in other Windows-based applications to select colors.</span></span> <span data-ttu-id="fff5b-105">Use-a em seu aplicativo baseado no Windows como uma solução simples em vez de configurar sua própria caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="fff5b-105">Use it within your Windows-based application as a simple solution in lieu of configuring your own dialog box.</span></span>  
  
 <span data-ttu-id="fff5b-106">A cor selecionada na caixa de diálogo é retornada no <xref:System.Windows.Forms.ColorDialog.Color%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="fff5b-106">The color selected in the dialog box is returned in the <xref:System.Windows.Forms.ColorDialog.Color%2A> property.</span></span> <span data-ttu-id="fff5b-107">Se o <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> está definida como `false`, o botão "Definir cores personalizadas" está desabilitado e o usuário é restrito às cores na paleta predefinidas.</span><span class="sxs-lookup"><span data-stu-id="fff5b-107">If the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> property is set to `false`, the "Define Custom Colors" button is disabled and the user is restricted to the predefined colors in the palette.</span></span> <span data-ttu-id="fff5b-108">Se o <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> está definida como `true`, o usuário não é possível selecionar cores pontilhadas.</span><span class="sxs-lookup"><span data-stu-id="fff5b-108">If the <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> property is set to `true`, the user cannot select dithered colors.</span></span> <span data-ttu-id="fff5b-109">Para exibir a caixa de diálogo, você deve chamar o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método.</span><span class="sxs-lookup"><span data-stu-id="fff5b-109">To display the dialog box, you must call its <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fff5b-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fff5b-110">See Also</span></span>  
 <xref:System.Windows.Forms.ColorDialog>  
 [<span data-ttu-id="fff5b-111">Componente ColorDialog</span><span class="sxs-lookup"><span data-stu-id="fff5b-111">ColorDialog Component</span></span>](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)  
 [<span data-ttu-id="fff5b-112">Controles e componentes da caixa de diálogo</span><span class="sxs-lookup"><span data-stu-id="fff5b-112">Dialog-Box Controls and Components</span></span>](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)  
 [<span data-ttu-id="fff5b-113">Como alterar a aparência do componente ColorDialog dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fff5b-113">How to: Change the Appearance of the Windows Forms ColorDialog Component</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)
