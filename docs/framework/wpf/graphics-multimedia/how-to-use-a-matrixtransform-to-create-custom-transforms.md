---
title: 'Como: Usar um MatrixTransform para criar transformações personalizadas'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], custom Transforms
ms.assetid: 919381ca-989f-47cf-86b4-1094060236e4
ms.openlocfilehash: 1971d5fe9422c5138f140517e6fd4c9f9b2cf48b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913911"
---
# <a name="how-to-use-a-matrixtransform-to-create-custom-transforms"></a><span data-ttu-id="76b22-102">Como: Usar um MatrixTransform para criar transformações personalizadas</span><span class="sxs-lookup"><span data-stu-id="76b22-102">How to: Use a MatrixTransform to Create Custom Transforms</span></span>
<span data-ttu-id="76b22-103">Este exemplo mostra como usar um <xref:System.Windows.Media.MatrixTransform> para converter (mover) a posição, a ampliação e a distorção de um. <xref:System.Windows.Controls.Button></span><span class="sxs-lookup"><span data-stu-id="76b22-103">This example shows how to use a <xref:System.Windows.Media.MatrixTransform> to translate (move) the position, stretch, and skew of a <xref:System.Windows.Controls.Button>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="76b22-104">Use a <xref:System.Windows.Media.MatrixTransform> classe para criar transformações personalizadas que não são fornecidas <xref:System.Windows.Media.RotateTransform>pelas classes, <xref:System.Windows.Media.SkewTransform> <xref:System.Windows.Media.ScaleTransform>, ou <xref:System.Windows.Media.TranslateTransform> .</span><span class="sxs-lookup"><span data-stu-id="76b22-104">Use the <xref:System.Windows.Media.MatrixTransform> class to create custom transformations that are not provided by the <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.SkewTransform>, <xref:System.Windows.Media.ScaleTransform>, or <xref:System.Windows.Media.TranslateTransform> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76b22-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="76b22-105">Example</span></span>  
 [!code-xaml[Transforms_snip#MatrixTransform](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MatrixTransformExample.xaml#matrixtransform)]  
  
## <a name="see-also"></a><span data-ttu-id="76b22-106">Consulte também</span><span class="sxs-lookup"><span data-stu-id="76b22-106">See also</span></span>

- <xref:System.Windows.Media.MatrixTransform>
- <xref:System.Windows.Media.Transform>
- [<span data-ttu-id="76b22-107">Visão geral de transformações</span><span class="sxs-lookup"><span data-stu-id="76b22-107">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="76b22-108">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="76b22-108">How-to Topics</span></span>](transformations-how-to-topics.md)
- [<span data-ttu-id="76b22-109">Visão geral de formas e desenho básico no WPF</span><span class="sxs-lookup"><span data-stu-id="76b22-109">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
