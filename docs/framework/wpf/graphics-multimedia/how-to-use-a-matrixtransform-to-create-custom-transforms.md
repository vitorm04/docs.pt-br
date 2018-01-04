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
ms.workload: dotnet
ms.openlocfilehash: 1414ae590be10c3adcc6857492e23bf659beec67
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-matrixtransform-to-create-custom-transforms"></a><span data-ttu-id="15610-102">Como usar um MatrixTransform para criar transformações personalizadas</span><span class="sxs-lookup"><span data-stu-id="15610-102">How to: Use a MatrixTransform to Create Custom Transforms</span></span>
<span data-ttu-id="15610-103">Este exemplo mostra como usar um <xref:System.Windows.Media.MatrixTransform> transladar (mover) a posição, Alongar e distorcer um <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="15610-103">This example shows how to use a <xref:System.Windows.Media.MatrixTransform> to translate (move) the position, stretch, and skew of a <xref:System.Windows.Controls.Button>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="15610-104">Use o <xref:System.Windows.Media.MatrixTransform> classe para criar transformações personalizadas que não são fornecidas pelo <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.SkewTransform>, <xref:System.Windows.Media.ScaleTransform>, ou <xref:System.Windows.Media.TranslateTransform> classes.</span><span class="sxs-lookup"><span data-stu-id="15610-104">Use the <xref:System.Windows.Media.MatrixTransform> class to create custom transformations that are not provided by the <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.SkewTransform>, <xref:System.Windows.Media.ScaleTransform>, or <xref:System.Windows.Media.TranslateTransform> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15610-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="15610-105">Example</span></span>  
 [!code-xaml[Transforms_snip#MatrixTransform](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MatrixTransformExample.xaml#matrixtransform)]  
  
## <a name="see-also"></a><span data-ttu-id="15610-106">Consulte também</span><span class="sxs-lookup"><span data-stu-id="15610-106">See Also</span></span>  
 <xref:System.Windows.Media.MatrixTransform>  
 <xref:System.Windows.Media.Transform>  
 [<span data-ttu-id="15610-107">Visão geral de transformações</span><span class="sxs-lookup"><span data-stu-id="15610-107">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="15610-108">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="15610-108">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)  
 [<span data-ttu-id="15610-109">Visão geral de formas e desenho básico no WPF</span><span class="sxs-lookup"><span data-stu-id="15610-109">Shapes and Basic Drawing in WPF Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
