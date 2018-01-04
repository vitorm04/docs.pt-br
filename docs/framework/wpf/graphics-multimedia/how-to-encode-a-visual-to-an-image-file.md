---
title: Como codificar um visual em um arquivo de imagem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image files [WPF], encoding from visuals
- encoding image formats [WPF]
- visuals [WPF], encoding to an image file
ms.assetid: 2036385b-ea47-4d54-8027-5797f52c8149
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 88a5d93c9c4726d1f6493df28d0a2a559394ef74
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-encode-a-visual-to-an-image-file"></a>Como codificar um visual em um arquivo de imagem
Este exemplo demonstra como codificar um <xref:System.Windows.Media.Visual> objeto em um arquivo de imagem usando um <xref:System.Windows.Media.Imaging.RenderTargetBitmap> e um <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.  
  
## <a name="example"></a>Exemplo  
 O <xref:System.Windows.Media.DrawingVisual> é criado usando um <xref:System.Windows.Media.Imaging.BitmapImage> e <xref:System.Windows.Media.FormattedText> que é processado como um <xref:System.Windows.Media.Imaging.RenderTargetBitmap>. O bitmap renderizado, em seguida, é usado para criar um <xref:System.Windows.Media.Imaging.BitmapFrame> que é adicionado para o <xref:System.Windows.Media.Imaging.PngBitmapEncoder> para criar um novo [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)] arquivo.  
  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample_Encode.cs#rtbencodeinline1)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample_Encode.vb#rtbencodeinline1)]  
  
 Um <xref:System.Windows.Media.Imaging.PngBitmapEncoder> foi usado neste exemplo, mas qualquer derivados <xref:System.Windows.Media.Imaging.BitmapEncoder> objetos podem ter sido usados para criar o arquivo de imagem.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.DrawingContext>  
 [Visão geral da geração de imagens](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)  
 [Visão geral dos objetos de desenho](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [Usando objetos DrawingVisual](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)
