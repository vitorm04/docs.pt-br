---
title: Splines cardinais no GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- splines [Windows Forms], cardinal
- GDI+, cardinal splines
- cardinal splines
ms.assetid: 09b3797a-6294-422d-9adf-a5a0a7695c0c
ms.openlocfilehash: f7d04f59e2424b71eb5bd0015f9496e6e67edbfa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589526"
---
# <a name="cardinal-splines-in-gdi"></a>Splines cardinais no GDI+
Um spline cardinal é uma sequência de curvas individuais unidas para formar uma curva maior. O spline é especificado por uma matriz de pontos e um parâmetro de tensão. Um spline cardinal passa suavemente pelos pontos na matriz. Não há cantos agudos nem mudanças abruptas na inclinação da curva. A ilustração a seguir mostra um conjunto de pontos e um spline cardinal que passa pelos pontos no conjunto.  
  
 ![Spline Cardinal](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art09.gif "Aboutgdip02_art09")  
  
## <a name="physical-and-mathematical-splines"></a>Splines físicos e matemáticos  
 Um spline físico é uma peça fina de madeira ou outro material flexível. Antes do advento do splines matemáticos, os designers usavam splines físicos para desenhar curvas. O designer colocava o spline em um pedaço de papel e ancorava-o em um determinado conjunto de pontos. Então o designer podia criar uma curva desenhando ao longo do spline com uma caneta ou um lápis. Um determinado conjunto de pontos podia produzir uma variedade de curvas, dependendo das propriedades do spline físico. Por exemplo, um spline com uma alta resistência à curvatura geraria uma curva diferente daquela de um spline extremamente flexível.  
  
 As fórmulas para splines matemáticos são baseadas nas propriedades de barras flexíveis, portanto, as curvas produzidas por splines matemáticos são semelhantes às curvas antes produzidas por splines físicos. Assim como splines físicos de tensão diferente produzirão curvas diferentes em um determinado conjunto de pontos, splines matemáticos com valores diferentes para o parâmetro de tensão produzirão curvas diferentes em um determinado conjunto de pontos. A ilustração a seguir mostra quatro splines cardinais passando pelo mesmo conjunto de pontos. A tensão é mostrada para cada spline. Uma tensão de 0 corresponde à tensão física infinita, forçando a curva a seguir o caminho mais curto (linhas retas) entre os pontos. Uma tensão de 1 corresponde à ausência de tensão física, permitindo que o spline siga o caminho de menor curvatura total. Com valores de tensão superiores a 1, a curva comporta-se como uma mola comprimida, pressionada para seguir um caminho mais longo.  
  
 ![Splines cardinais](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art10.gif "Aboutgdip02_art10")  
  
 Os quatro splines na ilustração anterior compartilham a mesma linha tangente no ponto de partida. A tangente é a linha desenhada do ponto de partida até o próximo seguinte ao longo da curva. Da mesma forma, a tangente compartilhada no ponto final é a linha desenhada do ponto final até o ponto anterior na curva.  
  
 Para desenhar um spline cardinal, você precisa de uma instância do <xref:System.Drawing.Graphics> classe, uma <xref:System.Drawing.Pen>e uma matriz de <xref:System.Drawing.Point> objetos da instância das <xref:System.Drawing.Graphics> classe fornece a <xref:System.Drawing.Graphics.DrawCurve%2A> método, que desenha o spline, e o <xref:System.Drawing.Pen> armazena os atributos do spline, como cor e largura da linha. A matriz de <xref:System.Drawing.Point> objetos armazena os pontos que a curva atravessará. O exemplo de código a seguir mostra como desenhar um spline cardinal que passa pelos pontos no `myPointArray`. O terceiro parâmetro é a tensão.  
  
 [!code-csharp[LinesCurvesAndShapes#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#31)]
 [!code-vb[LinesCurvesAndShapes#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>Consulte também
- [Linhas, Curvas e Formas](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)
- [Construir e Desenhar Curvas](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)
