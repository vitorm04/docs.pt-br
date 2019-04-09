---
title: 'Como: desenhar uma linha com terminações'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
- drawing lines [Windows Forms], line caps
ms.assetid: eb68c3e1-c400-4886-8a04-76978a429cb6
ms.openlocfilehash: c4a78569f6c0b14c32154611412d6b3ccd8a84ce
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59146205"
---
# <a name="how-to-draw-a-line-with-line-caps"></a>Como: desenhar uma linha com terminações
Você pode desenhar o início ou término de uma linha em uma das várias formas chamadas terminações de linha. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] dá suporte a várias terminações de linha, como round, quadrado, losango e ponta de seta.  
  
## <a name="example"></a>Exemplo  
 Você pode especificar as terminações de linha para o início de uma linha (início cap), a fim de uma linha (limite de extremidade) ou os traços de uma linha tracejada (limite do traço).  
  
 O exemplo a seguir desenha uma linha com uma ponta de seta em uma extremidade e uma extremidade redonda na outra extremidade. A ilustração mostra a linha resultante:  
  
 ![Ilustração que mostra uma linha com uma extremidade arredondada.](./media/how-to-draw-a-line-with-line-caps/line-cap-arrowhead-example.gif)  
  
 [!code-csharp[System.Drawing.UsingAPen#71](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.UsingAPen#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
-   Criar um formulário do Windows e lidar com o formulário <xref:System.Windows.Forms.Control.Paint> eventos. Cole o código de exemplo para o <xref:System.Windows.Forms.Control.Paint> manipulador de eventos passando `e` como <xref:System.Windows.Forms.PaintEventArgs>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.LineCap?displayProperty=nameWithType>
- [Elementos gráficos e desenho no Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Usando uma caneta para desenhar linhas e formas](using-a-pen-to-draw-lines-and-shapes.md)
