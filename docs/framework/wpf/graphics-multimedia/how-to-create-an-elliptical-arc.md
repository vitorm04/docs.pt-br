---
title: Como criar um arco elíptico
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], elliptical arcs
- elliptical arcs [WPF], creating
- arcs [WPF], elliptical
ms.assetid: 3dcfe502-3485-45de-99fb-d53a1367c484
ms.openlocfilehash: d0fffbb25f3c5aaceb2cd80af4f1093e44111200
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453059"
---
# <a name="how-to-create-an-elliptical-arc"></a>Como criar um arco elíptico
Este exemplo mostra como desenhar um arco elíptico. Para criar um arco elíptico, use as classes <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>e <xref:System.Windows.Media.ArcSegment>.  
  
## <a name="example"></a>Exemplo  
 Nos exemplos a seguir, um arco elíptico é desenhado de (10.100) a (200.100). O arco tem um <xref:System.Windows.Media.ArcSegment.Size%2A> de 100 por 50 pixels independentes de dispositivo, uma <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> de 45 graus, uma configuração de <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> de `true`e uma <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> de <xref:System.Windows.Media.SweepDirection.Counterclockwise>.  
  
 XAML  
  
 No [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], você pode usar a sintaxe de atributo para descrever um caminho.  
  
 [!code-xaml[GeometrySample#56](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#56)]  
  
 XAML  
  
 (Observe que essa sintaxe de atributo, na verdade, cria uma <xref:System.Windows.Media.StreamGeometry>, uma versão de peso mais leve de um <xref:System.Windows.Media.PathGeometry>. Para obter mais informações, consulte a página [sintaxe de marcação de caminho](path-markup-syntax.md) .)  
  
 Em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você também pode desenhar um arco elíptico explicitamente usando marcas de objeto. O seguinte é equivalente à marcação de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] anterior.  
  
 [!code-xaml[GeometrySample#36](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#36)]  
  
 Este exemplo é parte de um exemplo maior. Para obter o exemplo completo, consulte o [exemplo de geometrias](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).  
  
## <a name="see-also"></a>Confira também

- [Criar uma curva de Bézier quadrática](how-to-create-a-quadratic-bezier-curve.md)
- [Criar uma curva de Bézier cúbica](how-to-create-a-cubic-bezier-curve.md)
