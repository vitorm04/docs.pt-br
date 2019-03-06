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
ms.openlocfilehash: 0756a9e87840648b55ecad4b3f1ce6e0e5452eb7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363287"
---
# <a name="how-to-paint-an-area-with-a-video"></a><span data-ttu-id="16c8f-102">Como: Pintar uma área com um vídeo</span><span class="sxs-lookup"><span data-stu-id="16c8f-102">How to: Paint an Area with a Video</span></span>
<span data-ttu-id="16c8f-103">Este exemplo mostra como pintar uma área com mídia.</span><span class="sxs-lookup"><span data-stu-id="16c8f-103">This example shows how to paint an area with media.</span></span> <span data-ttu-id="16c8f-104">Uma maneira de pintar uma área com mídia é usar um <xref:System.Windows.Controls.MediaElement> junto com um <xref:System.Windows.Media.VisualBrush>.</span><span class="sxs-lookup"><span data-stu-id="16c8f-104">One way to paint an area with media is to use a <xref:System.Windows.Controls.MediaElement> together with a <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="16c8f-105">Use o <xref:System.Windows.Controls.MediaElement> para carregar e executar a mídia e, em seguida, usá-lo para definir o <xref:System.Windows.Media.VisualBrush.Visual%2A> propriedade do <xref:System.Windows.Media.VisualBrush>.</span><span class="sxs-lookup"><span data-stu-id="16c8f-105">Use the <xref:System.Windows.Controls.MediaElement> to load and play the media, and then use it to set the <xref:System.Windows.Media.VisualBrush.Visual%2A> property of the <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="16c8f-106">Você pode usar o <xref:System.Windows.Media.VisualBrush> para pintar uma área com a mídia carregada.</span><span class="sxs-lookup"><span data-stu-id="16c8f-106">You can then use the <xref:System.Windows.Media.VisualBrush> to paint an area with the loaded media.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16c8f-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="16c8f-107">Example</span></span>  
 <span data-ttu-id="16c8f-108">O exemplo a seguir usa uma <xref:System.Windows.Controls.MediaElement> e uma <xref:System.Windows.Media.VisualBrush> para pintar o <xref:System.Windows.Controls.TextBlock.Foreground%2A> de um <xref:System.Windows.Controls.TextBlock> controle com vídeo.</span><span class="sxs-lookup"><span data-stu-id="16c8f-108">The following example uses a <xref:System.Windows.Controls.MediaElement> and a <xref:System.Windows.Media.VisualBrush> to paint the <xref:System.Windows.Controls.TextBlock.Foreground%2A> of a <xref:System.Windows.Controls.TextBlock> control with video.</span></span> <span data-ttu-id="16c8f-109">Este exemplo define o <xref:System.Windows.Controls.MediaElement.IsMuted%2A> propriedade do <xref:System.Windows.Controls.MediaElement> para `true` para que ele produza nenhum som.</span><span class="sxs-lookup"><span data-stu-id="16c8f-109">This example sets the <xref:System.Windows.Controls.MediaElement.IsMuted%2A> property of the <xref:System.Windows.Controls.MediaElement> to `true` so that it produces no sound.</span></span>  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundinline)]  
  
## <a name="example"></a><span data-ttu-id="16c8f-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="16c8f-110">Example</span></span>  
 <span data-ttu-id="16c8f-111">Porque <xref:System.Windows.Media.VisualBrush> herda o <xref:System.Windows.Media.TileBrush> classe, ele fornece vários modos de lado a lado.</span><span class="sxs-lookup"><span data-stu-id="16c8f-111">Because <xref:System.Windows.Media.VisualBrush> inherits from the <xref:System.Windows.Media.TileBrush> class, it provides several tiling modes.</span></span> <span data-ttu-id="16c8f-112">Definindo o <xref:System.Windows.Media.TileBrush.TileMode%2A> propriedade de um <xref:System.Windows.Media.VisualBrush> à <xref:System.Windows.Media.TileMode.Tile> e definindo seu <xref:System.Windows.Media.TileBrush.Viewport%2A> propriedade um valor menor que a área que você está pintando, você pode criar um padrão lado a lado.</span><span class="sxs-lookup"><span data-stu-id="16c8f-112">By setting the <xref:System.Windows.Media.TileBrush.TileMode%2A> property of a <xref:System.Windows.Media.VisualBrush> to <xref:System.Windows.Media.TileMode.Tile> and by setting its <xref:System.Windows.Media.TileBrush.Viewport%2A> property to a value smaller than the area that you are painting, you can create a tiled pattern.</span></span>  
  
 <span data-ttu-id="16c8f-113">O exemplo a seguir é idêntico ao exemplo anterior, exceto que o <xref:System.Windows.Media.VisualBrush> gera um padrão de vídeo.</span><span class="sxs-lookup"><span data-stu-id="16c8f-113">The following example is identical to the previous example, except that the <xref:System.Windows.Media.VisualBrush> generates a pattern from the video.</span></span>  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundtiledinline)]  
  
 <span data-ttu-id="16c8f-114">Para obter informações sobre como adicionar um arquivo de conteúdo, como um arquivo de mídia, ao seu aplicativo, consulte [Recurso de aplicativo do WPF, conteúdo e arquivos de dados](../app-development/wpf-application-resource-content-and-data-files.md).</span><span class="sxs-lookup"><span data-stu-id="16c8f-114">For information about how to add a content file, such as a media file, to your application, see [WPF Application Resource, Content, and Data Files](../app-development/wpf-application-resource-content-and-data-files.md).</span></span> <span data-ttu-id="16c8f-115">Ao adicionar um arquivo de mídia, você deve adicioná-lo como um arquivo de conteúdo e não como um arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="16c8f-115">When you add a media file, you must add it as a content file, not as a resource file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16c8f-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16c8f-116">See also</span></span>
- <xref:System.Windows.Media.VisualBrush>
- [<span data-ttu-id="16c8f-117">Pintando com imagens, desenhos e visuais</span><span class="sxs-lookup"><span data-stu-id="16c8f-117">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="16c8f-118">Visão geral de TileBrush</span><span class="sxs-lookup"><span data-stu-id="16c8f-118">TileBrush Overview</span></span>](tilebrush-overview.md)
- [<span data-ttu-id="16c8f-119">Visão geral de multimídia</span><span class="sxs-lookup"><span data-stu-id="16c8f-119">Multimedia Overview</span></span>](multimedia-overview.md)
