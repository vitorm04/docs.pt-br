---
title: 'Como: Usar um classe de renderização do controle'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- professional appearance [Windows Forms], rendering Windows Forms controls
- visual themes [Windows Forms], applying to Windows Forms controls
- visual styles [Windows Forms], rendering Windows Forms controls
ms.assetid: c0125e34-cd74-4c35-818c-3e40f462b0a3
ms.openlocfilehash: d9da43b1686f416cf2149cef07665b0a726c3b0c
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723147"
---
# <a name="how-to-use-a-control-rendering-class"></a><span data-ttu-id="24cfb-102">Como: Usar um classe de renderização do controle</span><span class="sxs-lookup"><span data-stu-id="24cfb-102">How to: Use a Control Rendering Class</span></span>
<span data-ttu-id="24cfb-103">Este exemplo demonstra como usar o <xref:System.Windows.Forms.ComboBoxRenderer> classe para renderizar a seta suspensa de uma combinação de controle de caixa.</span><span class="sxs-lookup"><span data-stu-id="24cfb-103">This example demonstrates how to use the <xref:System.Windows.Forms.ComboBoxRenderer> class to render the drop-down arrow of a combo box control.</span></span> <span data-ttu-id="24cfb-104">O exemplo consiste de <xref:System.Windows.Forms.Control.OnPaint%2A> método de um controle personalizado simple.</span><span class="sxs-lookup"><span data-stu-id="24cfb-104">The example consists of the <xref:System.Windows.Forms.Control.OnPaint%2A> method of a simple custom control.</span></span> <span data-ttu-id="24cfb-105">O <xref:System.Windows.Forms.ComboBoxRenderer.IsSupported%2A?displayProperty=nameWithType> propriedade é usada para determinar se os estilos visuais estão habilitados na área de cliente do windows do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="24cfb-105">The <xref:System.Windows.Forms.ComboBoxRenderer.IsSupported%2A?displayProperty=nameWithType> property is used to determine whether visual styles are enabled in the client area of application windows.</span></span> <span data-ttu-id="24cfb-106">Se os estilos visuais estiverem ativos, em seguida, a <xref:System.Windows.Forms.ComboBoxRenderer.DrawDropDownButton%2A?displayProperty=nameWithType> método processará a seta suspensa com estilos visuais; caso contrário, o <xref:System.Windows.Forms.ControlPaint.DrawComboButton%2A?displayProperty=nameWithType> método processará a seta suspensa no estilo clássico do Windows.</span><span class="sxs-lookup"><span data-stu-id="24cfb-106">If visual styles are active, then the <xref:System.Windows.Forms.ComboBoxRenderer.DrawDropDownButton%2A?displayProperty=nameWithType> method will render the drop-down arrow with visual styles; otherwise, the <xref:System.Windows.Forms.ControlPaint.DrawComboButton%2A?displayProperty=nameWithType> method will render the drop-down arrow in the classic Windows style.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24cfb-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="24cfb-107">Example</span></span>  
 [!code-cpp[System.Windows.Forms_ControlRenderer#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/cpp/form1.cpp#10)]
 [!code-csharp[System.Windows.Forms_ControlRenderer#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms_ControlRenderer#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="24cfb-108">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="24cfb-108">Compiling the Code</span></span>  
 <span data-ttu-id="24cfb-109">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="24cfb-109">This example requires:</span></span>  
  
-   <span data-ttu-id="24cfb-110">Um controle personalizado derivado de <xref:System.Windows.Forms.Control> classe.</span><span class="sxs-lookup"><span data-stu-id="24cfb-110">A custom control derived from the <xref:System.Windows.Forms.Control> class.</span></span>  
  
-   <span data-ttu-id="24cfb-111">Um <xref:System.Windows.Forms.Form> que hospeda o controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="24cfb-111">A <xref:System.Windows.Forms.Form> that hosts the custom control.</span></span>  
  
-   <span data-ttu-id="24cfb-112">Referências para o <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, e <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> namespaces.</span><span class="sxs-lookup"><span data-stu-id="24cfb-112">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24cfb-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="24cfb-113">See also</span></span>
- [<span data-ttu-id="24cfb-114">Renderizando controles com estilos visuais</span><span class="sxs-lookup"><span data-stu-id="24cfb-114">Rendering Controls with Visual Styles</span></span>](rendering-controls-with-visual-styles.md)
