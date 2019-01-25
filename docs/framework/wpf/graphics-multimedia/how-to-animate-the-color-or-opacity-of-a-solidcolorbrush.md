---
title: 'Como: Animar a cor ou a opacidade de um SolidColorBrush'
ms.date: 03/30/2017
helpviewer_keywords:
- SolidColorBrush [WPF], animating color of
- colors [WPF], animating
- opacity [WPF], animating
- animation [WPF], color of SolidColorBrush
- animation [WPF], opacity of SolidColorBrush
- SolidColorBrush [WPF], animating opacity of
ms.assetid: d9154354-843f-4713-bad1-35bb0ba6eaeb
ms.openlocfilehash: a6bd7f27f1cce6169181640bb52edad4a493c228
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54738687"
---
# <a name="how-to-animate-the-color-or-opacity-of-a-solidcolorbrush"></a><span data-ttu-id="6bf46-102">Como: Animar a cor ou a opacidade de um SolidColorBrush</span><span class="sxs-lookup"><span data-stu-id="6bf46-102">How to: Animate the Color or Opacity of a SolidColorBrush</span></span>
<span data-ttu-id="6bf46-103">Este exemplo mostra como animar a <xref:System.Windows.Media.SolidColorBrush.Color%2A> e <xref:System.Windows.Media.Brush.Opacity%2A> de um <xref:System.Windows.Media.SolidColorBrush>.</span><span class="sxs-lookup"><span data-stu-id="6bf46-103">This example shows how to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> and <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.SolidColorBrush>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6bf46-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6bf46-104">Example</span></span>  
 <span data-ttu-id="6bf46-105">O exemplo a seguir usa três animações para animar a <xref:System.Windows.Media.SolidColorBrush.Color%2A> e <xref:System.Windows.Media.Brush.Opacity%2A> de um <xref:System.Windows.Media.SolidColorBrush>.</span><span class="sxs-lookup"><span data-stu-id="6bf46-105">The following example uses three animations to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> and <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.SolidColorBrush>.</span></span>  
  
-   <span data-ttu-id="6bf46-106">A primeira animação, um <xref:System.Windows.Media.Animation.ColorAnimation>, altera a cor do pincel para <xref:System.Windows.Media.Colors.Gray%2A> quando o mouse entra no retângulo.</span><span class="sxs-lookup"><span data-stu-id="6bf46-106">The first animation, a <xref:System.Windows.Media.Animation.ColorAnimation>, changes the brush's color to <xref:System.Windows.Media.Colors.Gray%2A> when the mouse enters the rectangle.</span></span>  
  
-   <span data-ttu-id="6bf46-107">A próxima animação, outro <xref:System.Windows.Media.Animation.ColorAnimation>, altera a cor do pincel para <xref:System.Windows.Media.Colors.Orange%2A> quando o mouse sai do retângulo.</span><span class="sxs-lookup"><span data-stu-id="6bf46-107">The next animation, another <xref:System.Windows.Media.Animation.ColorAnimation>, changes the brush's color to <xref:System.Windows.Media.Colors.Orange%2A> when the mouse leaves the rectangle.</span></span>  
  
-   <span data-ttu-id="6bf46-108">A animação final, um <xref:System.Windows.Media.Animation.DoubleAnimation>, altera a opacidade do pincel como 0,0, quando o botão esquerdo do mouse é pressionado.</span><span class="sxs-lookup"><span data-stu-id="6bf46-108">The final animation, a <xref:System.Windows.Media.Animation.DoubleAnimation>, changes the brush's opacity to 0.0 when the left mouse button is pressed.</span></span>  
  
 [!code-csharp[brushanimations_snip#SolidColorBrushAnimationExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushanimations_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushanimationexample)]  
  
 <span data-ttu-id="6bf46-109">Para obter um exemplo mais completo, que mostra como animar diferentes tipos de pincéis, consulte o [exemplo de pincéis](https://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="6bf46-109">For a more complete sample, which shows how to animate different types of brushes, see the [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="6bf46-110">Para mais informações sobre animação, consulte [Visão Geral de Animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6bf46-110">For more information about animation, see the [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span>  
  
 <span data-ttu-id="6bf46-111">Para consistência com outros exemplos de animação, as versões de código deste exemplo usam um <xref:System.Windows.Media.Animation.Storyboard> objeto para aplicar suas animações.</span><span class="sxs-lookup"><span data-stu-id="6bf46-111">For consistency with other animation examples, the code versions of this example use a <xref:System.Windows.Media.Animation.Storyboard> object to apply their animations.</span></span> <span data-ttu-id="6bf46-112">No entanto, ao aplicar uma única animação no código, é mais simples usar o <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> método em vez de usar um <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="6bf46-112">However, when applying a single animation in code, it's simpler to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method instead of using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="6bf46-113">Para obter um exemplo, consulte [Animar uma propriedade sem usar um storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="6bf46-113">For an example, see [Animate a Property Without Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bf46-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6bf46-114">See also</span></span>
- [<span data-ttu-id="6bf46-115">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="6bf46-115">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="6bf46-116">Visão geral de storyboards</span><span class="sxs-lookup"><span data-stu-id="6bf46-116">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
- [<span data-ttu-id="6bf46-117">Exemplo de pincéis</span><span class="sxs-lookup"><span data-stu-id="6bf46-117">Brushes Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159973)
