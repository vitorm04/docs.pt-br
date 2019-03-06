---
title: 'Como: Carregar uma imagem como uma miniatura'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- loading images as thumbnails [WPF]
- images [WPF], loading as thumbnails
- thumbnails [WPF], loading images as
ms.assetid: 02e055a0-54df-499a-b8b6-ab6ff7535cff
ms.openlocfilehash: 0b5435e9b06f37dae7dc762e9035b1eca8156ca6
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57353381"
---
# <a name="how-to-load-an-image-as-a-thumbnail"></a><span data-ttu-id="4759f-102">Como: Carregar uma imagem como uma miniatura</span><span class="sxs-lookup"><span data-stu-id="4759f-102">How to: Load an Image as a Thumbnail</span></span>
<span data-ttu-id="4759f-103">Os exemplos a seguir mostram como carregar um <xref:System.Windows.Controls.Image> como uma miniatura para conservar a memória do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4759f-103">The following examples show how to load an <xref:System.Windows.Controls.Image> as a thumbnail to conserve application memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4759f-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4759f-104">Example</span></span>  
 <span data-ttu-id="4759f-105">O exemplo a seguir define o <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> propriedade de um <xref:System.Windows.Media.Imaging.BitmapImage> no [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] para reduzir a memória necessária para carregar a imagem.</span><span class="sxs-lookup"><span data-stu-id="4759f-105">The following example sets the <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> property of a <xref:System.Windows.Media.Imaging.BitmapImage> in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to reduce the memory required to load the image.</span></span>  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a><span data-ttu-id="4759f-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4759f-106">Example</span></span>  
 <span data-ttu-id="4759f-107">O exemplo a seguir define o <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> propriedade de um <xref:System.Windows.Media.Imaging.BitmapImage> no código para reduzir a memória necessária para carregar a imagem.</span><span class="sxs-lookup"><span data-stu-id="4759f-107">The following example sets the <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> property of a <xref:System.Windows.Media.Imaging.BitmapImage> in code to reduce the memory required to load the image.</span></span>  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a><span data-ttu-id="4759f-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4759f-108">See also</span></span>
- [<span data-ttu-id="4759f-109">Visão geral da geração de imagens</span><span class="sxs-lookup"><span data-stu-id="4759f-109">Imaging Overview</span></span>](imaging-overview.md)
