---
title: 'Como: desenhar linhas opacas e semitransparentes'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- transparency [Windows Forms], lines
- lines [Windows Forms], drawing alpha blended
- alpha blending [Windows Forms], drawing lines
ms.assetid: 8f2508af-f495-4223-b5cc-646cbbb520eb
ms.openlocfilehash: 7408722dc13e83828cfca3f0615a2730e3c53461
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59188260"
---
# <a name="how-to-draw-opaque-and-semitransparent-lines"></a>Como: desenhar linhas opacas e semitransparentes
Quando você desenha uma linha, você deve passar uma <xref:System.Drawing.Pen> do objeto para o <xref:System.Drawing.Graphics.DrawLine%2A> método da <xref:System.Drawing.Graphics> classe. Um dos parâmetros do <xref:System.Drawing.Pen.%23ctor%2A> construtor é um <xref:System.Drawing.Color> objeto. Para desenhar uma linha opaca, defina o componente alfa da cor como 255. Para desenhar uma linha semitransparente, defina o componente alfa para qualquer valor de 1 a 254.  
  
 Ao desenhar uma linha semitransparente em uma tela de fundo, a cor da linha é combinada com as cores da tela de fundo. O componente alfa especifica como as cores da tela de fundo e da linha são misturadas; valores alfa próximos a 0 colocam mais peso nas cores da tela de fundo e valores alfa próximos a 255 colocam mais peso na cor da linha.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir desenha um bitmap e, em seguida, desenha três linhas que usam o bitmap como tela de fundo. A primeira linha usa um componente alfa de 255, portanto, é opaca. As segunda e terceira linhas usam um componente alfa de 128, para que sejam semitransparentes. É possível ver a imagem da tela de fundo pelas linhas. A instrução que define o <xref:System.Drawing.Graphics.CompositingQuality%2A> propriedade faz com que a mesclagem da terceira linha a ser feito em conjunto com a correção gama.  
  
 [!code-csharp[System.Drawing.AlphaBlending#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.AlphaBlending#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#11)]  
  
 A ilustração a seguir mostra a saída do código a seguir:  
  
 ![Ilustração que mostra a saída opaca e semitransparente](./media/how-to-draw-opaque-and-semitransparent-lines/opaque-semitransparent-lines.png)  

## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs>`e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.  
  
## <a name="see-also"></a>Consulte também

- [Combinação alfa em linhas e preenchimentos](alpha-blending-lines-and-fills.md)
- [Como: Dar ao controle um segundo plano transparente](../controls/how-to-give-your-control-a-transparent-background.md)
- [Como: desenhar com pincéis opacos e semitransparentes](how-to-draw-with-opaque-and-semitransparent-brushes.md)
