---
title: Como distorcer cores
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
- colors [Windows Forms], transforming with color matrices
- colors [Windows Forms], shearing
ms.assetid: 0a424171-5b8b-45c4-afef-e9720a6c3e22
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0a32e6c1901f84c276c071402dac641d45566717
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-shear-colors"></a>Como distorcer cores
A distorção aumenta ou diminui um componente de cor em uma quantidade proporcional a outro componente de cor. Por exemplo, considere a transformação em que o componente vermelho é aumentado pela metade do valor do componente azul. Nessa transformação, a cor (0,2, 0,5, 1) seria (0,7, 0,5, 1). O novo componente vermelho é 0,2 + (1/2)(1) = 0,7.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir constrói um <xref:System.Drawing.Image> objeto do arquivo ColorBars4.bmp. Em seguida, o código se aplica à transformação de distorção descrita no parágrafo anterior para cada pixel da imagem.  
  
 A ilustração a seguir mostra a imagem original à esquerda e a imagem distorcida à direita.  
  
 ![Distorcer cores](../../../../docs/framework/winforms/advanced/media/colortrans6.png "colortrans6")  
  
 A tabela a seguir lista os vetores de cores para as quatro barras antes e depois da transformação de distorção.  
  
|Original|Distorcido|  
|--------------|-------------|  
|(0, 0, 1, 1)|(0.5, 0, 1, 1)|  
|(0.5, 1, 0.5, 1)|(0.75, 1, 0.5, 1)|  
|(1, 1, 0, 1)|(1, 1, 0, 1)|  
|(0.4, 0.4, 0.4, 1)|(0.6, 0.4, 0.4, 1)|  
  
 [!code-csharp[System.Drawing.Misc3#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos. Substitua `ColorBars.bmp` por um nome de imagem e caminho válidos no sistema.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [Elementos Gráficos e Desenho nos Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Recolorindo Imagens](../../../../docs/framework/winforms/advanced/recoloring-images.md)
