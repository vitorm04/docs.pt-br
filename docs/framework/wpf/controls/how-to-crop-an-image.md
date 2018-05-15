---
title: Como recortar uma imagem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [WPF], cropping
- cropping images [WPF]
ms.assetid: c6bba109-c6e7-4cf8-bfe6-9cf8d01bb4fc
ms.openlocfilehash: 46c559356447688e52508b823cc260c13128208f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-crop-an-image"></a><span data-ttu-id="e2d34-102">Como recortar uma imagem</span><span class="sxs-lookup"><span data-stu-id="e2d34-102">How to: Crop an Image</span></span>
<span data-ttu-id="e2d34-103">Este exemplo mostra como cortar uma imagem usando <xref:System.Windows.Media.Imaging.CroppedBitmap>.</span><span class="sxs-lookup"><span data-stu-id="e2d34-103">This example shows how to crop an image using <xref:System.Windows.Media.Imaging.CroppedBitmap>.</span></span>  
  
 <span data-ttu-id="e2d34-104"><xref:System.Windows.Media.Imaging.CroppedBitmap> é usado principalmente quando codificando uma versão recortada de uma imagem para salvar um arquivo.</span><span class="sxs-lookup"><span data-stu-id="e2d34-104"><xref:System.Windows.Media.Imaging.CroppedBitmap> is primarily used when encoding a cropped version of an image to save out to a file.</span></span> <span data-ttu-id="e2d34-105">Para cortar uma imagem para fins de exibição, consulte o [criar uma região de Clip](http://msdn.microsoft.com/library/56e4bed6-78d7-4292-b917-d72d0b3e4376) tópico.</span><span class="sxs-lookup"><span data-stu-id="e2d34-105">To crop an image for display purposes see the [Create a Clip Region](http://msdn.microsoft.com/library/56e4bed6-78d7-4292-b917-d72d0b3e4376) topic.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2d34-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e2d34-106">Example</span></span>  
 <span data-ttu-id="e2d34-107">O seguinte [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] define os recursos usados no exemplo abaixo.</span><span class="sxs-lookup"><span data-stu-id="e2d34-107">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] defines resources used within the samples below.</span></span>  
  
 [!code-xaml[imageelementexample#CroppedXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml1)]  
  
 <span data-ttu-id="e2d34-108">O exemplo a seguir cria uma imagem usando uma <xref:System.Windows.Media.Imaging.CroppedBitmap> como sua fonte.</span><span class="sxs-lookup"><span data-stu-id="e2d34-108">The following example creates an image using a <xref:System.Windows.Media.Imaging.CroppedBitmap> as its source.</span></span>  
  
 [!code-xaml[imageelementexample#CroppedXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml2)]  
  
 [!code-csharp[imageelementexample#CroppedCSharp1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml.cs#croppedcsharp1)]
 [!code-vb[imageelementexample#CroppedCSharp1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/CroppedImageExample.xaml.vb#croppedcsharp1)]  
  
 <span data-ttu-id="e2d34-109">O <xref:System.Windows.Media.Imaging.CroppedBitmap> também pode ser usado como a origem de outro <xref:System.Windows.Media.Imaging.CroppedBitmap>, encadeamento de corte.</span><span class="sxs-lookup"><span data-stu-id="e2d34-109">The <xref:System.Windows.Media.Imaging.CroppedBitmap> can also be used as the source of another <xref:System.Windows.Media.Imaging.CroppedBitmap>, chaining the cropping.</span></span> <span data-ttu-id="e2d34-110">Observe que o <xref:System.Windows.Media.Imaging.CroppedBitmap.SourceRect%2A> usa valores que são relativas ao bitmap recortado fonte e não a imagem inicial.</span><span class="sxs-lookup"><span data-stu-id="e2d34-110">Note that the <xref:System.Windows.Media.Imaging.CroppedBitmap.SourceRect%2A> uses values that are relative to the source cropped bitmap and not the initial image.</span></span>  
  
 [!code-xaml[imageelementexample#CroppedXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml3)]  
  
 [!code-csharp[imageelementexample#CroppedCSharp2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml.cs#croppedcsharp2)]
 [!code-vb[imageelementexample#CroppedCSharp2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/CroppedImageExample.xaml.vb#croppedcsharp2)]  
  
## <a name="see-also"></a><span data-ttu-id="e2d34-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e2d34-111">See Also</span></span>  
 [<span data-ttu-id="e2d34-112">Criar uma região de recorte</span><span class="sxs-lookup"><span data-stu-id="e2d34-112">Create a Clip Region</span></span>](http://msdn.microsoft.com/library/56e4bed6-78d7-4292-b917-d72d0b3e4376)
