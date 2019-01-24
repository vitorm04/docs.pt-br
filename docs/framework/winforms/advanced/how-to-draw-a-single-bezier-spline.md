---
title: 'Como: Desenhar um único B&#233;Spline de Bézier'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Bezier splines [Windows Forms], drawing
- drawing [Windows Forms], Bezier splines
ms.assetid: f4f3fe30-f0a6-4743-ac91-11310cebea9f
ms.openlocfilehash: 32fc09c7525b40daea8c8705c43100cea0c052bc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676452"
---
# <a name="how-to-draw-a-single-b233zier-spline"></a>Como: Desenhar um único B&#233;Spline de Bézier
Uma spline de Bézier é definida por quatro pontos: um ponto de início, dois pontos de controle e um ponto de extremidade.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir desenha uma spline de Bézier com ponto de partida (10, 100) e o ponto de extremidade (200, 100). Pontos de controle são (100, 10) e (150, 150).  
  
 A ilustração a seguir mostra o spline de Bézier resultante junto com seu ponto inicial, a pontos de controle e o ponto de extremidade. A ilustração também mostra envoltória convexa o spline, que é um polígono formado conectando-se em quatro pontos com linhas retas.  
  
 ![Bezier Spline](../../../../docs/framework/winforms/advanced/media/bezierspline1.png "BezierSpline1")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Drawing.Graphics.DrawBezier%2A>
- [Splines de Bézier no GDI+](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)
- [Como: Desenhar uma sequência de Splines de Bézier](../../../../docs/framework/winforms/advanced/how-to-draw-a-sequence-of-bezier-splines.md)
