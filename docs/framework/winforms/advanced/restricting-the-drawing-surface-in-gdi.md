---
title: "Restringindo a superfície de desenho no GDI+"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, clipping
- clipping [Windows Forms], using GDI+
- GDI+, restricting drawing surface
ms.assetid: 8b5f71d9-d2f0-4540-9c41-740f90fd4c26
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b7834c95959972e7264e1caa2cfc21b190341b21
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="restricting-the-drawing-surface-in-gdi"></a><span data-ttu-id="6d46c-102">Restringindo a superfície de desenho no GDI+</span><span class="sxs-lookup"><span data-stu-id="6d46c-102">Restricting the Drawing Surface in GDI+</span></span>
<span data-ttu-id="6d46c-103">Recorte envolve restringir o desenho a um determinado retângulo ou região.</span><span class="sxs-lookup"><span data-stu-id="6d46c-103">Clipping involves restricting drawing to a certain rectangle or region.</span></span> <span data-ttu-id="6d46c-104">A ilustração a seguir mostra a cadeia de caracteres "Hello" recortado para uma região em forma de coração.</span><span class="sxs-lookup"><span data-stu-id="6d46c-104">The following illustration shows the string "Hello" clipped to a heart-shaped region.</span></span>  
  
 <span data-ttu-id="6d46c-105">![Superfície de desenho restrita](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art30.gif "AboutGdip02_Art30")</span><span class="sxs-lookup"><span data-stu-id="6d46c-105">![Restricted Drawing Surface](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art30.gif "AboutGdip02_Art30")</span></span>  
  
## <a name="clipping-with-regions"></a><span data-ttu-id="6d46c-106">Recorte com regiões</span><span class="sxs-lookup"><span data-stu-id="6d46c-106">Clipping with Regions</span></span>  
 <span data-ttu-id="6d46c-107">Regiões podem ser construídas de caminhos e caminhos podem conter os contornos das cadeias de caracteres, então você pode usar o texto com contorno de corte.</span><span class="sxs-lookup"><span data-stu-id="6d46c-107">Regions can be constructed from paths, and paths can contain the outlines of strings, so you can use outlined text for clipping.</span></span> <span data-ttu-id="6d46c-108">A ilustração a seguir mostra um conjunto de elipses concêntricas recortado para o interior de uma cadeia de caracteres de texto.</span><span class="sxs-lookup"><span data-stu-id="6d46c-108">The following illustration shows a set of concentric ellipses clipped to the interior of a string of text.</span></span>  
  
 <span data-ttu-id="6d46c-109">![Superfície de desenho restrita](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art31.gif "AboutGdip02_Art31")</span><span class="sxs-lookup"><span data-stu-id="6d46c-109">![Restricted Drawing Surface](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art31.gif "AboutGdip02_Art31")</span></span>  
  
 <span data-ttu-id="6d46c-110">Para desenhar com corte, crie um <xref:System.Drawing.Graphics> do objeto, defina seu <xref:System.Drawing.Graphics.Clip%2A> propriedade e, em seguida, chamar os métodos de desenho do mesmo <xref:System.Drawing.Graphics> objeto:</span><span class="sxs-lookup"><span data-stu-id="6d46c-110">To draw with clipping, create a <xref:System.Drawing.Graphics> object, set its <xref:System.Drawing.Graphics.Clip%2A> property, and then call the drawing methods of that same <xref:System.Drawing.Graphics> object:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#91](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#91)]
 [!code-vb[LinesCurvesAndShapes#91](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#91)]  
  
## <a name="see-also"></a><span data-ttu-id="6d46c-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d46c-111">See Also</span></span>  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Region?displayProperty=nameWithType>  
 [<span data-ttu-id="6d46c-112">Linhas, Curvas e Formas</span><span class="sxs-lookup"><span data-stu-id="6d46c-112">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="6d46c-113">Usando regiões</span><span class="sxs-lookup"><span data-stu-id="6d46c-113">Using Regions</span></span>](../../../../docs/framework/winforms/advanced/using-regions.md)
