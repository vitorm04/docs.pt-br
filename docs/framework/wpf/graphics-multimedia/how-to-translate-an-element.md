---
title: Como converter um elemento
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], translations
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
ms.openlocfilehash: ba6bda09a4ee189cdd1a32eed8f65b32d1a9abe4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187315"
---
# <a name="how-to-translate-an-element"></a><span data-ttu-id="3bc20-102">Como converter um elemento</span><span class="sxs-lookup"><span data-stu-id="3bc20-102">How to: Translate an Element</span></span>
<span data-ttu-id="3bc20-103">Este exemplo mostra como traduzir (mover) <xref:System.Windows.Media.TranslateTransform>um elemento usando um .</span><span class="sxs-lookup"><span data-stu-id="3bc20-103">This example shows how to translate (move) an element by using a <xref:System.Windows.Media.TranslateTransform>.</span></span>  
  
 <span data-ttu-id="3bc20-104">A <xref:System.Windows.Media.TranslateTransform> classe é especialmente útil para mover elementos dentro de painéis que não suportam posicionamento absoluto.</span><span class="sxs-lookup"><span data-stu-id="3bc20-104">The <xref:System.Windows.Media.TranslateTransform> class is especially useful for moving elements inside panels that do not support absolute positioning.</span></span> <span data-ttu-id="3bc20-105">Por exemplo, aplicando <xref:System.Windows.Media.TranslateTransform> um <xref:System.Windows.UIElement.RenderTransform%2A> à propriedade de um elemento, <xref:System.Windows.Controls.StackPanel> você <xref:System.Windows.Controls.DockPanel>pode mover um elemento dentro de um ou .</span><span class="sxs-lookup"><span data-stu-id="3bc20-105">For example, by applying a <xref:System.Windows.Media.TranslateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of an element, you can move an element within a <xref:System.Windows.Controls.StackPanel> or <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
 <span data-ttu-id="3bc20-106">Use <xref:System.Windows.Media.TranslateTransform.X%2A> a propriedade <xref:System.Windows.Media.TranslateTransform> do para especificar a quantidade, em pixels, para mover o elemento ao longo do eixo x.</span><span class="sxs-lookup"><span data-stu-id="3bc20-106">Use the <xref:System.Windows.Media.TranslateTransform.X%2A> property of the <xref:System.Windows.Media.TranslateTransform> to specify the amount, in pixels, to move the element along the x-axis.</span></span> <span data-ttu-id="3bc20-107">Use <xref:System.Windows.Media.TranslateTransform.Y%2A> a propriedade para especificar a quantidade, em pixels, para mover o elemento ao longo do eixo y.</span><span class="sxs-lookup"><span data-stu-id="3bc20-107">Use the <xref:System.Windows.Media.TranslateTransform.Y%2A> property to specify the amount, in pixels, to move the element along the y-axis.</span></span> <span data-ttu-id="3bc20-108">Por fim, <xref:System.Windows.Media.TranslateTransform> aplique <xref:System.Windows.UIElement.RenderTransform%2A> a propriedade do elemento.</span><span class="sxs-lookup"><span data-stu-id="3bc20-108">Finally, apply the <xref:System.Windows.Media.TranslateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span>  
  
 <span data-ttu-id="3bc20-109">O exemplo a <xref:System.Windows.Media.TranslateTransform> seguir usa um para mover um elemento 50 pixels para a direita e 50 pixels para baixo.</span><span class="sxs-lookup"><span data-stu-id="3bc20-109">The following example uses a <xref:System.Windows.Media.TranslateTransform> to move an element 50 pixels to the right and 50 pixels down.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3bc20-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3bc20-110">Example</span></span>  
 [!code-xaml[transformsSample#53](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 <span data-ttu-id="3bc20-111">Para obter o exemplo completo, consulte [Amostras de Transformação 2D](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span><span class="sxs-lookup"><span data-stu-id="3bc20-111">For the complete sample, see [2-D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bc20-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="3bc20-112">See also</span></span>

- [<span data-ttu-id="3bc20-113">Visão geral de transformações</span><span class="sxs-lookup"><span data-stu-id="3bc20-113">Transforms Overview</span></span>](transforms-overview.md)
