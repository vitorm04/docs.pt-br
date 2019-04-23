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
ms.openlocfilehash: ebb53e7df979a553ed4a44deba34345c9ecac772
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59171672"
---
# <a name="how-to-draw-a-single-b233zier-spline"></a>Como: Desenhar um único B&#233;Spline de Bézier
Uma spline de Bézier é definida por quatro pontos: um ponto de início, dois pontos de controle e um ponto de extremidade.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir desenha uma spline de Bézier com ponto de partida (10, 100) e o ponto de extremidade (200, 100). Pontos de controle são (100, 10) e (150, 150).  
  
 A ilustração a seguir mostra o spline de Bézier resultante junto com seu ponto inicial, a pontos de controle e o ponto de extremidade. A ilustração também mostra envoltória convexa o spline, que é um polígono formado conectando-se em quatro pontos com linhas retas.  
  
 ![Ilustração de uma Spline de Bézier.](./media/how-to-draw-a-single-bezier-spline/bezier-spline-illustration.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Drawing.Graphics.DrawBezier%2A>
- [Splines de Bézier no GDI+](bezier-splines-in-gdi.md)
- [Como: Desenhar uma sequência de Splines de Bézier](how-to-draw-a-sequence-of-bezier-splines.md)
