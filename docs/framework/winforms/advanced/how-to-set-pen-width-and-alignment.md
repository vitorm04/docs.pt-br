---
title: 'Como: definir a largura e o alinhamento de uma caneta'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pens [Windows Forms], setting width
- pens [Windows Forms], setting alignment
ms.assetid: a202af36-4d31-4401-a126-b232f51db581
ms.openlocfilehash: bc2ac2587554215ef3b2c2580413fbbb894aa687
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074970"
---
# <a name="how-to-set-pen-width-and-alignment"></a>Como: definir a largura e o alinhamento de uma caneta
Quando você cria um <xref:System.Drawing.Pen>, você pode fornecer a largura da caneta como um dos argumentos para o construtor. Você também pode alterar a largura da caneta com a <xref:System.Drawing.Pen.Width%2A> propriedade do <xref:System.Drawing.Pen> classe.  
  
 Uma linha teórica tem uma largura de 0. Quando você desenha uma linha com um pixel de largura, os pixels são centralizados na linha teórica. Se você desenhar uma linha contendo mais de um pixel de largura, os pixels serão centralizados na linha teórica ou aparecerão em um dos lados da linha teórica. Você pode definir a propriedade de alinhamento da caneta de um <xref:System.Drawing.Pen> para determinar como os pixels desenhados com essa caneta serão posicionados em relação ao linhas teóricas.  
  
 Os valores <xref:System.Drawing.Drawing2D.PenAlignment.Center>, <xref:System.Drawing.Drawing2D.PenAlignment.Outset>, e <xref:System.Drawing.Drawing2D.PenAlignment.Inset> que aparecem nas seguintes exemplos de código são membros do <xref:System.Drawing.Drawing2D.PenAlignment> enumeração.  
  
 O exemplo de código a seguir desenha uma linha duas vezes: uma vez com uma caneta preta da largura 1 e uma vez com uma caneta verde da largura 10.  
  
### <a name="to-vary-the-width-of-a-pen"></a>Variar a largura da caneta  
  
-   Defina o valor da <xref:System.Drawing.Pen.Alignment%2A> propriedade para <xref:System.Drawing.Drawing2D.PenAlignment.Center> (o padrão) para especificar que os pixels desenhados com a caneta verde serão centralizados na linha teórica. A ilustração a seguir mostra a linha resultante.  
  
     ![Uma linha preta fina com realce verde.](./media/how-to-set-pen-width-and-alignment/green-pixels-centered-line.gif)  
  
     O exemplo de código a seguir desenha um retângulo duas vezes: uma vez com uma caneta preta da largura 1 e uma vez com uma caneta verde da largura 10.  
  
     [!code-csharp[System.Drawing.UsingAPen#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#41)]
     [!code-vb[System.Drawing.UsingAPen#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#41)]  
  
### <a name="to-change-the-alignment-of-a-pen"></a>Alterar o alinhamento de uma caneta  
  
-   Defina o valor da <xref:System.Drawing.Pen.Alignment%2A> propriedade para <xref:System.Drawing.Drawing2D.PenAlignment.Center> para especificar que os pixels desenhados com a caneta verde serão centralizados no limite do retângulo.  
  
     A ilustração a seguir mostra o retângulo resultante:
  
     ![Um retângulo desenhado com linhas finas pretas com realce verde.](./media/how-to-set-pen-width-and-alignment/green-pixels-centered-rectangle.gif)  
  
     [!code-csharp[System.Drawing.UsingAPen#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#42)]
     [!code-vb[System.Drawing.UsingAPen#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#42)]  
  
### <a name="to-create-an-inset-pen"></a>Criar uma caneta de baixo-relevo  
  
-   Altere o alinhamento da caneta verde modificando a terceira instrução no exemplo de código anterior da seguinte maneira:  
  
     [!code-csharp[System.Drawing.UsingAPen#43](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#43)]
     [!code-vb[System.Drawing.UsingAPen#43](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#43)]  
  
     Agora os pixels na linha verde larga aparecem no interior do retângulo conforme mostrado na ilustração a seguir:
  
     ![Um retângulo desenhado com linhas pretas com a linha verde larga dentro.](./media/how-to-set-pen-width-and-alignment/green-pixels-inside-rectangle.gif)  
  
## <a name="see-also"></a>Consulte também

- [Usando uma caneta para desenhar linhas e formas](using-a-pen-to-draw-lines-and-shapes.md)
- [Elementos Gráficos e Desenho nos Windows Forms](graphics-and-drawing-in-windows-forms.md)
