---
title: 'Como: Aplicar um GuidelineSet a um desenho'
ms.date: 03/30/2017
helpviewer_keywords:
- GuidelineSet property [WPF], applying to drawings
- graphics [WPF], GuidelineSet property
ms.assetid: 45f3e0b4-8820-45a7-b865-b8ea5b17b0c8
ms.openlocfilehash: 4bd2ee349f2c1855a9af6b4c00f2630cd50a9108
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54493372"
---
# <a name="how-to-apply-a-guidelineset-to-a-drawing"></a>Como: Aplicar um GuidelineSet a um desenho
Este exemplo mostra como aplicar uma <xref:System.Windows.Media.GuidelineSet> para um <xref:System.Windows.Media.DrawingGroup>.  
  
 O <xref:System.Windows.Media.DrawingGroup> classe é o único tipo de <xref:System.Windows.Media.Drawing> que tem um <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> propriedade. Para aplicar uma <xref:System.Windows.Media.GuidelineSet> em outro tipo de <xref:System.Windows.Media.Drawing>, adicioná-lo a um <xref:System.Windows.Media.DrawingGroup> e, em seguida, aplique o <xref:System.Windows.Media.GuidelineSet> para sua <xref:System.Windows.Media.DrawingGroup>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria dois <xref:System.Windows.Media.DrawingGroup> objetos que são quase idênticos; a única diferença é: o segundo <xref:System.Windows.Media.DrawingGroup> tem um <xref:System.Windows.Media.GuidelineSet> e o primeiro não.  
  
 A ilustração a seguir mostra a saída do exemplo. Porque a renderização de diferença entre os dois <xref:System.Windows.Media.DrawingGroup> objetos é tão sutil, partes dos desenhos são ampliadas.  
  
 ![Um DrawingGroup com e sem um GuidelineSet](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupGuidelineSetExample.cs#graphicsmmdrawinggroupguidelinesetexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupGuidelineSetExample.xaml#graphicsmmdrawinggroupguidelinesetexamplewholepage)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Media.DrawingGroup>
- <xref:System.Windows.Media.GuidelineSet>
- [Visão geral dos objetos de desenho](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
