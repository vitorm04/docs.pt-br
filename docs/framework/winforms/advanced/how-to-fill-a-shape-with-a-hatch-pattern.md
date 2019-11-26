---
title: Como preencher uma forma com um padrão em hachura
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- patterns [Windows Forms], adding to shapes
- shapes [Windows Forms], filling with patterns
- brushes [Windows Forms], using hatch brushes
ms.assetid: 9c8300ff-187b-404f-af1f-ebd499f5b16f
ms.openlocfilehash: b80708f0ce722b1809fe49190639231e7e4c8329
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320071"
---
# <a name="how-to-fill-a-shape-with-a-hatch-pattern"></a>Como preencher uma forma com um padrão em hachura
Um padrão de hachura é feito de duas cores: um para o plano de fundo e outro para as linhas que formam o padrão em segundo plano. Para preencher uma forma fechada com um padrão de hachura, use um objeto <xref:System.Drawing.Drawing2D.HatchBrush>. O exemplo a seguir demonstra como preencher uma elipse com um padrão de hachura:  
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
 O construtor de <xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A> usa três argumentos: o estilo de hachura, a cor da linha de hachura e a cor do plano de fundo. O argumento de estilo de hachura pode ser qualquer valor da enumeração de <xref:System.Drawing.Drawing2D.HatchStyle>. Há mais de 50 elementos na enumeração de <xref:System.Drawing.Drawing2D.HatchStyle>; alguns desses elementos são mostrados na lista a seguir:  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.Vertical>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.BackwardDiagonal>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.Cross>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.DiagonalCross>  
  
 A ilustração a seguir mostra a elipse preenchida.  
  
  ![A captura de tela do que é uma elipse preenchida com um padrão de hachura.](./media/how-to-fill-a-shape-with-a-hatch-pattern/ellipse-filled-hatch.png "hatch1")
  
 [!code-csharp[System.Drawing.UsingABrush#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.UsingABrush#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 O exemplo anterior foi projetado para uso com Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs>`e`, que é um parâmetro do manipulador de eventos de <xref:System.Windows.Forms.Control.Paint>.  
  
## <a name="see-also"></a>Consulte também

- [Usando um Pincel para Preencher Formas](using-a-brush-to-fill-shapes.md)
