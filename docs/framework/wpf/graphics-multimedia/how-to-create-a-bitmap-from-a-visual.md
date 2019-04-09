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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59189866"
---
# <a name="how-to-create-a-bitmap-from-a-visual"></a><span data-ttu-id="1dfcb-102">Como: Criar um bitmap usando um visual</span><span class="sxs-lookup"><span data-stu-id="1dfcb-102">How to: Create a Bitmap from a Visual</span></span>
<span data-ttu-id="1dfcb-103">Este exemplo mostra como você pode criar um bitmap de um <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="1dfcb-103">This example shows how you can create a bitmap from a <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="1dfcb-104">Um <xref:System.Windows.Media.DrawingVisual> é renderizado com <xref:System.Windows.Media.FormattedText>.</span><span class="sxs-lookup"><span data-stu-id="1dfcb-104">A <xref:System.Windows.Media.DrawingVisual> is rendered with <xref:System.Windows.Media.FormattedText>.</span></span> <span data-ttu-id="1dfcb-105">O <xref:System.Windows.Media.Visual> é renderizado para o <xref:System.Windows.Media.Imaging.RenderTargetBitmap> criando um bitmap do texto especificado.</span><span class="sxs-lookup"><span data-stu-id="1dfcb-105">The <xref:System.Windows.Media.Visual> is then rendered to the <xref:System.Windows.Media.Imaging.RenderTargetBitmap> creating a bitmap of the given text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1dfcb-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1dfcb-106">Example</span></span>  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#CreateRTBImage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample.cs#creatertbimage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#CreateRTBImage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample.vb#creatertbimage)]  
  
## <a name="see-also"></a><span data-ttu-id="1dfcb-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1dfcb-107">See also</span></span>

- <xref:System.Windows.Media.DrawingContext>
- [<span data-ttu-id="1dfcb-108">Visão geral da geração de imagens</span><span class="sxs-lookup"><span data-stu-id="1dfcb-108">Imaging Overview</span></span>](imaging-overview.md)
- [<span data-ttu-id="1dfcb-109">Visão geral dos objetos de desenho</span><span class="sxs-lookup"><span data-stu-id="1dfcb-109">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="1dfcb-110">Usando objetos DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="1dfcb-110">Using DrawingVisual Objects</span></span>](using-drawingvisual-objects.md)
