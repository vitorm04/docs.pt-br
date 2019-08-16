---
title: 'Como: Codificar um visual em um arquivo de imagem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image files [WPF], encoding from visuals
- encoding image formats [WPF]
- visuals [WPF], encoding to an image file
ms.assetid: 2036385b-ea47-4d54-8027-5797f52c8149
ms.openlocfilehash: 193b6a14e404d32bb49d6e0ef3cbd513166bcce2
ms.sourcegitcommit: 43761fcee10aeefcf851ea81cea3f3c691420856
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69545299"
---
# <a name="how-to-encode-a-visual-to-an-image-file"></a>Como: Codificar um visual em um arquivo de imagem
Este exemplo demonstra como codificar um <xref:System.Windows.Media.Visual> objeto em um arquivo de imagem usando um <xref:System.Windows.Media.Imaging.RenderTargetBitmap> e um. <xref:System.Windows.Media.Imaging.PngBitmapEncoder>  
  
## <a name="example"></a>Exemplo  
 O <xref:System.Windows.Media.DrawingVisual> é criado usando um <xref:System.Windows.Media.Imaging.BitmapImage> e <xref:System.Windows.Media.FormattedText> que é renderizado para <xref:System.Windows.Media.Imaging.RenderTargetBitmap>um. Em seguida, o bitmap renderizado é usado <xref:System.Windows.Media.Imaging.BitmapFrame> para criar um que é <xref:System.Windows.Media.Imaging.PngBitmapEncoder> adicionado ao para criar um novo arquivo PNG (Portable Network Graphics).  
  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample_Encode.cs#rtbencodeinline1)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample_Encode.vb#rtbencodeinline1)]  
  
 Um <xref:System.Windows.Media.Imaging.PngBitmapEncoder> foi usado neste exemplo, mas qualquer um dos objetos <xref:System.Windows.Media.Imaging.BitmapEncoder> derivados poderia ter sido usado para criar o arquivo de imagem.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.DrawingContext>
- [Visão geral da geração de imagens](imaging-overview.md)
- [Visão geral dos objetos de desenho](drawing-objects-overview.md)
- [Usando objetos DrawingVisual](using-drawingvisual-objects.md)
