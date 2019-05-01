---
title: 'Como: Desenhar uma forma fechada usando o elemento Polygon'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], Polygon elements
- closed shapes [WPF], drawing with Polygon elements
- Polygon elements [WPF]
- drawing [WPF], closed shapes with Polygon elements
ms.assetid: 4b0ca008-29ce-48dd-8bc3-f3a20ffca6a6
ms.openlocfilehash: 533c341e2fae528ec896bf38bafa13974af1d127
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62003230"
---
# <a name="how-to-draw-a-closed-shape-by-using-the-polygon-element"></a>Como: Desenhar uma forma fechada usando o elemento Polygon
Este exemplo mostra como desenhar uma forma fechada usando o <xref:System.Windows.Shapes.Polygon> elemento. Para desenhar uma forma fechada, crie uma <xref:System.Windows.Shapes.Polygon> elemento e use seu <xref:System.Windows.Shapes.Polygon.Points%2A> propriedade para especificar os vértices de uma forma. Uma linha é desenhada automaticamente que conecta o primeiro e último pontos. Por fim, especifique um <xref:System.Windows.Shapes.Shape.Fill%2A>, um <xref:System.Windows.Shapes.Shape.Stroke%2A>, ou ambos.  
  
## <a name="example"></a>Exemplo  
 Em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], sintaxe válida para os pontos é uma lista delimitada por espaço de pares de coordenadas x e y, separados por vírgulas.  
  
 [!code-xaml[drawingwithshapeelements#PolygonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polygonexample.xaml#polygonexample1)]  
  
 Embora o exemplo usa uma <xref:System.Windows.Controls.Canvas> para conter os polígonos, você pode usar elementos de polígono (e todos os outros elementos de forma) com qualquer <xref:System.Windows.Controls.Panel> ou <xref:System.Windows.Controls.Control> que dá suporte a conteúdo não textual.  
  
 Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, consulte o [Exemplo de elementos de forma](https://go.microsoft.com/fwlink/?LinkID=160037).
