---
title: Visão geral de gráficos vetoriais
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inclusive-inclusive endpoints
- coordinate systems
- graphics [Windows Forms], vector graphics
ms.assetid: 0195df81-66be-452d-bb53-5a582ebfdc09
ms.openlocfilehash: d424254839db6c403bafe779f475c0e344918a5e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59087957"
---
# <a name="vector-graphics-overview"></a>Visão geral de gráficos vetoriais
O [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] desenha linhas, retângulos e outras formas em um sistema de coordenadas. Você pode escolher entre uma variedade de sistemas de coordenadas, mas o sistema de coordenadas padrão tem origem no canto superior esquerdo, com o eixo x apontando para a direita e o eixo y apontando para baixo. A unidade de medida no sistema de coordenadas padrão é o pixel.  
  
## <a name="the-building-blocks-of-gdi"></a>Os blocos de construção da GDI+  
 ![Gráfico vetorial](./media/aboutgdip02-art01.gif "AboutGdip02_Art01")  
  
 Um monitor de computador cria sua exibição em uma matriz retangular de pontos chamados de elementos de imagem ou pixels. O número de pixels que aparecem na tela varia de um monitor para outro e o número de pixels que aparecem em um monitor individual normalmente pode ser configurado em alguma medida pelo usuário.  
  
 ![Gráfico vetorial](./media/aboutgdip02-art02.gif "AboutGdip02_Art02")  
  
 Quando você usa [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] para desenhar uma linha, um retângulo ou uma curva, fornece determinadas informações importantes sobre o item a ser desenhado. Por exemplo, você pode especificar uma linha fornecendo dois pontos e especificar um retângulo fornecendo um ponto, uma altura e uma largura. O [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] funciona em conjunto com o software de driver de vídeo para determinar quais pixels devem ser ativados para mostrar a linha, o retângulo ou a curva. A ilustração a seguir mostra os pixels que são ativados para exibir uma linha do ponto (4, 2) ao ponto (12, 8).  
  
 ![Gráfico vetorial](./media/aboutgdip02-art03.gif "AboutGdip02_Art03")  
  
 Ao longo do tempo, determinados blocos de construção básicos mostraram ser mais úteis para criar imagens bidimensionais. Esses blocos de construção, que têm suporte no [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], são apresentados na lista a seguir:  
  
-   Linhas  
  
-   Retângulos  
  
-   Elipses  
  
-   Arcos  
  
-   Polígonos  
  
-   Splines cardinais  
  
-   splines de Bézier  
  
## <a name="methods-for-drawing-with-a-graphics-object"></a>Métodos para desenhar com um objeto gráfico  
 O <xref:System.Drawing.Graphics> classe [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] fornece os seguintes métodos para desenhar os itens na lista anterior: <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawRectangle%2A>, <xref:System.Drawing.Graphics.DrawEllipse%2A>, <xref:System.Drawing.Graphics.DrawPolygon%2A>, <xref:System.Drawing.Graphics.DrawArc%2A>, <xref:System.Drawing.Graphics.DrawCurve%2A> (para splines cardinais) e <xref:System.Drawing.Graphics.DrawBezier%2A>. Cada um desses métodos está sobrecarregado; ou seja, cada método dá suporte a diferentes listas de parâmetros. Por exemplo, uma variação do <xref:System.Drawing.Graphics.DrawLine%2A> método recebe um <xref:System.Drawing.Pen> objeto e quatro inteiros, enquanto outra variação do <xref:System.Drawing.Graphics.DrawLine%2A> método recebe um <xref:System.Drawing.Pen> objeto e dois <xref:System.Drawing.Point> objetos.  
  
 Os métodos para desenhar linhas, retângulos e splines de Bézier têm vários métodos complementares que desenham diversos itens em uma única chamada: <xref:System.Drawing.Graphics.DrawLines%2A>, <xref:System.Drawing.Graphics.DrawRectangles%2A>, e <xref:System.Drawing.Graphics.DrawBeziers%2A>. Além disso, o <xref:System.Drawing.Graphics.DrawCurve%2A> método tem um método correspondente, <xref:System.Drawing.Graphics.DrawClosedCurve%2A>, que fecha uma curva conectando o ponto final da curva a partir do ponto.  
  
 Todos os métodos de desenho a <xref:System.Drawing.Graphics> classe trabalham em conjunto com um <xref:System.Drawing.Pen> objeto. Para desenhar qualquer coisa, você deve criar pelo menos dois objetos: uma <xref:System.Drawing.Graphics> objeto e um <xref:System.Drawing.Pen> objeto. O <xref:System.Drawing.Pen> objeto armazena atributos como largura e cor do item a ser desenhado. O <xref:System.Drawing.Pen> objeto é passado como um dos argumentos para o método de desenho. Por exemplo, uma variação do <xref:System.Drawing.Graphics.DrawLine%2A> método recebe um <xref:System.Drawing.Pen> objeto e quatro inteiros, conforme mostrado no exemplo a seguir, que desenha um retângulo com uma largura de 100, uma altura de 50 e um canto superior esquerdo de (10, 20):  
  
 [!code-csharp[LinesCurvesAndShapes#11](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#11)]
 [!code-vb[LinesCurvesAndShapes#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#11)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- [Linhas, Curvas e Formas](lines-curves-and-shapes.md)
- [Como: Criar objetos gráficos para desenho](how-to-create-graphics-objects-for-drawing.md)
