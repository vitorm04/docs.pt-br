---
title: 'Como: Pintar uma área com um vídeo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- painting with a video [WPF]
- video [WPF], painting with
- brushes [WPF], painting with a video
ms.assetid: 04dd6600-4a6e-4b43-a93e-21cce7dfbcb8
ms.openlocfilehash: be09d1310847cd7214ea795a704c25d994f07b7a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59151171"
---
# <a name="how-to-paint-an-area-with-a-video"></a>Como: Pintar uma área com um vídeo
Este exemplo mostra como pintar uma área com mídia. Uma maneira de pintar uma área com mídia é usar um <xref:System.Windows.Controls.MediaElement> junto com um <xref:System.Windows.Media.VisualBrush>. Use o <xref:System.Windows.Controls.MediaElement> para carregar e executar a mídia e, em seguida, usá-lo para definir o <xref:System.Windows.Media.VisualBrush.Visual%2A> propriedade do <xref:System.Windows.Media.VisualBrush>. Você pode usar o <xref:System.Windows.Media.VisualBrush> para pintar uma área com a mídia carregada.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa uma <xref:System.Windows.Controls.MediaElement> e uma <xref:System.Windows.Media.VisualBrush> para pintar o <xref:System.Windows.Controls.TextBlock.Foreground%2A> de um <xref:System.Windows.Controls.TextBlock> controle com vídeo. Este exemplo define o <xref:System.Windows.Controls.MediaElement.IsMuted%2A> propriedade do <xref:System.Windows.Controls.MediaElement> para `true` para que ele produza nenhum som.  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundinline)]  
  
## <a name="example"></a>Exemplo  
 Porque <xref:System.Windows.Media.VisualBrush> herda o <xref:System.Windows.Media.TileBrush> classe, ele fornece vários modos de lado a lado. Definindo o <xref:System.Windows.Media.TileBrush.TileMode%2A> propriedade de um <xref:System.Windows.Media.VisualBrush> à <xref:System.Windows.Media.TileMode.Tile> e definindo seu <xref:System.Windows.Media.TileBrush.Viewport%2A> propriedade um valor menor que a área que você está pintando, você pode criar um padrão lado a lado.  
  
 O exemplo a seguir é idêntico ao exemplo anterior, exceto que o <xref:System.Windows.Media.VisualBrush> gera um padrão de vídeo.  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundtiledinline)]  
  
 Para obter informações sobre como adicionar um arquivo de conteúdo, como um arquivo de mídia, ao seu aplicativo, consulte [Recurso de aplicativo do WPF, conteúdo e arquivos de dados](../app-development/wpf-application-resource-content-and-data-files.md). Ao adicionar um arquivo de mídia, você deve adicioná-lo como um arquivo de conteúdo e não como um arquivo de recurso.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.VisualBrush>
- [Pintando com imagens, desenhos e visuais](painting-with-images-drawings-and-visuals.md)
- [Visão geral de TileBrush](tilebrush-overview.md)
- [Visão geral de multimídia](multimedia-overview.md)
