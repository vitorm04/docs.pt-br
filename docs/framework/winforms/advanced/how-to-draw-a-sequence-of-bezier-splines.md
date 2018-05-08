---
title: 'Como: Desenhar uma sequência de B&#233;zier Splines'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- splines [Windows Forms], drawing Bezier
- Bezier splines [Windows Forms], drawing sequence of
ms.assetid: 37a0bedb-20c2-4cf0-91fa-a5509e826b30
ms.openlocfilehash: 8439e08109630b9a59c8e0359aa4d18e5241412c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-draw-a-sequence-of-b233zier-splines"></a>Como: Desenhar uma sequência de B&#233;zier Splines
Você pode usar o <xref:System.Drawing.Graphics.DrawBeziers%2A> método o <xref:System.Drawing.Graphics> conectado de classe para desenhar uma sequência de splines de Bézier.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir desenha uma curva que consiste em dois splines de Bézier conectados. O ponto de extremidade da primeira spline de Bézier é o ponto de início da segunda spline de Bézier.  
  
 A ilustração a seguir mostra os splines conectados junto com os sete pontos.  
  
 ![Os Spline de Bézier](../../../../docs/framework/winforms/advanced/media/bezierspline2.png "BezierSpline2")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.  
  
## <a name="see-also"></a>Consulte também  
 [Elementos Gráficos e Desenho nos Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Splines de Bézier no GDI+](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)  
 [Construir e Desenhar Curvas](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)
