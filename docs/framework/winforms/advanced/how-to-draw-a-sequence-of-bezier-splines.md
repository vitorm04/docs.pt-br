---
title: 'Como: Desenhar uma sequência de B&#233;Splines de Bézier'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- splines [Windows Forms], drawing Bezier
- Bezier splines [Windows Forms], drawing sequence of
ms.assetid: 37a0bedb-20c2-4cf0-91fa-a5509e826b30
ms.openlocfilehash: 976787f5830282a581d05a9c24d1f83dceca4b25
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004245"
---
# <a name="how-to-draw-a-sequence-of-b233zier-splines"></a>Como: Desenhar uma sequência de B&#233;Splines de Bézier
Você pode usar o <xref:System.Drawing.Graphics.DrawBeziers%2A> método da <xref:System.Drawing.Graphics> conectado de classe para desenhar uma sequência de splines de Bézier.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir desenha uma curva que consiste em dois splines de Bézier conectadas. O ponto de extremidade da primeira spline de Bézier é o ponto de início da segunda spline de Bézier.  
  
 A ilustração a seguir mostra os conectados splines junto com os sete pontos:  
  
 ![Gráfico que mostra os conectados splines junto com sete pontos.](./media/how-to-draw-a-sequence-of-bezier-splines/bezier-spline-seven-points.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.  
  
## <a name="see-also"></a>Consulte também

- [Elementos Gráficos e Desenho nos Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Splines de Bézier no GDI+](bezier-splines-in-gdi.md)
- [Construir e Desenhar Curvas](constructing-and-drawing-curves.md)
