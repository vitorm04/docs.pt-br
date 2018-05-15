---
title: Como implementar um mecanismo de layout personalizado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- layout engines [Windows Forms], custom
- TableLayoutPanel control [Windows Forms], layout engine
- layout engines [Windows Forms], implementing
- FlowLayoutPanel control [Windows Forms], layout engine
ms.assetid: f91aa91c-29f4-4089-95ca-5d48b774b00e
ms.openlocfilehash: 0444f0d03a36adf833c04167c6d7a3c302ab15dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-implement-a-custom-layout-engine"></a><span data-ttu-id="59de5-102">Como implementar um mecanismo de layout personalizado</span><span class="sxs-lookup"><span data-stu-id="59de5-102">How to: Implement a Custom Layout Engine</span></span>
<span data-ttu-id="59de5-103">O exemplo de código a seguir demonstra como criar um mecanismo de layout personalizado que executa um layout de fluxo simples.</span><span class="sxs-lookup"><span data-stu-id="59de5-103">The following code example demonstrates how to create a custom layout engine that performs a simple flow layout.</span></span> <span data-ttu-id="59de5-104">Ele implementa um controle de painel chamado `DemoFlowPanel`, que substitui o <xref:System.Windows.Forms.Control.LayoutEngine%2A> propriedade para fornecer uma instância do `DemoFlowLayout` classe.</span><span class="sxs-lookup"><span data-stu-id="59de5-104">It implements a panel control named `DemoFlowPanel`, which overrides the <xref:System.Windows.Forms.Control.LayoutEngine%2A> property to provide an instance of the `DemoFlowLayout` class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59de5-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="59de5-105">Example</span></span>  
 [!code-cpp[System.Windows.Forms.Layout.LayoutEngine#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.Layout.LayoutEngine/cpp/DemoFlowLayout.cpp#1)]
 [!code-csharp[System.Windows.Forms.Layout.LayoutEngine#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Layout.LayoutEngine/CS/DemoFlowLayout.cs#1)]
 [!code-vb[System.Windows.Forms.Layout.LayoutEngine#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Layout.LayoutEngine/VB/DemoFlowLayout.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="59de5-106">Consulte também</span><span class="sxs-lookup"><span data-stu-id="59de5-106">See Also</span></span>  
 <xref:System.Windows.Forms.Layout.LayoutEngine>  
 <xref:System.Windows.Forms.Control.LayoutEngine%2A?displayProperty=nameWithType>
