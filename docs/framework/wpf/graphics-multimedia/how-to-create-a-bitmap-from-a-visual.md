---
title: 'Como: Criar um bitmap usando um visual'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [WPF], rendering from visuals
- visuals [WPF], rendering to bitmaps
ms.assetid: 103fc7f5-7306-4026-9d61-2005e79959f3
ms.openlocfilehash: a622d99f7c477f8654526ed399f1eb37288682fe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59189866"
---
# <a name="how-to-create-a-bitmap-from-a-visual"></a>Como: Criar um bitmap usando um visual
Este exemplo mostra como você pode criar um bitmap de um <xref:System.Windows.Media.Visual>. Um <xref:System.Windows.Media.DrawingVisual> é renderizado com <xref:System.Windows.Media.FormattedText>. O <xref:System.Windows.Media.Visual> é renderizado para o <xref:System.Windows.Media.Imaging.RenderTargetBitmap> criando um bitmap do texto especificado.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#CreateRTBImage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample.cs#creatertbimage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#CreateRTBImage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample.vb#creatertbimage)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.DrawingContext>
- [Visão geral da geração de imagens](imaging-overview.md)
- [Visão geral dos objetos de desenho](drawing-objects-overview.md)
- [Usando objetos DrawingVisual](using-drawingvisual-objects.md)
