---
title: "Como desenhar com pincéis opacos e semitransparentes"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- semi-transparent shapes [Windows Forms], drawing
- transparency [Windows Forms], semi-transparent shapes
- alpha blending [Windows Forms], brush
- brushes [Windows Forms], using semi-transparent
ms.assetid: a4f6f6b8-3bc8-440a-84af-d62ef0f8ff40
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6a7cae1284fbcabf70976866338ba37c6ee5710e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-with-opaque-and-semitransparent-brushes"></a>Como desenhar com pincéis opacos e semitransparentes
Quando você preencher uma forma, você deve passar um <xref:System.Drawing.Brush> objeto para um dos métodos de preenchimento a <xref:System.Drawing.Graphics> classe. Um parâmetro do <xref:System.Drawing.SolidBrush.%23ctor%2A> construtor é um <xref:System.Drawing.Color> objeto. Para preencher uma forma opaca, defina o componente alfa da cor como 255. Para preencher uma forma semitransparente, defina o componente alfa para qualquer valor de 1 a 254.  
  
 Ao preencher uma forma semitransparente, a cor da forma é combinada com as cores da tela de fundo. O componente alfa especifica como as cores da tela de fundo e da forma são misturadas; valores alfa próximos a 0 colocam mais peso nas cores da tela de fundo e valores alfabéticos próximos 255 colocam mais peso na cor da forma.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir desenha um bitmap e, em seguida, preenche três elipses que sobrepõem o bitmap. A primeira elipse usa um componente alfa de 255, portanto, é opaca. As segunda e terceira elipses usam um componente alfa de 128, para que sejam semitransparentes; É possível ver a imagem da tela de fundo pelas elipses. A chamada que define o <xref:System.Drawing.Graphics.CompositingQuality%2A> propriedade faz com que a mesclagem para a terceira elipse ser feita em conjunto com correção gama.  
  
 A seguinte ilustração mostra a saída do código a seguir.  
  
 ![Opacas e semitransparentes](../../../../docs/framework/winforms/advanced/media/compqualellipse.png "compqualellipse")  
  
 [!code-csharp[System.Drawing.AlphaBlending#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.AlphaBlending#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Consulte também  
 [Elementos Gráficos e Desenho nos Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Combinação Alfa em Linhas e Preenchimentos](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)  
 [Como dar ao controle uma tela de fundo transparente](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)  
 [Como Desenhar Linhas Opacas e Semitransparentes](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)
