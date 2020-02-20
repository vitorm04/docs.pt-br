---
title: Como desenhar uma forma fechada usando o elemento Polygon
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], Polygon elements
- closed shapes [WPF], drawing with Polygon elements
- Polygon elements [WPF]
- drawing [WPF], closed shapes with Polygon elements
ms.assetid: 4b0ca008-29ce-48dd-8bc3-f3a20ffca6a6
ms.openlocfilehash: 324a5623ee658789b8600a43a89ce26cab7cd6cd
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452968"
---
# <a name="how-to-draw-a-closed-shape-by-using-the-polygon-element"></a>Como desenhar uma forma fechada usando o elemento Polygon
Este exemplo mostra como desenhar uma forma fechada usando o elemento <xref:System.Windows.Shapes.Polygon>. Para desenhar uma forma fechada, crie um elemento <xref:System.Windows.Shapes.Polygon> e use sua propriedade <xref:System.Windows.Shapes.Polygon.Points%2A> para especificar os vértices de uma forma. Uma linha é desenhada automaticamente que conecta o primeiro e o último pontos. Por fim, especifique um <xref:System.Windows.Shapes.Shape.Fill%2A>, um <xref:System.Windows.Shapes.Shape.Stroke%2A>ou ambos.  
  
## <a name="example"></a>Exemplo  
 Em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], sintaxe válida para os pontos é uma lista delimitada por espaço de pares de coordenadas x e y, separados por vírgulas.  
  
 [!code-xaml[drawingwithshapeelements#PolygonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polygonexample.xaml#polygonexample1)]  
  
 Embora o exemplo use um <xref:System.Windows.Controls.Canvas> para conter os polígonos, você pode usar elementos Polygon (e todos os outros elementos Shape) com qualquer <xref:System.Windows.Controls.Panel> ou <xref:System.Windows.Controls.Control> que ofereça suporte a conteúdo que não seja de texto.  
  
 Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, consulte o [Exemplo de elementos de forma](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).
