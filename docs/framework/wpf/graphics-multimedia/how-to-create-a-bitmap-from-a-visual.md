---
title: Como criar um bitmap a partir de um visual
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [WPF], rendering from visuals
- visuals [WPF], rendering to bitmaps
ms.assetid: 103fc7f5-7306-4026-9d61-2005e79959f3
ms.openlocfilehash: 4735474d00712598cb5e41fad289e8f568d83a48
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-bitmap-from-a-visual"></a>Como criar um bitmap a partir de um visual
Este exemplo mostra como você pode criar um bitmap de um <xref:System.Windows.Media.Visual>. Um <xref:System.Windows.Media.DrawingVisual> é renderizada com <xref:System.Windows.Media.FormattedText>. O <xref:System.Windows.Media.Visual> é renderizado para o <xref:System.Windows.Media.Imaging.RenderTargetBitmap> criando um bitmap do texto especificado.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#CreateRTBImage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample.cs#creatertbimage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#CreateRTBImage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample.vb#creatertbimage)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.DrawingContext>  
 [Visão geral da geração de imagens](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)  
 [Visão geral dos objetos de desenho](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [Usando objetos DrawingVisual](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)
