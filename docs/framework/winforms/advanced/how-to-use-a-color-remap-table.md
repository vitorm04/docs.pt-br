---
title: Como usar uma tabela de remapeamento de cores
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- color tables [Windows Forms], remapping colors with
- custom colors [Windows Forms], creating with color remap table
- color remap tables [Windows Forms], using
ms.assetid: 977df1ce-8665-42d4-9fb1-ef7f0ff63419
ms.openlocfilehash: ba763cc7960e71c6fc705d40eefdbde163d06181
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522467"
---
# <a name="how-to-use-a-color-remap-table"></a>Como usar uma tabela de remapeamento de cores
Remapeamento é o processo de conversão de cores em uma imagem seguindo uma tabela de remapeamento de cores. A tabela de remapeamento de cores é uma matriz de <xref:System.Drawing.Imaging.ColorMap> objetos. Cada <xref:System.Drawing.Imaging.ColorMap> objeto na matriz tem um <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> propriedade e um <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> propriedade.  
  
 Quando [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] desenha uma imagem, cada pixel da imagem é comparado com a matriz de cores anterior. Se a cor do pixel corresponde a uma cor anterior, sua cor é alterada para a nova cor correspondente. As cores são alteradas somente para renderização — os valores de cor da imagem em si (armazenados em uma <xref:System.Drawing.Image> ou <xref:System.Drawing.Bitmap> objeto) não são alterados.  
  
 Para desenhar uma imagem remapeada, inicializar uma matriz de <xref:System.Drawing.Imaging.ColorMap> objetos. Passar a matriz para o <xref:System.Drawing.Imaging.ImageAttributes.SetRemapTable%2A> método de um <xref:System.Drawing.Imaging.ImageAttributes> objeto e, em seguida, passe o <xref:System.Drawing.Imaging.ImageAttributes> o objeto para o <xref:System.Drawing.Graphics.DrawImage%2A> método de um <xref:System.Drawing.Graphics> objeto.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um <xref:System.Drawing.Image> objeto do arquivo RemapInput.bmp. O código cria uma tabela de remapeamento de cores que consiste em um único <xref:System.Drawing.Imaging.ColorMap> objeto. O <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> propriedade o `ColorRemap` objeto é vermelho e o <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> propriedade é azul. A imagem é desenhada uma vez sem remapeamento e uma vez com remapeamento. O processo de remapeamento transforma todos os pixels vermelhos em azul.  
  
 A ilustração a seguir mostra a imagem original à esquerda e a imagem remapeada à direita.  
  
 ![Color ReMap](../../../../docs/framework/winforms/advanced/media/colortrans7.png "colortrans7")  
  
 [!code-csharp[System.Drawing.RecoloringImages#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.RecoloringImages#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.  
  
## <a name="see-also"></a>Consulte também  
 [Recolorindo Imagens](../../../../docs/framework/winforms/advanced/recoloring-images.md)  
 [Imagens, bitmaps e metarquivos](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
