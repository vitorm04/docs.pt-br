---
title: Como desenhar linhas opacas e semitransparentes
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
- drawing [Windows Forms], lines
- transparency [Windows Forms], lines
- lines [Windows Forms], drawing alpha blended
- alpha blending [Windows Forms], drawing lines
ms.assetid: 8f2508af-f495-4223-b5cc-646cbbb520eb
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a298458489968cf680a9d5f935d98afb470859ce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-opaque-and-semitransparent-lines"></a>Como desenhar linhas opacas e semitransparentes
Quando você desenha uma linha, você deve passar um <xref:System.Drawing.Pen> o objeto para o <xref:System.Drawing.Graphics.DrawLine%2A> método do <xref:System.Drawing.Graphics> classe. Um dos parâmetros do <xref:System.Drawing.Pen.%23ctor%2A> construtor é um <xref:System.Drawing.Color> objeto. Para desenhar uma linha opaca, defina o componente alfa da cor como 255. Para desenhar uma linha semitransparente, defina o componente alfa para qualquer valor de 1 a 254.  
  
 Ao desenhar uma linha semitransparente em uma tela de fundo, a cor da linha é combinada com as cores da tela de fundo. O componente alfa especifica como as cores da tela de fundo e da linha são misturadas; valores alfa próximos a 0 colocam mais peso nas cores da tela de fundo e valores alfa próximos a 255 colocam mais peso na cor da linha.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir desenha um bitmap e, em seguida, desenha três linhas que usam o bitmap como tela de fundo. A primeira linha usa um componente alfa de 255, portanto, é opaca. As segunda e terceira linhas usam um componente alfa de 128, para que sejam semitransparentes. É possível ver a imagem da tela de fundo pelas linhas. A instrução que define o <xref:System.Drawing.Graphics.CompositingQuality%2A> propriedade faz com que a mesclagem para a terceira linha a ser feita em conjunto com correção gama.  
  
 A seguinte ilustração mostra a saída do código a seguir.  
  
 ![Opacas e semitransparentes](../../../../docs/framework/winforms/advanced/media/compqualline.png "compqualline")  
  
 [!code-csharp[System.Drawing.AlphaBlending#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.AlphaBlending#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.  
  
## <a name="see-also"></a>Consulte também  
 [Combinação Alfa em Linhas e Preenchimentos](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)  
 [Como dar ao controle uma tela de fundo transparente](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)  
 [Como Desenhar com Pincéis Opacos e Semitransparentes](../../../../docs/framework/winforms/advanced/how-to-draw-with-opaque-and-semitransparent-brushes.md)
