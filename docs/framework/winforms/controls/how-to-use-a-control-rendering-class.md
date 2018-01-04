---
title: "Como usar uma classe de renderização do controle"
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
- professional appearance [Windows Forms], rendering Windows Forms controls
- visual themes [Windows Forms], applying to Windows Forms controls
- visual styles [Windows Forms], rendering Windows Forms controls
ms.assetid: c0125e34-cd74-4c35-818c-3e40f462b0a3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bbf17ea84cb24d167975e6b918a0410a38c8ed3b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-control-rendering-class"></a><span data-ttu-id="88e7a-102">Como usar uma classe de renderização do controle</span><span class="sxs-lookup"><span data-stu-id="88e7a-102">How to: Use a Control Rendering Class</span></span>
<span data-ttu-id="88e7a-103">Este exemplo demonstra como usar o <xref:System.Windows.Forms.ComboBoxRenderer> classe para renderizar a seta suspensa de uma caixa de combinação controle de caixa.</span><span class="sxs-lookup"><span data-stu-id="88e7a-103">This example demonstrates how to use the <xref:System.Windows.Forms.ComboBoxRenderer> class to render the drop-down arrow of a combo box control.</span></span> <span data-ttu-id="88e7a-104">O exemplo consiste de <xref:System.Windows.Forms.Control.OnPaint%2A> método de um controle personalizado simples.</span><span class="sxs-lookup"><span data-stu-id="88e7a-104">The example consists of the <xref:System.Windows.Forms.Control.OnPaint%2A> method of a simple custom control.</span></span> <span data-ttu-id="88e7a-105">O <xref:System.Windows.Forms.ComboBoxRenderer.IsSupported%2A?displayProperty=nameWithType> propriedade é usada para determinar se os estilos visuais são habilitados na área do cliente do windows do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="88e7a-105">The <xref:System.Windows.Forms.ComboBoxRenderer.IsSupported%2A?displayProperty=nameWithType> property is used to determine whether visual styles are enabled in the client area of application windows.</span></span> <span data-ttu-id="88e7a-106">Se os estilos visuais estão ativos, o <xref:System.Windows.Forms.ComboBoxRenderer.DrawDropDownButton%2A?displayProperty=nameWithType> método processará a seta suspensa com estilos visuais; caso contrário, o <xref:System.Windows.Forms.ControlPaint.DrawComboButton%2A?displayProperty=nameWithType> método processará a seta suspensa no estilo clássico do Windows.</span><span class="sxs-lookup"><span data-stu-id="88e7a-106">If visual styles are active, then the <xref:System.Windows.Forms.ComboBoxRenderer.DrawDropDownButton%2A?displayProperty=nameWithType> method will render the drop-down arrow with visual styles; otherwise, the <xref:System.Windows.Forms.ControlPaint.DrawComboButton%2A?displayProperty=nameWithType> method will render the drop-down arrow in the classic Windows style.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88e7a-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="88e7a-107">Example</span></span>  
 [!code-cpp[System.Windows.Forms_ControlRenderer#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/cpp/form1.cpp#10)]
 [!code-csharp[System.Windows.Forms_ControlRenderer#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms_ControlRenderer#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="88e7a-108">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="88e7a-108">Compiling the Code</span></span>  
 <span data-ttu-id="88e7a-109">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="88e7a-109">This example requires:</span></span>  
  
-   <span data-ttu-id="88e7a-110">Um controle personalizado derivado de <xref:System.Windows.Forms.Control> classe.</span><span class="sxs-lookup"><span data-stu-id="88e7a-110">A custom control derived from the <xref:System.Windows.Forms.Control> class.</span></span>  
  
-   <span data-ttu-id="88e7a-111">Um <xref:System.Windows.Forms.Form> que hospeda o controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="88e7a-111">A <xref:System.Windows.Forms.Form> that hosts the custom control.</span></span>  
  
-   <span data-ttu-id="88e7a-112">Referências a <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, e <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> namespaces.</span><span class="sxs-lookup"><span data-stu-id="88e7a-112">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88e7a-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="88e7a-113">See Also</span></span>  
 [<span data-ttu-id="88e7a-114">Renderizando controles com estilos visuais</span><span class="sxs-lookup"><span data-stu-id="88e7a-114">Rendering Controls with Visual Styles</span></span>](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)
