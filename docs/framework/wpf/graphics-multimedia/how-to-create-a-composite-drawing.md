---
title: 'Como: Criar um desenho composto'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], composite
- composite drawings [WPF]
- graphics [WPF], composite drawings
ms.assetid: 066eb0ab-5f0e-439d-85c6-dca60af269fc
ms.openlocfilehash: 886956b03bd3e17360283cee1bc0e4db1d2a4731
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491409"
---
# <a name="how-to-create-a-composite-drawing"></a>Como: Criar um desenho composto
Este exemplo mostra como usar um <xref:System.Windows.Media.DrawingGroup> para criar desenhos complexos combinando vários <xref:System.Windows.Media.Drawing> objetos em um único desenho composto.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa uma <xref:System.Windows.Media.DrawingGroup> para criar um desenho composto por meio de <xref:System.Windows.Media.GeometryDrawing> e <xref:System.Windows.Media.ImageDrawing> objetos. A ilustração a seguir mostra a saída que esse exemplo produz.  
  
 ![Um DrawingGroup com vários desenhos](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple.jpg "graphicsmm_simple")  
Um desenho composto criado usando DrawingGroup  
  
 Observe a borda cinza, que mostra os limites do desenho.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 Você pode usar um <xref:System.Windows.Media.DrawingGroup> para aplicar uma <xref:System.Windows.Media.DrawingGroup.Transform%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A> definir, <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, ou <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> aos desenhos que ele contém. Como uma <xref:System.Windows.Media.DrawingGroup> também é um <xref:System.Windows.Media.Drawing>, ele pode conter outros <xref:System.Windows.Media.DrawingGroup> objetos.  
  
 O exemplo a seguir é semelhante ao exemplo anterior, exceto que ele usa adicionais <xref:System.Windows.Media.DrawingGroup> objetos para aplicar efeitos de bitmap e uma máscara de opacidade a alguns dos seus desenhos. A ilustração a seguir mostra a saída que esse exemplo produz.  
  
 ![Um DrawingGroup com vários desenhos](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-multiple.jpg "graphicsmm_multiple")  
Desenho composto que tem vários objetos DrawingGroup  
  
 Observe a borda cinza, que mostra os limites do desenho.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmmultipledrawinggroupsexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmmultipledrawinggroupsexample)]  
  
 Para obter mais informações sobre <xref:System.Windows.Media.Drawing> objetos, consulte [visão geral de objetos de desenho](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>
- <xref:System.Windows.Media.DrawingGroup.Transform%2A>
- <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>
- <xref:System.Windows.Media.DrawingGroup.Opacity%2A>
- <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>
- <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>
- [Visão geral dos objetos de desenho](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
