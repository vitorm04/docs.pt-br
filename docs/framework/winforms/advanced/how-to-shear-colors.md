---
title: Como distorcer cores
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], transforming with color matrices
- colors [Windows Forms], shearing
ms.assetid: 0a424171-5b8b-45c4-afef-e9720a6c3e22
ms.openlocfilehash: 825e5a90ebb0d9df3b894ce7bd353e917b676939
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142388"
---
# <a name="how-to-shear-colors"></a>Como distorcer cores
A distorção aumenta ou diminui um componente de cor em uma quantidade proporcional a outro componente de cor. Por exemplo, considere a transformação em que o componente vermelho é aumentado pela metade do valor do componente azul. Nessa transformação, a cor (0,2, 0,5, 1) seria (0,7, 0,5, 1). O novo componente vermelho é 0,2 + (1/2)(1) = 0,7.  
  
## <a name="example"></a>Exemplo  
 O exemplo a <xref:System.Drawing.Image> seguir constrói um objeto a partir do arquivo ColorBars4.bmp. Em seguida, o código se aplica à transformação de distorção descrita no parágrafo anterior para cada pixel da imagem.  
  
 A ilustração a seguir mostra a imagem original à esquerda e a imagem desfiada à direita:
  
 ![Dois quadrados com listras coloridas lado a lado ilustrando a imagem original e a imagem de sheared.](./media/how-to-shear-colors/original-image-sheared-image.png)  
  
 A tabela a seguir lista os vetores de cores para as quatro barras antes e depois da transformação de distorção.  
  
|Original|Distorcido|  
|--------------|-------------|  
|(0, 0, 1, 1)|(0.5, 0, 1, 1)|  
|(0.5, 1, 0.5, 1)|(0.75, 1, 0.5, 1)|  
|(1, 1, 0, 1)|(1, 1, 0, 1)|  
|(0.4, 0.4, 0.4, 1)|(0.6, 0.4, 0.4, 1)|  
  
 [!code-csharp[System.Drawing.Misc3#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior foi projetado para ser <xref:System.Windows.Forms.PaintEventArgs> `e`usado com formulários do <xref:System.Windows.Forms.Control.Paint> Windows e requer , o que é um parâmetro do manipulador de eventos. Substitua `ColorBars.bmp` por um nome de imagem e caminho válidos no sistema.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Elementos gráficos e desenho no Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Recolorindo Imagens](recoloring-images.md)
