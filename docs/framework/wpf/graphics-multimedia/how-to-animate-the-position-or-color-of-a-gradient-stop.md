---
title: Como animar a posição ou cor de uma marca de gradiente
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- position [WPF], animating
- animation [WPF], position of GradientStop objects
- GradientStop objects [WPF], animating color of
- colors [WPF], animating
- animation [WPF], color of GradientStop objects
- GradientStop objects [WPF], animating position of
ms.assetid: 6f5b8b47-6c32-4b8e-98ee-fdf6515ec843
ms.openlocfilehash: aeae33f5f3c8016808988f58d61969e9b6f05039
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452838"
---
# <a name="how-to-animate-the-position-or-color-of-a-gradient-stop"></a><span data-ttu-id="3b23f-102">Como animar a posição ou cor de uma marca de gradiente</span><span class="sxs-lookup"><span data-stu-id="3b23f-102">How to: Animate the Position or Color of a Gradient Stop</span></span>
<span data-ttu-id="3b23f-103">Este exemplo mostra como animar o <xref:System.Windows.Media.GradientStop.Color%2A> e <xref:System.Windows.Media.GradientStop.Offset%2A> de objetos <xref:System.Windows.Media.GradientStop>.</span><span class="sxs-lookup"><span data-stu-id="3b23f-103">This example shows how to animate the <xref:System.Windows.Media.GradientStop.Color%2A> and <xref:System.Windows.Media.GradientStop.Offset%2A> of <xref:System.Windows.Media.GradientStop> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b23f-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3b23f-104">Example</span></span>  
 <span data-ttu-id="3b23f-105">O exemplo a seguir anima três paradas de gradientes dentro de um <xref:System.Windows.Media.LinearGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="3b23f-105">The following example animates three gradient stops inside a <xref:System.Windows.Media.LinearGradientBrush>.</span></span> <span data-ttu-id="3b23f-106">O exemplo usa três animações, cada qual animando uma marca de gradiente diferente:</span><span class="sxs-lookup"><span data-stu-id="3b23f-106">The example uses three animations, each of which animates a different gradient stop:</span></span>  
  
- <span data-ttu-id="3b23f-107">A primeira animação, uma <xref:System.Windows.Media.Animation.DoubleAnimation>, anima a <xref:System.Windows.Media.GradientStop.Offset%2A> da primeira parada de gradiente de 0,0 para 1,0 e, em seguida, de volta para 0,0.</span><span class="sxs-lookup"><span data-stu-id="3b23f-107">The first animation, a <xref:System.Windows.Media.Animation.DoubleAnimation>, animates the first gradient stop's <xref:System.Windows.Media.GradientStop.Offset%2A> from 0.0 to 1.0 and then back to 0.0.</span></span> <span data-ttu-id="3b23f-108">Como resultado, a primeira cor do gradiente muda do lado esquerdo para o lado direito do retângulo e, em seguida, volta para o lado esquerdo.</span><span class="sxs-lookup"><span data-stu-id="3b23f-108">As a result, the first color in the gradient shifts from the left side to the right side of the rectangle and then back to the left side.</span></span>  
  
- <span data-ttu-id="3b23f-109">A segunda animação, uma <xref:System.Windows.Media.Animation.ColorAnimation>, anima a segunda <xref:System.Windows.Media.GradientStop.Color%2A> de parada de gradiente de <xref:System.Windows.Media.Colors.Purple%2A> para <xref:System.Windows.Media.Colors.Yellow%2A> e, em seguida, de volta para <xref:System.Windows.Media.Colors.Purple%2A>.</span><span class="sxs-lookup"><span data-stu-id="3b23f-109">The second animation, a <xref:System.Windows.Media.Animation.ColorAnimation>, animates the second gradient stop's <xref:System.Windows.Media.GradientStop.Color%2A> from <xref:System.Windows.Media.Colors.Purple%2A> to <xref:System.Windows.Media.Colors.Yellow%2A> and then back to <xref:System.Windows.Media.Colors.Purple%2A>.</span></span> <span data-ttu-id="3b23f-110">Como resultado, a cor intermediária do gradiente muda de roxo para amarelo e de volta para roxo.</span><span class="sxs-lookup"><span data-stu-id="3b23f-110">As a result, the middle color in the gradient changes from purple to yellow and back to purple.</span></span>  
  
- <span data-ttu-id="3b23f-111">A terceira animação, outra <xref:System.Windows.Media.Animation.ColorAnimation>, anima a opacidade do terceiro <xref:System.Windows.Media.GradientStop.Color%2A> de parada de gradiente por-1 e, em seguida, de volta.</span><span class="sxs-lookup"><span data-stu-id="3b23f-111">The third animation, another <xref:System.Windows.Media.Animation.ColorAnimation>, animates the opacity of the third gradient stop's <xref:System.Windows.Media.GradientStop.Color%2A> by -1 and then back.</span></span> <span data-ttu-id="3b23f-112">Como resultado, a terceira cor do gradiente desaparece e, em seguida, se torna opaca novamente.</span><span class="sxs-lookup"><span data-stu-id="3b23f-112">As a result, the third color in the gradient fades away and then becomes opaque again.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 <span data-ttu-id="3b23f-113">Embora este exemplo use uma <xref:System.Windows.Media.LinearGradientBrush>, o processo é o mesmo para animar <xref:System.Windows.Media.GradientStop> objetos dentro de um <xref:System.Windows.Media.RadialGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="3b23f-113">Although this example uses a <xref:System.Windows.Media.LinearGradientBrush>, the process is the same for animating <xref:System.Windows.Media.GradientStop> objects inside a <xref:System.Windows.Media.RadialGradientBrush>.</span></span>  
  
 <span data-ttu-id="3b23f-114">Para obter exemplos adicionais, consulte o [Exemplo de pincéis](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span><span class="sxs-lookup"><span data-stu-id="3b23f-114">For additional examples, see the [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b23f-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="3b23f-115">See also</span></span>

- <xref:System.Windows.Media.GradientStop>
- [<span data-ttu-id="3b23f-116">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="3b23f-116">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="3b23f-117">Visão geral de storyboards</span><span class="sxs-lookup"><span data-stu-id="3b23f-117">Storyboards Overview</span></span>](storyboards-overview.md)
