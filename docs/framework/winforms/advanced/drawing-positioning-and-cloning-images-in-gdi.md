---
title: Desenhando, posicionando e clonando imagens no GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- raster images [Windows Forms]
- images [Windows Forms], positioning
- drawing [Windows Forms], images
- drawing [Windows Forms], raster images
- images [Windows Forms], cloning
- images [Windows Forms], drawing
- GDI+, drawing images
- GDI+, cloning images
- GDI+, positioning images
ms.assetid: 09f0c07a-19c0-43b4-90a2-862a10545ce8
ms.openlocfilehash: 9682c7be5956680556defd698cb97e8f4b1a7f50
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724643"
---
# <a name="drawing-positioning-and-cloning-images-in-gdi"></a>Desenhando, posicionando e clonando imagens no GDI+
Você pode usar o <xref:System.Drawing.Bitmap> classe para carregar e exibir imagens de varredura e você pode usar o <xref:System.Drawing.Imaging.Metafile> classe para carregar e exibir imagens vetoriais. O <xref:System.Drawing.Bitmap> e <xref:System.Drawing.Imaging.Metafile> classes herdam o <xref:System.Drawing.Image> classe. Para exibir uma imagem vetorial, você precisa de uma instância das <xref:System.Drawing.Graphics> classe e um <xref:System.Drawing.Imaging.Metafile>. Para exibir uma imagem de varredura, você precisa de uma instância das <xref:System.Drawing.Graphics> classe e um <xref:System.Drawing.Bitmap>. A instância das <xref:System.Drawing.Graphics> classe fornece a <xref:System.Drawing.Graphics.DrawImage%2A> método, que recebe o <xref:System.Drawing.Imaging.Metafile> ou <xref:System.Drawing.Bitmap> como um argumento.  
  
## <a name="file-types-and-cloning"></a>Tipos de arquivo e clonagem  
 O exemplo de código a seguir mostra como construir um <xref:System.Drawing.Bitmap> do arquivo climber e exibe o bitmap. O ponto de destino para o canto superior esquerdo da imagem, (10, 10), especificado no segundo e terceiro parâmetros.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#11)]  
  
 A ilustração a seguir mostra a imagem.  
  
 ![Exemplo de imagem](./media/aboutgdip03-art04.gif "AboutGdip03_Art04")  
  
 Você pode construir <xref:System.Drawing.Bitmap> objetos de uma variedade de elementos gráficos de formatos de arquivo: BMP, GIF, JPEG, EXIF, PNG, TIFF e ícone.  
  
 O exemplo de código a seguir mostra como construir <xref:System.Drawing.Bitmap> objetos de uma variedade de tipos de arquivo e, em seguida, exibe os bitmaps.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#12)]  
  
 O <xref:System.Drawing.Bitmap> classe fornece uma <xref:System.Drawing.Bitmap.Clone%2A> método que você pode usar para fazer uma cópia de um existente <xref:System.Drawing.Bitmap>. O <xref:System.Drawing.Bitmap.Clone%2A> método tem um parâmetro do retângulo de origem que você pode usar para especificar a parte do bitmap original que você deseja copiar. O exemplo de código a seguir mostra como criar uma <xref:System.Drawing.Bitmap> clonando a metade superior da existente <xref:System.Drawing.Bitmap>. As duas imagens são desenhadas.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#13)]  
  
 A ilustração a seguir mostra as duas imagens.  
  
 ![Recorte](./media/aboutgdip03-art05.gif "AboutGdip03_Art05")  
  
## <a name="see-also"></a>Consulte também
- [Imagens, bitmaps e metarquivos](images-bitmaps-and-metafiles.md)
- [Como: Criar objetos gráficos para desenho](how-to-create-graphics-objects-for-drawing.md)
- [Trabalhando com Imagens, Bitmaps, Ícones e Metarquivos](working-with-images-bitmaps-icons-and-metafiles.md)
