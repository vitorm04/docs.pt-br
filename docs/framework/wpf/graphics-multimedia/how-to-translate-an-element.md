---
title: Como converter um elemento
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], translations
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
ms.openlocfilehash: 04e1e8288bcccc4a310f05abff01fbdf160cdb11
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43420997"
---
# <a name="how-to-translate-an-element"></a><span data-ttu-id="75de8-102">Como converter um elemento</span><span class="sxs-lookup"><span data-stu-id="75de8-102">How to: Translate an Element</span></span>
<span data-ttu-id="75de8-103">Este exemplo mostra como mover (translação) um elemento usando um <xref:System.Windows.Media.TranslateTransform>.</span><span class="sxs-lookup"><span data-stu-id="75de8-103">This example shows how to translate (move) an element by using a <xref:System.Windows.Media.TranslateTransform>.</span></span>  
  
 <span data-ttu-id="75de8-104">O <xref:System.Windows.Media.TranslateTransform> classe é especialmente útil para mover elementos dentro de painéis que não dão suporte ao posicionamento absoluto.</span><span class="sxs-lookup"><span data-stu-id="75de8-104">The <xref:System.Windows.Media.TranslateTransform> class is especially useful for moving elements inside panels that do not support absolute positioning.</span></span> <span data-ttu-id="75de8-105">Por exemplo, aplicando uma <xref:System.Windows.Media.TranslateTransform> para o <xref:System.Windows.UIElement.RenderTransform%2A> propriedade de um elemento, você pode mover um elemento dentro de uma <xref:System.Windows.Controls.StackPanel> ou <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="75de8-105">For example, by applying a <xref:System.Windows.Media.TranslateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of an element, you can move an element within a <xref:System.Windows.Controls.StackPanel> or <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
 <span data-ttu-id="75de8-106">Use o <xref:System.Windows.Media.TranslateTransform.X%2A> propriedade do <xref:System.Windows.Media.TranslateTransform> para especificar a quantidade, em pixels, para mover o elemento ao longo do eixo x.</span><span class="sxs-lookup"><span data-stu-id="75de8-106">Use the <xref:System.Windows.Media.TranslateTransform.X%2A> property of the <xref:System.Windows.Media.TranslateTransform> to specify the amount, in pixels, to move the element along the x-axis.</span></span> <span data-ttu-id="75de8-107">Use o <xref:System.Windows.Media.TranslateTransform.Y%2A> propriedade para especificar a quantidade, em pixels, para mover o elemento ao longo do eixo y.</span><span class="sxs-lookup"><span data-stu-id="75de8-107">Use the <xref:System.Windows.Media.TranslateTransform.Y%2A> property to specify the amount, in pixels, to move the element along the y-axis.</span></span> <span data-ttu-id="75de8-108">Por fim, aplique a <xref:System.Windows.Media.TranslateTransform> para o <xref:System.Windows.UIElement.RenderTransform%2A> propriedade do elemento.</span><span class="sxs-lookup"><span data-stu-id="75de8-108">Finally, apply the <xref:System.Windows.Media.TranslateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span>  
  
 <span data-ttu-id="75de8-109">O exemplo a seguir usa um <xref:System.Windows.Media.TranslateTransform> para mover o elemento 50 pixels para as direita e 50 pixels para baixo.</span><span class="sxs-lookup"><span data-stu-id="75de8-109">The following example uses a <xref:System.Windows.Media.TranslateTransform> to move an element 50 pixels to the right and 50 pixels down.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75de8-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="75de8-110">Example</span></span>  
 [!code-xaml[transformsSample#53](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 <span data-ttu-id="75de8-111">Para obter o exemplo completo, consulte [Amostras de Transformação 2D](https://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="75de8-111">For the complete sample, see [2-D Transforms Sample](https://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75de8-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="75de8-112">See Also</span></span>  
 [<span data-ttu-id="75de8-113">Visão geral de transformações</span><span class="sxs-lookup"><span data-stu-id="75de8-113">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
