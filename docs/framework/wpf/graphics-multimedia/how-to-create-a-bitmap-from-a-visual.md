---
title: 'Como: Criar um bitmap a partir de um visual'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [WPF], rendering from visuals
- visuals [WPF], rendering to bitmaps
ms.assetid: 103fc7f5-7306-4026-9d61-2005e79959f3
ms.openlocfilehash: 429aacc99d8ead5a18e9be7602b19a74773b419a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362858"
---
# <a name="how-to-create-a-bitmap-from-a-visual"></a><span data-ttu-id="3a679-102">Como: Criar um bitmap a partir de um visual</span><span class="sxs-lookup"><span data-stu-id="3a679-102">How to: Create a Bitmap from a Visual</span></span>
<span data-ttu-id="3a679-103">Este exemplo mostra como você pode criar um bitmap de um <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="3a679-103">This example shows how you can create a bitmap from a <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="3a679-104">Um <xref:System.Windows.Media.DrawingVisual> é renderizado com <xref:System.Windows.Media.FormattedText>.</span><span class="sxs-lookup"><span data-stu-id="3a679-104">A <xref:System.Windows.Media.DrawingVisual> is rendered with <xref:System.Windows.Media.FormattedText>.</span></span> <span data-ttu-id="3a679-105">O <xref:System.Windows.Media.Visual> é renderizado para o <xref:System.Windows.Media.Imaging.RenderTargetBitmap> criando um bitmap do texto especificado.</span><span class="sxs-lookup"><span data-stu-id="3a679-105">The <xref:System.Windows.Media.Visual> is then rendered to the <xref:System.Windows.Media.Imaging.RenderTargetBitmap> creating a bitmap of the given text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a679-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3a679-106">Example</span></span>  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#CreateRTBImage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample.cs#creatertbimage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#CreateRTBImage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample.vb#creatertbimage)]  
  
## <a name="see-also"></a><span data-ttu-id="3a679-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3a679-107">See also</span></span>
- <xref:System.Windows.Media.DrawingContext>
- [<span data-ttu-id="3a679-108">Visão geral da geração de imagens</span><span class="sxs-lookup"><span data-stu-id="3a679-108">Imaging Overview</span></span>](imaging-overview.md)
- [<span data-ttu-id="3a679-109">Visão geral dos objetos de desenho</span><span class="sxs-lookup"><span data-stu-id="3a679-109">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="3a679-110">Usando objetos DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="3a679-110">Using DrawingVisual Objects</span></span>](using-drawingvisual-objects.md)
