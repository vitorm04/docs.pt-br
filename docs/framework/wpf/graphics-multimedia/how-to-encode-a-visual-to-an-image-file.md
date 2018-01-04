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
# <a name="how-to-encode-a-visual-to-an-image-file"></a><span data-ttu-id="cff87-102">Como codificar um visual em um arquivo de imagem</span><span class="sxs-lookup"><span data-stu-id="cff87-102">How to: Encode a Visual to an Image File</span></span>
<span data-ttu-id="cff87-103">Este exemplo demonstra como codificar um <xref:System.Windows.Media.Visual> objeto em um arquivo de imagem usando um <xref:System.Windows.Media.Imaging.RenderTargetBitmap> e um <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.</span><span class="sxs-lookup"><span data-stu-id="cff87-103">This example demonstrates how to encode a <xref:System.Windows.Media.Visual> object into an image file using a <xref:System.Windows.Media.Imaging.RenderTargetBitmap> and a <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cff87-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cff87-104">Example</span></span>  
 <span data-ttu-id="cff87-105">O <xref:System.Windows.Media.DrawingVisual> é criado usando um <xref:System.Windows.Media.Imaging.BitmapImage> e <xref:System.Windows.Media.FormattedText> que é processado como um <xref:System.Windows.Media.Imaging.RenderTargetBitmap>.</span><span class="sxs-lookup"><span data-stu-id="cff87-105">The <xref:System.Windows.Media.DrawingVisual> is created using a <xref:System.Windows.Media.Imaging.BitmapImage> and <xref:System.Windows.Media.FormattedText> which is rendered to a <xref:System.Windows.Media.Imaging.RenderTargetBitmap>.</span></span> <span data-ttu-id="cff87-106">O bitmap renderizado, em seguida, é usado para criar um <xref:System.Windows.Media.Imaging.BitmapFrame> que é adicionado para o <xref:System.Windows.Media.Imaging.PngBitmapEncoder> para criar um novo [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)] arquivo.</span><span class="sxs-lookup"><span data-stu-id="cff87-106">The rendered bitmap is then used to create a <xref:System.Windows.Media.Imaging.BitmapFrame> which is added to the <xref:System.Windows.Media.Imaging.PngBitmapEncoder> to create a new [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)] file.</span></span>  
  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample_Encode.cs#rtbencodeinline1)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample_Encode.vb#rtbencodeinline1)]  
  
 <span data-ttu-id="cff87-107">Um <xref:System.Windows.Media.Imaging.PngBitmapEncoder> foi usado neste exemplo, mas qualquer derivados <xref:System.Windows.Media.Imaging.BitmapEncoder> objetos podem ter sido usados para criar o arquivo de imagem.</span><span class="sxs-lookup"><span data-stu-id="cff87-107">A <xref:System.Windows.Media.Imaging.PngBitmapEncoder> was used in this example but any of the derived <xref:System.Windows.Media.Imaging.BitmapEncoder> objects could have been used to create the image file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cff87-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cff87-108">See Also</span></span>  
 <xref:System.Windows.Media.DrawingContext>  
 [<span data-ttu-id="cff87-109">Visão geral da geração de imagens</span><span class="sxs-lookup"><span data-stu-id="cff87-109">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)  
 [<span data-ttu-id="cff87-110">Visão geral dos objetos de desenho</span><span class="sxs-lookup"><span data-stu-id="cff87-110">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="cff87-111">Usando objetos DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="cff87-111">Using DrawingVisual Objects</span></span>](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)
