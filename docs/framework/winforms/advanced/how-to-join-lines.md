---
title: 'Como: unir linhas'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- miter line join style
- bevel line join style
- line join
- drawing [Windows Forms], joining lines
- GraphicsPath object
- round line join style
- lines [Windows Forms], joining
- graphics [Windows Forms], joining lines
ms.assetid: 9fc480c2-3c75-4fd1-8ab5-296a99e820e2
ms.openlocfilehash: 362ce0c701d6e5f640fecd143a60cf471045629c
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505871"
---
# <a name="how-to-join-lines"></a>Como: unir linhas
Uma junção de linha é a área comum que é formada por duas linhas cujas extremidades se encontram ou se sobrepõem. GDI+ fornece três estilos de junção de linha: Malhete, Bisel e redonda. Estilo da linha de junção é uma propriedade do <xref:System.Drawing.Pen> classe. Quando você especifica um estilo de junção de linha para um <xref:System.Drawing.Pen> do objeto, que o estilo de junção será aplicado a todas as linhas conectadas em qualquer <xref:System.Drawing.Drawing2D.GraphicsPath> objeto desenhado usando essa caneta.  
  
 A ilustração a seguir mostra os resultados do exemplo de junção de linha biselada.  
  
 ![Ilustração que mostra linhas unidas.](./media/how-to-join-lines/joined-beveled-lines.gif)  
  
## <a name="example"></a>Exemplo  
 Você pode especificar o estilo de junção de linha usando o <xref:System.Drawing.Pen.LineJoin%2A> propriedade do <xref:System.Drawing.Pen> classe. O exemplo demonstra uma junção de linha biselada entre uma linha horizontal e uma linha vertical. No código a seguir, o valor <xref:System.Drawing.Drawing2D.LineJoin.Bevel> atribuídas para o <xref:System.Drawing.Pen.LineJoin%2A> propriedade é um membro do <xref:System.Drawing.Drawing2D.LineJoin> enumeração. Os outros membros dos <xref:System.Drawing.Drawing2D.LineJoin> enumeração estão <xref:System.Drawing.Drawing2D.LineJoin.Miter> e <xref:System.Drawing.Drawing2D.LineJoin.Round>.  
  
 [!code-csharp[System.Drawing.UsingAPen#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingAPen#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.  
  
## <a name="see-also"></a>Consulte também

- [Usando uma caneta para desenhar linhas e formas](using-a-pen-to-draw-lines-and-shapes.md)
