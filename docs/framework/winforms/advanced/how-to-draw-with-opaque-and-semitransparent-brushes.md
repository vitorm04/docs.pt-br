---
title: 'Como: desenhar com pincéis opacos e semitransparentes'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- semi-transparent shapes [Windows Forms], drawing
- transparency [Windows Forms], semi-transparent shapes
- alpha blending [Windows Forms], brush
- brushes [Windows Forms], using semi-transparent
ms.assetid: a4f6f6b8-3bc8-440a-84af-d62ef0f8ff40
ms.openlocfilehash: a302b8bf978afcead5768fadeb6336c1ece986ec
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59100906"
---
# <a name="how-to-draw-with-opaque-and-semitransparent-brushes"></a>Como: desenhar com pincéis opacos e semitransparentes
Ao preencher uma forma, você deve passar uma <xref:System.Drawing.Brush> objeto para um dos métodos de preenchimento do <xref:System.Drawing.Graphics> classe. O parâmetro do construtor de <xref:System.Drawing.SolidBrush.%23ctor%2A> construtor é um <xref:System.Drawing.Color> objeto. Para preencher uma forma opaca, defina o componente alfa da cor como 255. Para preencher uma forma semitransparente, defina o componente alfa para qualquer valor de 1 a 254.  
  
 Ao preencher uma forma semitransparente, a cor da forma é combinada com as cores da tela de fundo. O componente alfa especifica como as cores da tela de fundo e da forma são misturadas; valores alfa próximos a 0 colocam mais peso nas cores da tela de fundo e valores alfabéticos próximos 255 colocam mais peso na cor da forma.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir desenha um bitmap e, em seguida, preenche três elipses que sobrepõem o bitmap. A primeira elipse usa um componente alfa de 255, portanto, é opaca. As segunda e terceira elipses usam um componente alfa de 128, para que sejam semitransparentes; É possível ver a imagem da tela de fundo pelas elipses. A chamada que define o <xref:System.Drawing.Graphics.CompositingQuality%2A> propriedade faz com que a combinação da terceira elipse seja feita em conjunto com a correção gama.  

 [!code-csharp[System.Drawing.AlphaBlending#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.AlphaBlending#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#31)]  

 A ilustração a seguir mostra a saída do código a seguir: 
  
 ![Ilustração que mostra a saída opaca e semitransparente.](./media/how-to-draw-with-opaque-and-semitransparent-brushes/compositingquality-ellipse-semitransparent.png)  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Consulte também

- [Elementos Gráficos e Desenho nos Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Combinação Alfa em Linhas e Preenchimentos](alpha-blending-lines-and-fills.md)
- [Como: Dar ao controle uma tela de fundo transparente](../controls/how-to-give-your-control-a-transparent-background.md)
- [Como: Desenhar linhas opacas e semitransparentes](how-to-draw-opaque-and-semitransparent-lines.md)
