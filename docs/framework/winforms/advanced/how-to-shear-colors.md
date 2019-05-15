---
title: 'Como: distorcer cores'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], transforming with color matrices
- colors [Windows Forms], shearing
ms.assetid: 0a424171-5b8b-45c4-afef-e9720a6c3e22
ms.openlocfilehash: b390caf644b86de0001387b2c3f41503fd34759a
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593200"
---
# <a name="how-to-shear-colors"></a>Como: distorcer cores
A distorção aumenta ou diminui um componente de cor em uma quantidade proporcional a outro componente de cor. Por exemplo, considere a transformação em que o componente vermelho é aumentado pela metade do valor do componente azul. Nessa transformação, a cor (0,2, 0,5, 1) seria (0,7, 0,5, 1). O novo componente vermelho é 0,2 + (1/2)(1) = 0,7.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir constrói um <xref:System.Drawing.Image> objeto no arquivo ColorBars4.bmp. Em seguida, o código se aplica à transformação de distorção descrita no parágrafo anterior para cada pixel da imagem.  
  
 A ilustração a seguir mostra a imagem original à esquerda e a imagem distorcida à direita: 
  
 ![Dois quadrados com listras colorida side-by-side ilustrando a imagem original e a imagem distorcida.](./media/how-to-shear-colors/original-image-sheared-image.png)  
  
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
 O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos. Substitua `ColorBars.bmp` por um nome de imagem e caminho válidos no sistema.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Elementos Gráficos e Desenho nos Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Recolorindo Imagens](recoloring-images.md)
