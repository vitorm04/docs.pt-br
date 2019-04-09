---
title: Polígonos no GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- polygons
- drawing [Windows Forms], polygons
- GDI+, polygons
ms.assetid: a72213d2-d69a-4c2b-a75c-be7b20390c13
ms.openlocfilehash: 2b1e3d387e4d056d9187c54dcef560544206c370
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132620"
---
# <a name="polygons-in-gdi"></a>Polígonos no GDI+
Um polígono é uma forma fechada com três ou mais lados retos. Por exemplo, um triângulo é um polígono com três lados, um retângulo é um polígono com quatro lados e um Pentágono é um polígono com cinco lados. A ilustração a seguir mostra diversos polígonos.  
  
 ![Polígonos](./media/aboutgdip02-art07.gif "Aboutgdip02_art07")  
  
## <a name="drawing-a-polygon"></a>Desenhando um polígono  
 Para desenhar um polígono, é necessário um <xref:System.Drawing.Graphics> objeto, um <xref:System.Drawing.Pen> objeto e uma matriz de <xref:System.Drawing.Point> (ou <xref:System.Drawing.PointF>) objetos. O <xref:System.Drawing.Graphics> objeto fornece o <xref:System.Drawing.Graphics.DrawPolygon%2A> método. O <xref:System.Drawing.Pen> objeto armazena atributos como largura e cor da linha usada para renderizar o polígono e a matriz de <xref:System.Drawing.Point> objetos armazena os pontos a serem conectados por linhas retas. O <xref:System.Drawing.Pen> objeto e a matriz de <xref:System.Drawing.Point> objetos são passados como argumentos para o <xref:System.Drawing.Graphics.DrawPolygon%2A> método. O exemplo a seguir desenha um polígono com três lados. Observe que há apenas três pontos em `myPointArray`: (0, 0), (50, 30) e (30, 60). O <xref:System.Drawing.Graphics.DrawPolygon%2A> método fecha automaticamente o polígono desenhando uma linha de (30, 60) para o ponto de partida (0, 0).  
  
 [!code-csharp[LinesCurvesAndShapes#111](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#111)]
 [!code-vb[LinesCurvesAndShapes#111](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#111)]  
  
 A ilustração a seguir mostra o polígono.  
  
 ![Polígono](./media/aboutgdip02-art08.gif "Aboutgdip02_art08")  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- [Linhas, curvas e formas](lines-curves-and-shapes.md)
- [Como: criar uma caneta](how-to-create-a-pen.md)
