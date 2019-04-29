---
title: Cortando e dimensionando imagens no GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, scaling images
- GDI+, cropping images
- images [Windows Forms], cropping
- compressing data [Windows Forms], images
- images [Windows Forms], expansion
- images [Windows Forms], scaling
- rectangles [Windows Forms], source
- rectangles [Windows Forms], destination
- images [Windows Forms], compression
ms.assetid: ad5daf26-005f-45bc-a2af-e0e97777a21a
ms.openlocfilehash: c3cdb06e99770808461f9266fb5f07df9074149b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769469"
---
# <a name="cropping-and-scaling-images-in-gdi"></a>Cortando e dimensionando imagens no GDI+
Você pode usar o <xref:System.Drawing.Graphics.DrawImage%2A> método da <xref:System.Drawing.Graphics> classe para desenhar e posicionar imagens vetoriais e imagens de varredura. <xref:System.Drawing.Graphics.DrawImage%2A> é um método sobrecarregado, portanto, há várias maneiras que você pode fornecer argumentos.  
  
## <a name="drawimage-variations"></a>Variações de DrawImage  
 Uma variação do <xref:System.Drawing.Graphics.DrawImage%2A> método recebe um <xref:System.Drawing.Bitmap> e um <xref:System.Drawing.Rectangle>. O retângulo especifica o destino da operação de desenho ou seja, especifica o retângulo no qual a imagem será desenhada. Se o tamanho do retângulo de destino for diferente do tamanho da imagem original, a escala dela será ajustada para caber no retângulo de destino. O exemplo de código a seguir mostra como desenhar a mesma imagem três vezes: uma vez sem escala, uma vez expandida e outra compactada:  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#31)]  
  
 A ilustração a seguir mostra as três imagens.  
  
 ![Colocação em escala](./media/aboutgdip03-art06.gif "AboutGdip03_Art06")  
  
 Algumas variações do <xref:System.Drawing.Graphics.DrawImage%2A> método têm um parâmetro do retângulo de origem, bem como um parâmetro do retângulo de destino. O parâmetro do retângulo de origem especifica a parte da imagem original a ser desenhada. O retângulo de destino especifica o retângulo no qual desenhar a parte da imagem. Se o tamanho do retângulo de destino for diferente do tamanho do retângulo de origem, a escala dela será ajustada para caber no retângulo de destino.  
  
 O exemplo de código a seguir mostra como construir um <xref:System.Drawing.Bitmap> do arquivo jpg. Toda a imagem é desenhada sem nenhuma escala em (0, 0). Em seguida, uma pequena parte da imagem é desenhada duas vezes: uma expandida e outra compactada.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#32)]  
  
 A ilustração a seguir mostra a imagem sem escala e as partes da imagem compactada e expandida.  
  
 ![Recorte e colocação em escala](./media/aboutgdip03-art07.gif "AboutGdip03_Art07")  
  
## <a name="see-also"></a>Consulte também

- [Imagens, bitmaps e metarquivos](images-bitmaps-and-metafiles.md)
- [Trabalhando com Imagens, Bitmaps, Ícones e Metarquivos](working-with-images-bitmaps-icons-and-metafiles.md)
