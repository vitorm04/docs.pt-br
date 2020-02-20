---
title: Como criar um reflexo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating reflections [WPF]
- brushes [WPF], creating reflections
- reflections [WPF], creating
ms.assetid: 4f017e16-ab80-43c7-98df-03b6bddbb203
ms.openlocfilehash: 8a5ed345c0aa25312bd74799264e1f66ab4554e0
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452052"
---
# <a name="how-to-create-a-reflection"></a><span data-ttu-id="a1102-102">Como criar um reflexo</span><span class="sxs-lookup"><span data-stu-id="a1102-102">How to: Create a Reflection</span></span>
<span data-ttu-id="a1102-103">Este exemplo mostra como usar um <xref:System.Windows.Media.VisualBrush> para criar uma reflexão.</span><span class="sxs-lookup"><span data-stu-id="a1102-103">This example shows how to use a <xref:System.Windows.Media.VisualBrush> to create a reflection.</span></span> <span data-ttu-id="a1102-104">Como um <xref:System.Windows.Media.VisualBrush> pode exibir um Visual existente, você pode usar essa capacidade para produzir efeitos visuais interessantes, como reflexos e ampliação.</span><span class="sxs-lookup"><span data-stu-id="a1102-104">Because a <xref:System.Windows.Media.VisualBrush> can display an existing visual, you can use this capability to produce interesting visual effects, such as reflections and magnification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1102-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a1102-105">Example</span></span>  
 <span data-ttu-id="a1102-106">O exemplo a seguir usa um <xref:System.Windows.Media.VisualBrush> para criar uma reflexão de uma <xref:System.Windows.Controls.Border> que contém vários elementos.</span><span class="sxs-lookup"><span data-stu-id="a1102-106">The following example uses a <xref:System.Windows.Media.VisualBrush> to create a reflection of a <xref:System.Windows.Controls.Border> that contains several elements.</span></span> <span data-ttu-id="a1102-107">A ilustração a seguir mostra a saída que esse exemplo produz.</span><span class="sxs-lookup"><span data-stu-id="a1102-107">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="a1102-108">![Um objeto visual refletido](./media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")</span><span class="sxs-lookup"><span data-stu-id="a1102-108">![A reflected Visual object](./media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")</span></span>  
<span data-ttu-id="a1102-109">Um objeto visual refletido</span><span class="sxs-lookup"><span data-stu-id="a1102-109">A reflected Visual object</span></span>  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 <span data-ttu-id="a1102-110">Para obter o exemplo completo, que inclui exemplos que mostram como ampliar partes da tela e como criar reflexos, consulte [exemplo de VisualBrush](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush).</span><span class="sxs-lookup"><span data-stu-id="a1102-110">For the complete sample, which includes examples that show how to magnify parts of the screen and how to create reflections, see [VisualBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1102-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="a1102-111">See also</span></span>

- <xref:System.Windows.Media.VisualBrush>
- [<span data-ttu-id="a1102-112">Pintando com imagens, desenhos e visuais</span><span class="sxs-lookup"><span data-stu-id="a1102-112">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
