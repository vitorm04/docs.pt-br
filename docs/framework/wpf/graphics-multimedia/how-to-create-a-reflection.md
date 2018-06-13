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
ms.openlocfilehash: c791dbbe02faaba790c650d482db092702730fa6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560570"
---
# <a name="how-to-create-a-reflection"></a><span data-ttu-id="a07c0-102">Como criar um reflexo</span><span class="sxs-lookup"><span data-stu-id="a07c0-102">How to: Create a Reflection</span></span>
<span data-ttu-id="a07c0-103">Este exemplo mostra como usar um <xref:System.Windows.Media.VisualBrush> para criar um reflexo.</span><span class="sxs-lookup"><span data-stu-id="a07c0-103">This example shows how to use a <xref:System.Windows.Media.VisualBrush> to create a reflection.</span></span> <span data-ttu-id="a07c0-104">Porque um <xref:System.Windows.Media.VisualBrush> pode exibir um visual existente, você pode usar esse recurso para produzir efeitos visuais interessantes, como reflexos e ampliação.</span><span class="sxs-lookup"><span data-stu-id="a07c0-104">Because a <xref:System.Windows.Media.VisualBrush> can display an existing visual, you can use this capability to produce interesting visual effects, such as reflections and magnification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a07c0-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a07c0-105">Example</span></span>  
 <span data-ttu-id="a07c0-106">O exemplo a seguir usa uma <xref:System.Windows.Media.VisualBrush> para criar um reflexo de um <xref:System.Windows.Controls.Border> que contém vários elementos.</span><span class="sxs-lookup"><span data-stu-id="a07c0-106">The following example uses a <xref:System.Windows.Media.VisualBrush> to create a reflection of a <xref:System.Windows.Controls.Border> that contains several elements.</span></span> <span data-ttu-id="a07c0-107">A ilustração a seguir mostra a saída que esse exemplo produz.</span><span class="sxs-lookup"><span data-stu-id="a07c0-107">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="a07c0-108">![Um objeto Visual de refletidas](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")</span><span class="sxs-lookup"><span data-stu-id="a07c0-108">![A reflected Visual object](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")</span></span>  
<span data-ttu-id="a07c0-109">Um objeto visual refletido</span><span class="sxs-lookup"><span data-stu-id="a07c0-109">A reflected Visual object</span></span>  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 <span data-ttu-id="a07c0-110">Para o exemplo completo, que inclui exemplos que mostram como ampliar partes da tela e como criar reflexos, consulte [VisualBrush Sample](http://go.microsoft.com/fwlink/?LinkID=160049).</span><span class="sxs-lookup"><span data-stu-id="a07c0-110">For the complete sample, which includes examples that show how to magnify parts of the screen and how to create reflections, see [VisualBrush Sample](http://go.microsoft.com/fwlink/?LinkID=160049).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a07c0-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a07c0-111">See Also</span></span>  
 <xref:System.Windows.Media.VisualBrush>  
 [<span data-ttu-id="a07c0-112">Pintando com imagens, desenhos e visuais</span><span class="sxs-lookup"><span data-stu-id="a07c0-112">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
