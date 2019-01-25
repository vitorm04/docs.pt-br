---
title: Elipses e arcos no GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- arcs
- GDI+, arcs
- drawing [Windows Forms], ellipses
- GDI+, ellipses
- ellipses
- drawing [Windows Forms], arcs
ms.assetid: 34f35133-a835-4ca4-81f6-0dfedee8b683
ms.openlocfilehash: 93f82d35449c42772e9fbd1b7454364885b38769
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54697199"
---
# <a name="ellipses-and-arcs-in-gdi"></a>Elipses e arcos no GDI+
É possível desenhar facilmente elipses e arcos usando o <xref:System.Drawing.Graphics.DrawEllipse%2A> e <xref:System.Drawing.Graphics.DrawArc%2A> métodos do <xref:System.Drawing.Graphics> classe.  
  
## <a name="drawing-an-ellipse"></a>Desenhando uma elipse  
 Para desenhar uma elipse, é necessário um <xref:System.Drawing.Graphics> objeto e um <xref:System.Drawing.Pen> objeto. O <xref:System.Drawing.Graphics> objeto fornece os <xref:System.Drawing.Graphics.DrawEllipse%2A> método e o <xref:System.Drawing.Pen> objeto armazena atributos como largura e cor da linha usada para renderizar a elipse. O <xref:System.Drawing.Pen> objeto é passado como um dos argumentos para o <xref:System.Drawing.Graphics.DrawEllipse%2A> método. Os argumentos restantes passados para o <xref:System.Drawing.Graphics.DrawEllipse%2A> método especificam o retângulo delimitador para a elipse. A ilustração a seguir mostra uma elipse junto a seu retângulo delimitador.  
  
 ![Elipses e arcos](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art05.gif "Aboutgdip02_art05")  
  
 O exemplo a seguir desenha uma elipse; o retângulo delimitador tem uma largura de 80, uma altura de 40 e um canto superior esquerdo de (100, 50):  
  
 [!code-csharp[LinesCurvesAndShapes#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#51)]
 [!code-vb[LinesCurvesAndShapes#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#51)]  
  
 <xref:System.Drawing.Graphics.DrawEllipse%2A> é um método sobrecarregado do <xref:System.Drawing.Graphics> de classe, portanto, há várias maneiras que você pode fornecer argumentos. Por exemplo, você pode construir uma <xref:System.Drawing.Rectangle> e passe a <xref:System.Drawing.Rectangle> para o <xref:System.Drawing.Graphics.DrawEllipse%2A> método como um argumento:  
  
 [!code-csharp[LinesCurvesAndShapes#52](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#52)]
 [!code-vb[LinesCurvesAndShapes#52](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#52)]  
  
## <a name="drawing-an-arc"></a>Desenhando um arco  
 Um arco é uma parte de uma elipse. Para desenhar um arco, você chama o <xref:System.Drawing.Graphics.DrawArc%2A> método da <xref:System.Drawing.Graphics> classe. Os parâmetros do <xref:System.Drawing.Graphics.DrawArc%2A> método são os mesmos que os parâmetros das <xref:System.Drawing.Graphics.DrawEllipse%2A> método, exceto que <xref:System.Drawing.Graphics.DrawArc%2A> requer um ângulo inicial e ângulo de flecha. O exemplo a seguir desenha um arco com um ângulo inicial de 30 graus e um ângulo de flecha de 180 graus:  
  
 [!code-csharp[LinesCurvesAndShapes#53](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#53)]
 [!code-vb[LinesCurvesAndShapes#53](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#53)]  
  
 A ilustração a seguir mostra o arco, a elipse e o retângulo delimitador.  
  
 ![Elipses e arcos](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art06.gif "Aboutgdip02_art06")  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- [Linhas, Curvas e Formas](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)
- [Como: Criar objetos gráficos para desenho](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)
- [Como: Criar uma caneta](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)
- [Como: Desenhar uma forma delineada](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)
