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
ms.workload: dotnet
ms.openlocfilehash: 5cf689f8a7c475dbdda416297e28118d43bfdbff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-apply-a-guidelineset-to-a-drawing"></a>Como aplicar um GuidelineSet a um desenho
Este exemplo mostra como aplicar uma <xref:System.Windows.Media.GuidelineSet> para um <xref:System.Windows.Media.DrawingGroup>.  
  
 O <xref:System.Windows.Media.DrawingGroup> classe é o único tipo de <xref:System.Windows.Media.Drawing> que tem um <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> propriedade. Para aplicar um <xref:System.Windows.Media.GuidelineSet> para outro tipo de <xref:System.Windows.Media.Drawing>, adicioná-lo para um <xref:System.Windows.Media.DrawingGroup> e, em seguida, aplicar o <xref:System.Windows.Media.GuidelineSet> para sua <xref:System.Windows.Media.DrawingGroup>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria dois <xref:System.Windows.Media.DrawingGroup> objetos que são quase idênticos; a única diferença é: o segundo <xref:System.Windows.Media.DrawingGroup> tem um <xref:System.Windows.Media.GuidelineSet> e o primeiro não.  
  
 A ilustração a seguir mostra a saída do exemplo. Como a renderização a diferença entre os dois <xref:System.Windows.Media.DrawingGroup> objetos é tão sutil, partes dos desenhos são ampliadas.  
  
 ![Um DrawingGroup com e sem um GuidelineSet](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupGuidelineSetExample.cs#graphicsmmdrawinggroupguidelinesetexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupGuidelineSetExample.xaml#graphicsmmdrawinggroupguidelinesetexamplewholepage)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.DrawingGroup>  
 <xref:System.Windows.Media.GuidelineSet>  
 [Visão geral dos objetos de desenho](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
