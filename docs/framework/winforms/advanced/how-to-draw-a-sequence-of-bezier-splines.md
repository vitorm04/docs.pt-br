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
ms.openlocfilehash: 2b74b03137d5a450fb1e436a514877d1a17229ad
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654244"
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
