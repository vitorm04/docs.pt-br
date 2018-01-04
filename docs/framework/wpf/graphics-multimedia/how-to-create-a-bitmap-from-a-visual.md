---
title: Como criar um bitmap a partir de um visual
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
- bitmaps [WPF], rendering from visuals
- visuals [WPF], rendering to bitmaps
ms.assetid: 103fc7f5-7306-4026-9d61-2005e79959f3
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: db3ad547072f1d9162ede5c45144aa30e809c50e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-bitmap-from-a-visual"></a><span data-ttu-id="711fb-102">Como criar um bitmap a partir de um visual</span><span class="sxs-lookup"><span data-stu-id="711fb-102">How to: Create a Bitmap from a Visual</span></span>
<span data-ttu-id="711fb-103">Este exemplo mostra como você pode criar um bitmap de um <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="711fb-103">This example shows how you can create a bitmap from a <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="711fb-104">Um <xref:System.Windows.Media.DrawingVisual> é renderizada com <xref:System.Windows.Media.FormattedText>.</span><span class="sxs-lookup"><span data-stu-id="711fb-104">A <xref:System.Windows.Media.DrawingVisual> is rendered with <xref:System.Windows.Media.FormattedText>.</span></span> <span data-ttu-id="711fb-105">O <xref:System.Windows.Media.Visual> é renderizado para o <xref:System.Windows.Media.Imaging.RenderTargetBitmap> criando um bitmap do texto especificado.</span><span class="sxs-lookup"><span data-stu-id="711fb-105">The <xref:System.Windows.Media.Visual> is then rendered to the <xref:System.Windows.Media.Imaging.RenderTargetBitmap> creating a bitmap of the given text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="711fb-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="711fb-106">Example</span></span>  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#CreateRTBImage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample.cs#creatertbimage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#CreateRTBImage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample.vb#creatertbimage)]  
  
## <a name="see-also"></a><span data-ttu-id="711fb-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="711fb-107">See Also</span></span>  
 <xref:System.Windows.Media.DrawingContext>  
 [<span data-ttu-id="711fb-108">Visão geral da geração de imagens</span><span class="sxs-lookup"><span data-stu-id="711fb-108">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)  
 [<span data-ttu-id="711fb-109">Visão geral dos objetos de desenho</span><span class="sxs-lookup"><span data-stu-id="711fb-109">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="711fb-110">Usando objetos DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="711fb-110">Using DrawingVisual Objects</span></span>](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)
