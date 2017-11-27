---
title: "Como usar um MatrixTransform para criar transformações personalizadas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: graphics [WPF], custom Transforms
ms.assetid: 919381ca-989f-47cf-86b4-1094060236e4
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4995c5d712807e91b27c7afacd6f5b7015cb5898
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-matrixtransform-to-create-custom-transforms"></a><span data-ttu-id="f3a58-102">Como usar um MatrixTransform para criar transformações personalizadas</span><span class="sxs-lookup"><span data-stu-id="f3a58-102">How to: Use a MatrixTransform to Create Custom Transforms</span></span>
<span data-ttu-id="f3a58-103">Este exemplo mostra como usar um <xref:System.Windows.Media.MatrixTransform> transladar (mover) a posição, Alongar e distorcer um <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="f3a58-103">This example shows how to use a <xref:System.Windows.Media.MatrixTransform> to translate (move) the position, stretch, and skew of a <xref:System.Windows.Controls.Button>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f3a58-104">Use o <xref:System.Windows.Media.MatrixTransform> classe para criar transformações personalizadas que não são fornecidas pelo <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.SkewTransform>, <xref:System.Windows.Media.ScaleTransform>, ou <xref:System.Windows.Media.TranslateTransform> classes.</span><span class="sxs-lookup"><span data-stu-id="f3a58-104">Use the <xref:System.Windows.Media.MatrixTransform> class to create custom transformations that are not provided by the <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.SkewTransform>, <xref:System.Windows.Media.ScaleTransform>, or <xref:System.Windows.Media.TranslateTransform> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3a58-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f3a58-105">Example</span></span>  
 [!code-xaml[Transforms_snip#MatrixTransform](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MatrixTransformExample.xaml#matrixtransform)]  
  
## <a name="see-also"></a><span data-ttu-id="f3a58-106">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3a58-106">See Also</span></span>  
 <xref:System.Windows.Media.MatrixTransform>  
 <xref:System.Windows.Media.Transform>  
 [<span data-ttu-id="f3a58-107">Visão geral de transformações</span><span class="sxs-lookup"><span data-stu-id="f3a58-107">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="f3a58-108">Tópicos explicativos</span><span class="sxs-lookup"><span data-stu-id="f3a58-108">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)  
 [<span data-ttu-id="f3a58-109">Visão geral de formas e desenho básico no WPF</span><span class="sxs-lookup"><span data-stu-id="f3a58-109">Shapes and Basic Drawing in WPF Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
