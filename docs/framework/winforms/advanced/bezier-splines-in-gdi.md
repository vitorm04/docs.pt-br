---
title: Splines de Bézier no GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Bezier splines
- splines [Windows Forms], Bezier
- GDI+, Bezier splines
ms.assetid: 5774ce1e-87d4-4bc7-88c4-4862052781b8
ms.openlocfilehash: ff4e9eb18610b70c88e057d3d44020321bbb9f4f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107322"
---
# <a name="b233zier-splines-in-gdi"></a>Splines de Bézier no GDI+
Uma spline de Bézier é uma curva especificada por quatro pontos: dois pontos de extremidade (p1 e p2) e dois pontos de controle (c1 e c2). A curva começa em p1 e termina em p2. A curva não passa pelos pontos de controle, porém eles funcionam como ímãs, puxando a curva em determinadas direções e influenciando o modo de inclinação da curva. A ilustração a seguir mostra uma curva de Bézier junto com seus pontos de extremidade e de controle.  
  
 ![Splines de Bézier](./media/aboutgdip02-art11a.gif "Aboutgdip02_art11a")  
  
 A curva começa em p1 e se move para o ponto de controle c1. A linha tangente da curva em p1 é a linha desenhada de p1 a c1. A linha tangente no ponto de extremidade em p2 é a linha desenhada de c2 a p2.  
  
## <a name="drawing-bzier-splines"></a>Desenhando splines de Bézier  
 Para desenhar uma spline de Bézier, você precisa de uma instância das <xref:System.Drawing.Graphics> classe e um <xref:System.Drawing.Pen>. A instância das <xref:System.Drawing.Graphics> classe fornece a <xref:System.Drawing.Graphics.DrawBezier%2A> método e o <xref:System.Drawing.Pen> armazena atributos como largura e cor da linha usada para renderizar a curva. O <xref:System.Drawing.Pen> é passado como um dos argumentos para o <xref:System.Drawing.Graphics.DrawBezier%2A> método. Os argumentos restantes passados para o <xref:System.Drawing.Graphics.DrawBezier%2A> método são os pontos de extremidade e os pontos de controle. O exemplo a seguir desenha uma spline de Bézier com ponto inicial (0, 0), pontos de controle (40, 20) e (80, 150) e ponto final (100, 10):  
  
 [!code-csharp[LinesCurvesAndShapes#71](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#71)]
 [!code-vb[LinesCurvesAndShapes#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#71)]  
  
 A ilustração a seguir mostra a curva, os pontos de controle e duas linhas tangentes.  
  
 ![Splines de Bézier](./media/aboutgdip02-art12.gif "Aboutgdip02_art12")  
  
 As splines de Bézier foram desenvolvidos originalmente por Pierre Bézier para projetos da indústria automotiva. Desde então, elas se provaram úteis em vários tipos de projeto auxiliados por computador, sendo também usadas para definir os contornos de fontes. Splines de Bézier podem gerar uma grande variedade de formas, algumas das quais são mostradas na ilustração a seguir.  
  
 ![Demarcadores](./media/aboutgdip02-art13.gif "Aboutgdip02_art13")  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- [Linhas, curvas e formas](lines-curves-and-shapes.md)
- [Construindo e desenhando curvas](constructing-and-drawing-curves.md)
- [Como: criar objetos gráficos para desenho](how-to-create-graphics-objects-for-drawing.md)
- [Como: criar uma caneta](how-to-create-a-pen.md)
