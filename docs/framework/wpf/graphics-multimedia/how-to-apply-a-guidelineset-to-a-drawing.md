---
title: Como aplicar um GuidelineSet a um desenho
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GuidelineSet property [WPF], applying to drawings
- graphics [WPF], GuidelineSet property
ms.assetid: 45f3e0b4-8820-45a7-b865-b8ea5b17b0c8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dd8d93d128c03cb9ee482860603e5734e96c6fc2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-apply-a-guidelineset-to-a-drawing"></a><span data-ttu-id="7558c-102">Como aplicar um GuidelineSet a um desenho</span><span class="sxs-lookup"><span data-stu-id="7558c-102">How to: Apply a GuidelineSet to a Drawing</span></span>
<span data-ttu-id="7558c-103">Este exemplo mostra como aplicar uma <xref:System.Windows.Media.GuidelineSet> para um <xref:System.Windows.Media.DrawingGroup>.</span><span class="sxs-lookup"><span data-stu-id="7558c-103">This example shows how to apply a <xref:System.Windows.Media.GuidelineSet> to a <xref:System.Windows.Media.DrawingGroup>.</span></span>  
  
 <span data-ttu-id="7558c-104">O <xref:System.Windows.Media.DrawingGroup> classe é o único tipo de <xref:System.Windows.Media.Drawing> que tem um <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="7558c-104">The <xref:System.Windows.Media.DrawingGroup> class is the only type of <xref:System.Windows.Media.Drawing> that has a <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> property.</span></span> <span data-ttu-id="7558c-105">Para aplicar um <xref:System.Windows.Media.GuidelineSet> para outro tipo de <xref:System.Windows.Media.Drawing>, adicioná-lo para um <xref:System.Windows.Media.DrawingGroup> e, em seguida, aplicar o <xref:System.Windows.Media.GuidelineSet> para sua <xref:System.Windows.Media.DrawingGroup>.</span><span class="sxs-lookup"><span data-stu-id="7558c-105">To apply a <xref:System.Windows.Media.GuidelineSet> to another type of <xref:System.Windows.Media.Drawing>, add it to a <xref:System.Windows.Media.DrawingGroup> and then apply the <xref:System.Windows.Media.GuidelineSet> to your <xref:System.Windows.Media.DrawingGroup>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7558c-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7558c-106">Example</span></span>  
 <span data-ttu-id="7558c-107">O exemplo a seguir cria dois <xref:System.Windows.Media.DrawingGroup> objetos que são quase idênticos; a única diferença é: o segundo <xref:System.Windows.Media.DrawingGroup> tem um <xref:System.Windows.Media.GuidelineSet> e o primeiro não.</span><span class="sxs-lookup"><span data-stu-id="7558c-107">The following example creates two <xref:System.Windows.Media.DrawingGroup> objects that are almost identical; the only difference is: the second <xref:System.Windows.Media.DrawingGroup> has a <xref:System.Windows.Media.GuidelineSet> and the first does not.</span></span>  
  
 <span data-ttu-id="7558c-108">A ilustração a seguir mostra a saída do exemplo.</span><span class="sxs-lookup"><span data-stu-id="7558c-108">The following illustration shows the output from the example.</span></span> <span data-ttu-id="7558c-109">Como a renderização a diferença entre os dois <xref:System.Windows.Media.DrawingGroup> objetos é tão sutil, partes dos desenhos são ampliadas.</span><span class="sxs-lookup"><span data-stu-id="7558c-109">Because the rendering difference between the two <xref:System.Windows.Media.DrawingGroup> objects is so subtle, portions of the drawings are enlarged.</span></span>  
  
 <span data-ttu-id="7558c-110">![Um DrawingGroup com e sem um GuidelineSet](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")</span><span class="sxs-lookup"><span data-stu-id="7558c-110">![A DrawingGroup with and without a GuidelineSet](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupGuidelineSetExample.cs#graphicsmmdrawinggroupguidelinesetexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupGuidelineSetExample.xaml#graphicsmmdrawinggroupguidelinesetexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="7558c-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7558c-111">See Also</span></span>  
 <xref:System.Windows.Media.DrawingGroup>  
 <xref:System.Windows.Media.GuidelineSet>  
 [<span data-ttu-id="7558c-112">Visão geral dos objetos de desenho</span><span class="sxs-lookup"><span data-stu-id="7558c-112">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
