---
title: Como desenhar splines cardinais
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cardinal splines [Windows Forms], drawing
- drawing [Windows Forms], cardinal splines
- graphics [Windows Forms], cardinal splines
ms.assetid: a4a41e80-4461-4b47-b6bd-2c5e68881994
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c47ff269cb1c367abee0be197fdc80485fb37b97
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-cardinal-splines"></a>Como desenhar splines cardinais
Um spline cardinal é uma curva que passa suavemente por um determinado conjunto de pontos. Para desenhar uma spline cardeal, crie um <xref:System.Drawing.Graphics> de objeto e passar o endereço de uma matriz de pontos para a <xref:System.Drawing.Graphics.DrawCurve%2A> método.  
  
### <a name="drawing-a-bell-shaped-cardinal-spline"></a>Desenhando um spline cardinal em forma de sino  
  
-   O exemplo a seguir desenha um spline cardinal em forma de sino que passa por cinco pontos designados. A ilustração a seguir mostra a curva e cinco pontos.  
  
     ![Spline cardinal](../../../../docs/framework/winforms/advanced/media/cardinalspline1.png "CardinalSpline1")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#21)]  
  
### <a name="drawing-a-closed-cardinal-spline"></a>Desenhando um spline cardinal fechado  
  
-   Use o <xref:System.Drawing.Graphics.DrawClosedCurve%2A> método o <xref:System.Drawing.Graphics> classe para desenhar uma spline cardeal fechada. Em um spline cardinal fechado, a curva continua durante o último ponto na matriz e se conecta com o primeiro ponto na matriz. O exemplo a seguir desenha um spline cardinal fechado que passa por seis pontos designados. A ilustração a seguir mostra o spline fechado junto com os seis pontos.  
  
 ![Spline cardinal](../../../../docs/framework/winforms/advanced/media/cardinalspline1a.png "CardinalSpline1A")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#22)]  
  
### <a name="changing-the-bend-of-a-cardinal-spline"></a>Alterando a curva de um spline cardinal  
  
-   Alterar a maneira como um spline cardinal se dobra passando um argumento de tensão para o <xref:System.Drawing.Graphics.DrawCurve%2A> método. O exemplo a seguir desenha três splines cardinais que passam pelo mesmo conjunto de pontos. A ilustração a seguir mostra os três splines junto com seus valores de tensão. Observe que, quando a tensão for 0, os pontos são conectados por linhas retas.  
  
 ![Spline cardinal](../../../../docs/framework/winforms/advanced/media/cardinalspline2.png "CardinalSpline2")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#23)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Os exemplos anteriores são projetados para uso com o Windows Forms e eles requerem <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.  
  
## <a name="see-also"></a>Consulte também  
 [Linhas, Curvas e Formas](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Construir e Desenhar Curvas](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)
