---
title: 'Como: Desenhar uma linha preenchida com uma textura'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- lines [Windows Forms], texture
- drawing lines [Windows Forms], texture
ms.assetid: dc9118cc-f3c2-42e5-8173-f46d41d18fd5
ms.openlocfilehash: 65d830ca2d01c63288ef73b6b3a3a94f328fe32b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676231"
---
# <a name="how-to-draw-a-line-filled-with-a-texture"></a>Como: Desenhar uma linha preenchida com uma textura
Em vez de desenhar uma linha com uma cor sólida, você pode desenhar uma linha com uma textura. Para desenhar linhas e curvas com uma textura, crie uma <xref:System.Drawing.TextureBrush> do objeto e passá-lo <xref:System.Drawing.TextureBrush> do objeto para um <xref:System.Drawing.Pen.%23ctor%2A> construtor. O bitmap associado ao pincel de textura é usado para organizar lado a lado o plano (modo invisível) e quando a caneta desenha uma linha ou curva, o traço de caneta revela determinados pixels da textura lado a lado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria uma <xref:System.Drawing.Bitmap> objeto do arquivo `Texture1.jpg`. Esse bitmap é usado para construir um <xref:System.Drawing.TextureBrush> objeto e o <xref:System.Drawing.TextureBrush> objeto é usado para construir um <xref:System.Drawing.Pen> objeto. A chamada para <xref:System.Drawing.Graphics.DrawImage%2A> desenha o bitmap com seu canto superior esquerdo em (0, 0). A chamada para <xref:System.Drawing.Graphics.DrawEllipse%2A> usa o <xref:System.Drawing.Pen> objeto ao desenhar uma elipse texturizada.  
  
 A ilustração a seguir mostra o bitmap e a elipse texturizada.  
  
 ![Pens](../../../../docs/framework/winforms/advanced/media/pens7.png "pens7")  
  
 [!code-csharp[System.Drawing.UsingAPen#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.UsingAPen#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Criar um formulário do Windows e lidar com o formulário <xref:System.Windows.Forms.Control.Paint> eventos. Cole o código anterior para o <xref:System.Windows.Forms.Control.Paint> manipulador de eventos. Substitua `Texture.jpg` por uma imagem válida no sistema.  
  
## <a name="see-also"></a>Consulte também
- [Usando uma caneta para desenhar linhas e formas](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
- [Elementos Gráficos e Desenho nos Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
