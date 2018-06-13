---
title: 'Como: Desenhar uma única B&#233;zier Spline'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Bezier splines [Windows Forms], drawing
- drawing [Windows Forms], Bezier splines
ms.assetid: f4f3fe30-f0a6-4743-ac91-11310cebea9f
ms.openlocfilehash: 9e91b63275c37fc0cdde5721fddd114e1bf2264e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521330"
---
# <a name="how-to-draw-a-single-b233zier-spline"></a>Como: Desenhar uma única B&#233;zier Spline
Uma spline de Bézier é definida por quatro pontos: um ponto inicial, dois pontos de controle e um ponto de extremidade.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir desenha um spline de Bézier com o ponto inicial (10, 100) e o ponto de extremidade (200, 100). O controle pontos são (100, 10) e (150, 150).  
  
 A ilustração a seguir mostra o spline de Bézier resultante juntamente com seu ponto inicial, a pontos de controle e o ponto de extremidade. A ilustração também mostra forma convexa os spline, que é um polígono formado conectando os quatro pontos com linhas retas.  
  
 ![Os Spline de Bézier](../../../../docs/framework/winforms/advanced/media/bezierspline1.png "BezierSpline1")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Drawing.Graphics.DrawBezier%2A>  
 [Splines de Bézier no GDI+](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)  
 [Como Desenhar uma Sequência de Splines de Bézier](../../../../docs/framework/winforms/advanced/how-to-draw-a-sequence-of-bezier-splines.md)
