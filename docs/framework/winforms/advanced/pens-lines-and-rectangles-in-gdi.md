---
title: Canetas, linhas e retângulos no GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines
- GDI+, lines
- drawing [Windows Forms], rectangles
- rectangles
- drawing [Windows Forms], lines
- GDI+, pens
- examples [Windows Forms], drawing lines and shapes
- examples [Windows Forms], pens
- GDI+, rectangles
- examples [Windows Forms], GDI+
- lines [Windows Forms], dashed
ms.assetid: 30b25aae-e3eb-4479-bdb8-187cf651fc84
ms.openlocfilehash: 84752773c0b56d9684dc31620d463d4ddccf9dad
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078220"
---
# <a name="pens-lines-and-rectangles-in-gdi"></a>Canetas, linhas e retângulos no GDI+
Para desenhar linhas com [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] você precisa criar um <xref:System.Drawing.Graphics> objeto e um <xref:System.Drawing.Pen> objeto. O <xref:System.Drawing.Graphics> objeto fornece os métodos que realmente fazem o desenho, e o <xref:System.Drawing.Pen> objeto armazena atributos, como cor da linha, largura e estilo.  
  
## <a name="drawing-a-line"></a>Desenhar uma Linha  
 Para desenhar uma linha, chame o <xref:System.Drawing.Graphics.DrawLine%2A> método da <xref:System.Drawing.Graphics> objeto. O <xref:System.Drawing.Pen> objeto é passado como um dos argumentos para o <xref:System.Drawing.Graphics.DrawLine%2A> método. O exemplo a seguir desenha uma linha do ponto (4, 2) ao ponto (12, 6):  
  
 [!code-csharp[LinesCurvesAndShapes#41](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#41)]
 [!code-vb[LinesCurvesAndShapes#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#41)]  
  
 <xref:System.Drawing.Graphics.DrawLine%2A> é um método sobrecarregado do <xref:System.Drawing.Graphics> de classe, portanto, há várias maneiras que você pode fornecer argumentos. Por exemplo, você pode construir dois <xref:System.Drawing.Point> objetos e passe a <xref:System.Drawing.Point> objetos como argumentos para o <xref:System.Drawing.Graphics.DrawLine%2A> método:  
  
 [!code-csharp[LinesCurvesAndShapes#42](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#42)]
 [!code-vb[LinesCurvesAndShapes#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#42)]  
  
## <a name="constructing-a-pen"></a>Construir uma Caneta  
 Você pode especificar determinados atributos ao construir um <xref:System.Drawing.Pen> objeto. Por exemplo, um construtor `Pen` permite especificar a cor e a largura. O exemplo a seguir desenha uma linha azul de largura 2 de (0, 0) a (60, 30):  
  
 [!code-csharp[LinesCurvesAndShapes#43](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#43)]
 [!code-vb[LinesCurvesAndShapes#43](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#43)]  
  
## <a name="dashed-lines-and-line-caps"></a>Linhas Tracejadas e Terminações de Linha  
 O <xref:System.Drawing.Pen> também expões propriedades, tais como <xref:System.Drawing.Pen.DashStyle%2A>, que você pode usar para especificar os recursos da linha. O exemplo a seguir desenha uma linha tracejada de (100, 50) a (300, 80):  
  
 [!code-csharp[LinesCurvesAndShapes#44](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#44)]
 [!code-vb[LinesCurvesAndShapes#44](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#44)]  
  
 Você pode usar as propriedades do <xref:System.Drawing.Pen> objeto para definir muitos mais atributos da linha. O <xref:System.Drawing.Pen.StartCap%2A> e <xref:System.Drawing.Pen.EndCap%2A> propriedades especificam a aparência das extremidades da linha; as extremidades podem ser simples, quadradas, arredondadas, triangulares ou uma forma personalizada. O <xref:System.Drawing.Pen.LineJoin%2A> propriedade permite que você especifique se linhas conectadas estão em Malhete (unidas com cantos), biseladas, arredondadas ou recortadas. A ilustração a seguir mostra linhas com vários estilos de extremidade e junção.  
  
 ![Lines](./media/aboutgdip02-art04.gif "Aboutgdip02_art04")  
  
## <a name="drawing-a-rectangle"></a>Desenhar um Retângulo  
 Desenhar retângulos com [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] é semelhante a desenhar linhas. Para desenhar um retângulo, você precisa de uma <xref:System.Drawing.Graphics> objeto e um <xref:System.Drawing.Pen> objeto. O <xref:System.Drawing.Graphics> objeto fornece uma <xref:System.Drawing.Graphics.DrawRectangle%2A> método e o <xref:System.Drawing.Pen> objeto armazena atributos, como cor e largura da linha. O <xref:System.Drawing.Pen> objeto é passado como um dos argumentos para o <xref:System.Drawing.Graphics.DrawRectangle%2A> método. O exemplo a seguir desenha um retângulo com seu canto superior esquerdo em (100, 50), uma largura de 80 e altura de 40:  
  
 [!code-csharp[LinesCurvesAndShapes#45](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#45)]
 [!code-vb[LinesCurvesAndShapes#45](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#45)]  
  
 <xref:System.Drawing.Graphics.DrawRectangle%2A> é um método sobrecarregado do <xref:System.Drawing.Graphics> de classe, portanto, há várias maneiras que você pode fornecer argumentos. Por exemplo, você pode construir uma <xref:System.Drawing.Rectangle> do objeto e passe a <xref:System.Drawing.Rectangle> do objeto para o <xref:System.Drawing.Graphics.DrawRectangle%2A> método como um argumento:  
  
 [!code-csharp[LinesCurvesAndShapes#46](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#46)]
 [!code-vb[LinesCurvesAndShapes#46](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#46)]  
  
 Um <xref:System.Drawing.Rectangle> objeto tem métodos e propriedades para manipular e coletar informações sobre o retângulo. Por exemplo, o <xref:System.Drawing.Rectangle.Inflate%2A> e <xref:System.Drawing.Rectangle.Offset%2A> os métodos de alterar o tamanho e posição do retângulo. O <xref:System.Drawing.Rectangle.IntersectsWith%2A> método informa se o retângulo intersecciona outro dado retângulo e o <xref:System.Drawing.Rectangle.Contains%2A> método informa se um determinado ponto está dentro do retângulo.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- <xref:System.Drawing.Rectangle?displayProperty=nameWithType>
- [Como: criar uma caneta](how-to-create-a-pen.md)
- [Como: desenhar uma linha em um formulário do Windows](how-to-draw-a-line-on-a-windows-form.md)
- [Como: desenhar uma forma delineada](how-to-draw-an-outlined-shape.md)
