---
title: Como carregar uma imagem como uma miniatura
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- loading images as thumbnails [WPF]
- images [WPF], loading as thumbnails
- thumbnails [WPF], loading images as
ms.assetid: 02e055a0-54df-499a-b8b6-ab6ff7535cff
ms.openlocfilehash: 349a602a10b89931701e24334bf5ac5536f26400
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562317"
---
# <a name="how-to-load-an-image-as-a-thumbnail"></a><span data-ttu-id="eeec9-102">Como carregar uma imagem como uma miniatura</span><span class="sxs-lookup"><span data-stu-id="eeec9-102">How to: Load an Image as a Thumbnail</span></span>
<span data-ttu-id="eeec9-103">Os exemplos a seguir mostram como carregar um <xref:System.Windows.Controls.Image> como uma miniatura para conservar a memória do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eeec9-103">The following examples show how to load an <xref:System.Windows.Controls.Image> as a thumbnail to conserve application memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eeec9-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="eeec9-104">Example</span></span>  
 <span data-ttu-id="eeec9-105">O exemplo a seguir define o <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> propriedade de um <xref:System.Windows.Media.Imaging.BitmapImage> no [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] para reduzir a memória necessária para carregar a imagem.</span><span class="sxs-lookup"><span data-stu-id="eeec9-105">The following example sets the <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> property of a <xref:System.Windows.Media.Imaging.BitmapImage> in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to reduce the memory required to load the image.</span></span>  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a><span data-ttu-id="eeec9-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="eeec9-106">Example</span></span>  
 <span data-ttu-id="eeec9-107">O exemplo a seguir define o <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> propriedade de um <xref:System.Windows.Media.Imaging.BitmapImage> em código para reduzir a memória necessária para carregar a imagem.</span><span class="sxs-lookup"><span data-stu-id="eeec9-107">The following example sets the <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> property of a <xref:System.Windows.Media.Imaging.BitmapImage> in code to reduce the memory required to load the image.</span></span>  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a><span data-ttu-id="eeec9-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eeec9-108">See Also</span></span>  
 [<span data-ttu-id="eeec9-109">Visão geral da geração de imagens</span><span class="sxs-lookup"><span data-stu-id="eeec9-109">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
