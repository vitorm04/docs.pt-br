---
title: 'Como: Criar uma reflexão'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating reflections [WPF]
- brushes [WPF], creating reflections
- reflections [WPF], creating
ms.assetid: 4f017e16-ab80-43c7-98df-03b6bddbb203
ms.openlocfilehash: 61b597cd36fcf0d60f215d9b5403f3b42b21dec4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61904210"
---
# <a name="how-to-create-a-reflection"></a><span data-ttu-id="18ed5-102">Como: Criar uma reflexão</span><span class="sxs-lookup"><span data-stu-id="18ed5-102">How to: Create a Reflection</span></span>
<span data-ttu-id="18ed5-103">Este exemplo mostra como usar um <xref:System.Windows.Media.VisualBrush> para criar um reflexo.</span><span class="sxs-lookup"><span data-stu-id="18ed5-103">This example shows how to use a <xref:System.Windows.Media.VisualBrush> to create a reflection.</span></span> <span data-ttu-id="18ed5-104">Porque um <xref:System.Windows.Media.VisualBrush> pode exibir um elemento visual existente, você pode usar esse recurso para produzir efeitos visuais interessantes, como reflexões e ampliações.</span><span class="sxs-lookup"><span data-stu-id="18ed5-104">Because a <xref:System.Windows.Media.VisualBrush> can display an existing visual, you can use this capability to produce interesting visual effects, such as reflections and magnification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18ed5-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="18ed5-105">Example</span></span>  
 <span data-ttu-id="18ed5-106">O exemplo a seguir usa uma <xref:System.Windows.Media.VisualBrush> para criar um reflexo de um <xref:System.Windows.Controls.Border> que contém vários elementos.</span><span class="sxs-lookup"><span data-stu-id="18ed5-106">The following example uses a <xref:System.Windows.Media.VisualBrush> to create a reflection of a <xref:System.Windows.Controls.Border> that contains several elements.</span></span> <span data-ttu-id="18ed5-107">A ilustração a seguir mostra a saída que esse exemplo produz.</span><span class="sxs-lookup"><span data-stu-id="18ed5-107">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="18ed5-108">![Um objeto Visual de refletidas](./media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")</span><span class="sxs-lookup"><span data-stu-id="18ed5-108">![A reflected Visual object](./media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")</span></span>  
<span data-ttu-id="18ed5-109">Um objeto visual refletido</span><span class="sxs-lookup"><span data-stu-id="18ed5-109">A reflected Visual object</span></span>  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 <span data-ttu-id="18ed5-110">Para o exemplo completo, que inclui exemplos que mostram como ampliar partes da tela e como criar reflexões, consulte [exemplo de VisualBrush](https://go.microsoft.com/fwlink/?LinkID=160049).</span><span class="sxs-lookup"><span data-stu-id="18ed5-110">For the complete sample, which includes examples that show how to magnify parts of the screen and how to create reflections, see [VisualBrush Sample](https://go.microsoft.com/fwlink/?LinkID=160049).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18ed5-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="18ed5-111">See also</span></span>

- <xref:System.Windows.Media.VisualBrush>
- [<span data-ttu-id="18ed5-112">Pintando com imagens, desenhos e visuais</span><span class="sxs-lookup"><span data-stu-id="18ed5-112">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
