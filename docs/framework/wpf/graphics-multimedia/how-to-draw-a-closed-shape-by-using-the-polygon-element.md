---
title: Como desenhar uma forma fechada usando o elemento Polygon
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], Polygon elements
- closed shapes [WPF], drawing with Polygon elements
- Polygon elements [WPF]
- drawing [WPF], closed shapes with Polygon elements
ms.assetid: 4b0ca008-29ce-48dd-8bc3-f3a20ffca6a6
ms.openlocfilehash: 4105139e159783cf0197f4e56c82001835077cbf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559455"
---
# <a name="how-to-draw-a-closed-shape-by-using-the-polygon-element"></a>Como desenhar uma forma fechada usando o elemento Polygon
Este exemplo mostra como desenhar uma forma fechada, usando o <xref:System.Windows.Shapes.Polygon> elemento. Para desenhar uma forma fechada, crie um <xref:System.Windows.Shapes.Polygon> elemento e use seu <xref:System.Windows.Shapes.Polygon.Points%2A> propriedade para especificar os vértices de uma forma. Uma linha é desenhada automaticamente que conecta o primeiro e último pontos. Finalmente, especifique um <xref:System.Windows.Shapes.Shape.Fill%2A>, um <xref:System.Windows.Shapes.Shape.Stroke%2A>, ou ambos.  
  
## <a name="example"></a>Exemplo  
 Em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], sintaxe válida para os pontos é uma lista delimitada por espaço de pares de coordenadas x e y, separados por vírgulas.  
  
 [!code-xaml[drawingwithshapeelements#PolygonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polygonexample.xaml#polygonexample1)]  
  
 Embora o exemplo usa um <xref:System.Windows.Controls.Canvas> para conter os polígonos, você pode usar elementos polígono (e todos os outros elementos de forma) com qualquer <xref:System.Windows.Controls.Panel> ou <xref:System.Windows.Controls.Control> que dá suporte a conteúdo não texto.  
  
 Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, consulte o [Exemplo de elementos de forma](http://go.microsoft.com/fwlink/?LinkID=160037).
