---
title: Como usar uma matriz de cores para definir valores alfa em imagens
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], using color matrices for semi-transparent
- transparency [Windows Forms], color matrices
- matrices [Windows Forms], alpha values
- bitmaps [Windows Forms], using color matrices for semi-transparent
ms.assetid: a27121e6-f7e9-4c09-84e2-f05aa9d2a1bb
ms.openlocfilehash: 73e820845d040856a0ae367da8b9371ad6afa142
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423728"
---
# <a name="how-to-use-a-color-matrix-to-set-alpha-values-in-images"></a>Como usar uma matriz de cores para definir valores alfa em imagens
A classe <xref:System.Drawing.Bitmap> (que herda da classe <xref:System.Drawing.Image>) e a classe <xref:System.Drawing.Imaging.ImageAttributes> fornecem funcionalidade para obter e definir valores de pixel. Você pode usar a classe <xref:System.Drawing.Imaging.ImageAttributes> para modificar os valores Alfa de uma imagem inteira ou pode chamar o método <xref:System.Drawing.Bitmap.SetPixel%2A> da classe <xref:System.Drawing.Bitmap> para modificar valores de pixel individuais.  
  
## <a name="example"></a>Exemplo  
 A classe <xref:System.Drawing.Imaging.ImageAttributes> tem muitas propriedades que você pode usar para modificar imagens durante a renderização. No exemplo a seguir, um objeto <xref:System.Drawing.Imaging.ImageAttributes> é usado para definir todos os valores alfa como 80% do que eles eram. Isso é feito inicializando uma matriz de cores e configurando o valor de escala alfa na matriz para 0,8. O endereço da matriz de cores é passado para o método <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> do objeto <xref:System.Drawing.Imaging.ImageAttributes> e o objeto <xref:System.Drawing.Imaging.ImageAttributes> é passado para o método <xref:System.Drawing.Graphics.DrawString%2A> do objeto <xref:System.Drawing.Graphics>.  
  
 Durante o processamento, os valores alfa no bitmap são convertidos em 80 por cento do que eram. Isso resulta em uma imagem que é combinada com a tela de fundo. Como mostra a ilustração a seguir, a imagem de bitmap é transparente; é possível ver a linha preta sólida através dela.  
  
 ![Captura de tela de mesclagem alfa usando uma matriz.](./media/how-to-use-a-color-matrix-to-set-alpha-values-in-images/alpha-blending-matrix.png "image2")  
  
 Nos pontos em que a imagem está sobre a parte branca da tela de fundo, ela é combinada com a cor branca. Nos pontos em que imagem cruza a linha preta, ela é combinada a cor preta.  
  
 [!code-csharp[System.Drawing.AlphaBlending#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.AlphaBlending#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 O exemplo anterior foi projetado para uso com Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Consulte também

- [Elementos Gráficos e Desenho nos Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Combinação alfa em linhas e preenchimentos](alpha-blending-lines-and-fills.md)
