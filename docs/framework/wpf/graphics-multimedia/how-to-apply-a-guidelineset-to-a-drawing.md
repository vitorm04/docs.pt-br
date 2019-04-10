---
title: 'Como: Aplicar um GuidelineSet a um desenho'
ms.date: 03/30/2017
helpviewer_keywords:
- GuidelineSet property [WPF], applying to drawings
- graphics [WPF], GuidelineSet property
ms.assetid: 45f3e0b4-8820-45a7-b865-b8ea5b17b0c8
ms.openlocfilehash: 134236c5beca806b747d45f20764cc82ddd8a4e8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217803"
---
# <a name="how-to-apply-a-guidelineset-to-a-drawing"></a><span data-ttu-id="906de-102">Como: Aplicar um GuidelineSet a um desenho</span><span class="sxs-lookup"><span data-stu-id="906de-102">How to: Apply a GuidelineSet to a Drawing</span></span>
<span data-ttu-id="906de-103">Este exemplo mostra como aplicar uma <xref:System.Windows.Media.GuidelineSet> para um <xref:System.Windows.Media.DrawingGroup>.</span><span class="sxs-lookup"><span data-stu-id="906de-103">This example shows how to apply a <xref:System.Windows.Media.GuidelineSet> to a <xref:System.Windows.Media.DrawingGroup>.</span></span>  
  
 <span data-ttu-id="906de-104">O <xref:System.Windows.Media.DrawingGroup> classe é o único tipo de <xref:System.Windows.Media.Drawing> que tem um <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="906de-104">The <xref:System.Windows.Media.DrawingGroup> class is the only type of <xref:System.Windows.Media.Drawing> that has a <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> property.</span></span> <span data-ttu-id="906de-105">Para aplicar uma <xref:System.Windows.Media.GuidelineSet> em outro tipo de <xref:System.Windows.Media.Drawing>, adicioná-lo a um <xref:System.Windows.Media.DrawingGroup> e, em seguida, aplique o <xref:System.Windows.Media.GuidelineSet> para sua <xref:System.Windows.Media.DrawingGroup>.</span><span class="sxs-lookup"><span data-stu-id="906de-105">To apply a <xref:System.Windows.Media.GuidelineSet> to another type of <xref:System.Windows.Media.Drawing>, add it to a <xref:System.Windows.Media.DrawingGroup> and then apply the <xref:System.Windows.Media.GuidelineSet> to your <xref:System.Windows.Media.DrawingGroup>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="906de-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="906de-106">Example</span></span>  
 <span data-ttu-id="906de-107">O exemplo a seguir cria dois <xref:System.Windows.Media.DrawingGroup> objetos que são quase idênticos; a única diferença é: o segundo <xref:System.Windows.Media.DrawingGroup> tem um <xref:System.Windows.Media.GuidelineSet> e o primeiro não.</span><span class="sxs-lookup"><span data-stu-id="906de-107">The following example creates two <xref:System.Windows.Media.DrawingGroup> objects that are almost identical; the only difference is: the second <xref:System.Windows.Media.DrawingGroup> has a <xref:System.Windows.Media.GuidelineSet> and the first does not.</span></span>  
  
 <span data-ttu-id="906de-108">A ilustração a seguir mostra a saída do exemplo.</span><span class="sxs-lookup"><span data-stu-id="906de-108">The following illustration shows the output from the example.</span></span> <span data-ttu-id="906de-109">Porque a renderização de diferença entre os dois <xref:System.Windows.Media.DrawingGroup> objetos é tão sutil, partes dos desenhos são ampliadas.</span><span class="sxs-lookup"><span data-stu-id="906de-109">Because the rendering difference between the two <xref:System.Windows.Media.DrawingGroup> objects is so subtle, portions of the drawings are enlarged.</span></span>  
  
 <span data-ttu-id="906de-110">![Um DrawingGroup com e sem um GuidelineSet](./media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")</span><span class="sxs-lookup"><span data-stu-id="906de-110">![A DrawingGroup with and without a GuidelineSet](./media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupGuidelineSetExample.cs#graphicsmmdrawinggroupguidelinesetexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupGuidelineSetExample.xaml#graphicsmmdrawinggroupguidelinesetexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="906de-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="906de-111">See also</span></span>

- <xref:System.Windows.Media.DrawingGroup>
- <xref:System.Windows.Media.GuidelineSet>
- [<span data-ttu-id="906de-112">Visão geral dos objetos de desenho</span><span class="sxs-lookup"><span data-stu-id="906de-112">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
