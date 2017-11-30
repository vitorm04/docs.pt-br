---
title: Desenhando, posicionando e clonando imagens no GDI+
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a3ba716a36280d2ac08dae907abbdbe05e563dfc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="drawing-positioning-and-cloning-images-in-gdi"></a>Desenhando, posicionando e clonando imagens no GDI+
Você pode usar o <xref:System.Drawing.Bitmap> classe para carregar e exibir as imagens de varredura e você pode usar o <xref:System.Drawing.Imaging.Metafile> classe para carregar e exibir imagens de vetor. O <xref:System.Drawing.Bitmap> e <xref:System.Drawing.Imaging.Metafile> classes herdam o <xref:System.Drawing.Image> classe. Para exibir uma imagem de vetor, você precisa de uma ocorrência da <xref:System.Drawing.Graphics> classe e um <xref:System.Drawing.Imaging.Metafile>. Para exibir uma imagem de varredura, você precisa de uma ocorrência da <xref:System.Drawing.Graphics> classe e um <xref:System.Drawing.Bitmap>. A instância do <xref:System.Drawing.Graphics> classe fornece a <xref:System.Drawing.Graphics.DrawImage%2A> método, que recebe o <xref:System.Drawing.Imaging.Metafile> ou <xref:System.Drawing.Bitmap> como um argumento.  
  
## <a name="file-types-and-cloning"></a>Tipos de arquivo e clonagem  
 O exemplo de código a seguir mostra como construir um <xref:System.Drawing.Bitmap> do arquivo Climber.jpg e exibe o bitmap. O ponto de destino para o canto superior esquerdo da imagem, (10, 10), especificado no segundo e terceiro parâmetros.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#11)]  
  
 A ilustração a seguir mostra a imagem.  
  
 ![Exemplo de imagem](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art04.gif "AboutGdip03_Art04")  
  
 Você pode construir <xref:System.Drawing.Bitmap> objetos de uma variedade de elementos gráficos de formatos de arquivo: BMP, GIF, JPEG, EXIF, PNG, TIFF e ícone.  
  
 O exemplo de código a seguir mostra como construir <xref:System.Drawing.Bitmap> objetos de uma variedade de tipos de arquivo e, em seguida, exibe os bitmaps.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#12)]  
  
 O <xref:System.Drawing.Bitmap> classe fornece um <xref:System.Drawing.Bitmap.Clone%2A> método que você pode usar para fazer uma cópia de um objeto existente <xref:System.Drawing.Bitmap>. O <xref:System.Drawing.Bitmap.Clone%2A> método tem um parâmetro de retângulo de origem que você pode usar para especificar a parte do bitmap original que você deseja copiar. O exemplo de código a seguir mostra como criar um <xref:System.Drawing.Bitmap> por meio da clonagem metade superior de um objeto existente <xref:System.Drawing.Bitmap>. As duas imagens são desenhadas.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#13)]  
  
 A ilustração a seguir mostra as duas imagens.  
  
 ![Recorte](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art05.gif "AboutGdip03_Art05")  
  
## <a name="see-also"></a>Consulte também  
 [Imagens, bitmaps e metarquivos](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Como Criar Objetos Gráficos para Desenho](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [Trabalhando com Imagens, Bitmaps, Ícones e Metarquivos](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
