---
title: Caminhos de elementos gráficos no GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], paths
- GDI+, drawing paths
- paths [Windows Forms], drawing
- drawing [Windows Forms], paths
ms.assetid: a5500dec-666c-41fd-9da3-2169dd89c5eb
ms.openlocfilehash: b6f0ebd500aa3503c0c0d473ebe21a61f4438862
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720417"
---
# <a name="graphics-paths-in-gdi"></a>Caminhos de elementos gráficos no GDI+
Os demarcadores são formados combinando linhas, retângulos e curvas simples. Lembre-se do [visão geral de elementos gráficos vetoriais](vector-graphics-overview.md) que os seguintes blocos de construção básicos provaram para ser mais útil para desenhar imagens:  
  
-   Linhas  
  
-   Retângulos  
  
-   Elipses  
  
-   Arcos  
  
-   Polígonos  
  
-   Splines cardinais  
  
-   Splines de Bézier  
  
 No GDI+, a <xref:System.Drawing.Drawing2D.GraphicsPath> objeto permite que você colete uma sequência desses blocos de construção em uma única unidade. Toda a sequência de linhas, retângulos, polígonos e curvas pode então ser desenhada com uma chamada para o <xref:System.Drawing.Graphics.DrawPath%2A> método da <xref:System.Drawing.Graphics> classe. A ilustração a seguir mostra um demarcador criado pela combinação de uma linha, um arco, uma spline de Bézier e uma spline cardinal.  
  
 ![Demarcador](./media/aboutgdip02-art14.gif "Aboutgdip02_art14")  
  
## <a name="using-a-path"></a>Usando um demarcador  
 O <xref:System.Drawing.Drawing2D.GraphicsPath> classe fornece os seguintes métodos para a criação de uma sequência de itens a ser desenhada: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangle%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddPolygon%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> (para splines cardinais) e <xref:System.Drawing.Drawing2D.GraphicsPath.AddBezier%2A>. Cada um desses métodos está sobrecarregado; ou seja, cada método dá suporte a diferentes listas de parâmetros. Por exemplo, uma variação do <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> método recebe quatro inteiros e outra variação de <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> método recebe dois <xref:System.Drawing.Point> objetos.  
  
 Os métodos para adicionar linhas, retângulos e splines de Bézier em um caminho tem vários métodos complementares que adicionam diversos itens para o caminho em uma única chamada: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLines%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangles%2A>, e <xref:System.Drawing.Drawing2D.GraphicsPath.AddBeziers%2A>. Além disso, o <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> e <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A> têm métodos complementares, <xref:System.Drawing.Drawing2D.GraphicsPath.AddClosedCurve%2A> e <xref:System.Drawing.Drawing2D.GraphicsPath.AddPie%2A>, que adicionam uma curva fechada ou pizza ao caminho.  
  
 Para desenhar um caminho, você precisa de uma <xref:System.Drawing.Graphics> objeto, um <xref:System.Drawing.Pen> objeto e um <xref:System.Drawing.Drawing2D.GraphicsPath> objeto. O <xref:System.Drawing.Graphics> objeto fornece os <xref:System.Drawing.Graphics.DrawPath%2A> método e o <xref:System.Drawing.Pen> objeto armazena atributos como largura e cor da linha usada para renderizar o demarcador. O <xref:System.Drawing.Drawing2D.GraphicsPath> objeto armazena a sequência de linhas e curvas que compõem o caminho. O <xref:System.Drawing.Pen> objeto e o <xref:System.Drawing.Drawing2D.GraphicsPath> objeto são passados como argumentos para o <xref:System.Drawing.Graphics.DrawPath%2A> método. O exemplo a seguir desenha um demarcador que consiste em uma linha, uma elipse e uma spline de Bézier:  
  
 [!code-csharp[LinesCurvesAndShapes#101](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#101)]
 [!code-vb[LinesCurvesAndShapes#101](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#101)]  
  
 A ilustração a seguir mostra o demarcador.  
  
 ![Demarcador](./media/aboutgdip02-art15.gif "Aboutgdip02_art15")  
  
 Além de adicionar linhas, retângulos e curvas a um demarcador, você pode adicionar demarcadores a um demarcador. Isso permite combinar os demarcadores existentes para formar demarcadores grandes e complexos.  
  
 [!code-csharp[LinesCurvesAndShapes#102](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#102)]
 [!code-vb[LinesCurvesAndShapes#102](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#102)]  
  
 Há dois outros itens que você pode adicionar a um demarcador: cadeias de caracteres e pizzas. Uma pizza é uma parte do interior de uma elipse. O exemplo a seguir cria um demarcador de um arco, uma spline cardinal, uma cadeia de caracteres e uma pizza:  
  
 [!code-csharp[LinesCurvesAndShapes#103](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#103)]
 [!code-vb[LinesCurvesAndShapes#103](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#103)]  
  
 A ilustração a seguir mostra o demarcador. Observe que um demarcador não precisa estar conectado; o arco, spline cardinal, cadeia de caracteres e pizza são separados.  
  
 ![Demarcadores](./media/aboutgdip02-art16.gif "Aboutgdip02_Art16")  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>
- <xref:System.Drawing.Point?displayProperty=nameWithType>
- [Linhas, Curvas e Formas](lines-curves-and-shapes.md)
- [Como: Criar objetos gráficos para desenho](how-to-create-graphics-objects-for-drawing.md)
- [Construindo e desenhando demarcadores](constructing-and-drawing-paths.md)
