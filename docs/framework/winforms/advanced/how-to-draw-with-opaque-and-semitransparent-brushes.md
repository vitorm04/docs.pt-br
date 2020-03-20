---
title: Como desenhar com pincéis opacos e semitransparentes
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
ms.openlocfilehash: 1e48bbd563f6377380848949325962b568fa432c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142401"
---
# <a name="how-to-draw-with-opaque-and-semitransparent-brushes"></a>Como desenhar com pincéis opacos e semitransparentes
Quando você preenche uma forma, <xref:System.Drawing.Brush> você deve passar um objeto <xref:System.Drawing.Graphics> para um dos métodos de preenchimento da classe. O único parâmetro <xref:System.Drawing.SolidBrush.%23ctor%2A> do construtor <xref:System.Drawing.Color> é um objeto. Para preencher uma forma opaca, defina o componente alfa da cor como 255. Para preencher uma forma semitransparente, defina o componente alfa para qualquer valor de 1 a 254.  
  
 Ao preencher uma forma semitransparente, a cor da forma é combinada com as cores da tela de fundo. O componente alfa especifica como as cores da tela de fundo e da forma são misturadas; valores alfa próximos a 0 colocam mais peso nas cores da tela de fundo e valores alfabéticos próximos 255 colocam mais peso na cor da forma.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir desenha um bitmap e, em seguida, preenche três elipses que sobrepõem o bitmap. A primeira elipse usa um componente alfa de 255, portanto, é opaca. As segunda e terceira elipses usam um componente alfa de 128, para que sejam semitransparentes; É possível ver a imagem da tela de fundo pelas elipses. A chamada que <xref:System.Drawing.Graphics.CompositingQuality%2A> define a propriedade faz com que a mistura para a terceira elipse seja feita em conjunto com a correção gama.  

 [!code-csharp[System.Drawing.AlphaBlending#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.AlphaBlending#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#31)]  

 A ilustração a seguir mostra a saída do seguinte código:
  
 ![Ilustração que mostra saída opaca e semitransparente.](./media/how-to-draw-with-opaque-and-semitransparent-brushes/compositingquality-ellipse-semitransparent.png)  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior foi projetado para ser <xref:System.Windows.Forms.PaintEventArgs> `e`usado com formulários <xref:System.Windows.Forms.PaintEventHandler>do Windows, e requer , que é um parâmetro de .  
  
## <a name="see-also"></a>Confira também

- [Elementos gráficos e desenho no Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Combinação Alfa em Linhas e Preenchimentos](alpha-blending-lines-and-fills.md)
- [Como dar ao controle um plano de fundo transparente](../controls/how-to-give-your-control-a-transparent-background.md)
- [Como desenhar linhas opacas e semitransparentes](how-to-draw-opaque-and-semitransparent-lines.md)
