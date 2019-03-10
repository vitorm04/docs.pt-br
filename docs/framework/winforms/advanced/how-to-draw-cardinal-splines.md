---
title: 'Como: Desenhar splines cardinais'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cardinal splines [Windows Forms], drawing
- drawing [Windows Forms], cardinal splines
- graphics [Windows Forms], cardinal splines
ms.assetid: a4a41e80-4461-4b47-b6bd-2c5e68881994
ms.openlocfilehash: 687143273a07acba4b4d60acb1be25eee165b91d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710479"
---
# <a name="how-to-draw-cardinal-splines"></a>Como: Desenhar splines cardinais
Um spline cardinal é uma curva que passa suavemente por um determinado conjunto de pontos. Para desenhar um spline cardinal, crie uma <xref:System.Drawing.Graphics> do objeto e passar o endereço de uma matriz de pontos para o <xref:System.Drawing.Graphics.DrawCurve%2A> método.  
  
### <a name="drawing-a-bell-shaped-cardinal-spline"></a>Desenhando um spline cardinal em forma de sino  
  
-   O exemplo a seguir desenha um spline cardinal em forma de sino que passa por cinco pontos designados. A ilustração a seguir mostra a curva e cinco pontos.  
  
     ![Spline cardinal](./media/cardinalspline1.png "CardinalSpline1")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#21)]  
  
### <a name="drawing-a-closed-cardinal-spline"></a>Desenhando um spline cardinal fechado  
  
-   Use o <xref:System.Drawing.Graphics.DrawClosedCurve%2A> método da <xref:System.Drawing.Graphics> classe para desenhar um spline cardinal fechado. Em um spline cardinal fechado, a curva continua durante o último ponto na matriz e se conecta com o primeiro ponto na matriz. O exemplo a seguir desenha um spline cardinal fechado que passa por seis pontos designados. A ilustração a seguir mostra o spline fechado junto com os seis pontos.  
  
 ![Spline cardinal](./media/cardinalspline1a.png "CardinalSpline1A")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#22)]  
  
### <a name="changing-the-bend-of-a-cardinal-spline"></a>Alterando a curva de um spline cardinal  
  
-   Alterar a maneira como um spline cardinal se dobra, passando um argumento de tensão para os <xref:System.Drawing.Graphics.DrawCurve%2A> método. O exemplo a seguir desenha três splines cardinais que passam pelo mesmo conjunto de pontos. A ilustração a seguir mostra os três splines junto com seus valores de tensão. Observe que, quando a tensão for 0, os pontos são conectados por linhas retas.  
  
 ![Spline cardinal](./media/cardinalspline2.png "CardinalSpline2")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#23)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Os exemplos anteriores são projetados para uso com o Windows Forms e exigem <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.  
  
## <a name="see-also"></a>Consulte também
- [Linhas, Curvas e Formas](lines-curves-and-shapes.md)
- [Construir e Desenhar Curvas](constructing-and-drawing-curves.md)
