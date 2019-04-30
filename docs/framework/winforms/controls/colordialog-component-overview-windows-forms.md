---
title: Visão geral do componente ColorDialog (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ColorDialog
helpviewer_keywords:
- color dialog box [Windows Forms], about color dialog box
- ColorDialog component [Windows Forms], about ColorDialog
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
ms.openlocfilehash: 284d42218fb4fbce873325b1e45c883d51eefab8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61956332"
---
# <a name="colordialog-component-overview-windows-forms"></a><span data-ttu-id="f85e9-102">Visão geral do componente ColorDialog (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="f85e9-102">ColorDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="f85e9-103">Os formulários do Windows <xref:System.Windows.Forms.ColorDialog> componente é uma caixa de diálogo pré-configurada que permite ao usuário selecionar uma cor de uma paleta e adicione cores personalizadas a essa paleta.</span><span class="sxs-lookup"><span data-stu-id="f85e9-103">The Windows Forms <xref:System.Windows.Forms.ColorDialog> component is a pre-configured dialog box that allows the user to select a color from a palette and to add custom colors to that palette.</span></span> <span data-ttu-id="f85e9-104">É a mesma caixa de diálogo que você vê em outros aplicativos baseados no Windows para selecionar cores.</span><span class="sxs-lookup"><span data-stu-id="f85e9-104">It is the same dialog box that you see in other Windows-based applications to select colors.</span></span> <span data-ttu-id="f85e9-105">Use-a em seu aplicativo baseado no Windows como uma solução simples em vez de configurar sua própria caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="f85e9-105">Use it within your Windows-based application as a simple solution in lieu of configuring your own dialog box.</span></span>  
  
 <span data-ttu-id="f85e9-106">A cor selecionada na caixa de diálogo é retornada no <xref:System.Windows.Forms.ColorDialog.Color%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="f85e9-106">The color selected in the dialog box is returned in the <xref:System.Windows.Forms.ColorDialog.Color%2A> property.</span></span> <span data-ttu-id="f85e9-107">Se o <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> estiver definida como `false`, o botão "Definir cores personalizadas" estará desabilitado e o usuário está restrito a cores predefinidas na paleta.</span><span class="sxs-lookup"><span data-stu-id="f85e9-107">If the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> property is set to `false`, the "Define Custom Colors" button is disabled and the user is restricted to the predefined colors in the palette.</span></span> <span data-ttu-id="f85e9-108">Se o <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> estiver definida como `true`, o usuário não poderá selecionar cores pontilhadas.</span><span class="sxs-lookup"><span data-stu-id="f85e9-108">If the <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> property is set to `true`, the user cannot select dithered colors.</span></span> <span data-ttu-id="f85e9-109">Para exibir a caixa de diálogo, você deve chamar seu <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método.</span><span class="sxs-lookup"><span data-stu-id="f85e9-109">To display the dialog box, you must call its <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f85e9-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f85e9-110">See also</span></span>

- <xref:System.Windows.Forms.ColorDialog>
- [<span data-ttu-id="f85e9-111">Componente ColorDialog</span><span class="sxs-lookup"><span data-stu-id="f85e9-111">ColorDialog Component</span></span>](colordialog-component-windows-forms.md)
- [<span data-ttu-id="f85e9-112">Controles e componentes da caixa de diálogo</span><span class="sxs-lookup"><span data-stu-id="f85e9-112">Dialog-Box Controls and Components</span></span>](dialog-box-controls-and-components-windows-forms.md)
- [<span data-ttu-id="f85e9-113">Como: Alterar a aparência do componente ColorDialog dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f85e9-113">How to: Change the Appearance of the Windows Forms ColorDialog Component</span></span>](how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)
