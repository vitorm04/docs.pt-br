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
ms.openlocfilehash: fcbb546b64810416d3f7dbe052da77b7bc941e7a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43395317"
---
# <a name="how-to-animate-the-position-or-color-of-a-gradient-stop"></a><span data-ttu-id="4e4af-102">Como animar a posição ou cor de uma marca de gradiente</span><span class="sxs-lookup"><span data-stu-id="4e4af-102">How to: Animate the Position or Color of a Gradient Stop</span></span>
<span data-ttu-id="4e4af-103">Este exemplo mostra como animar a <xref:System.Windows.Media.GradientStop.Color%2A> e <xref:System.Windows.Media.GradientStop.Offset%2A> de <xref:System.Windows.Media.GradientStop> objetos.</span><span class="sxs-lookup"><span data-stu-id="4e4af-103">This example shows how to animate the <xref:System.Windows.Media.GradientStop.Color%2A> and <xref:System.Windows.Media.GradientStop.Offset%2A> of <xref:System.Windows.Media.GradientStop> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e4af-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4e4af-104">Example</span></span>  
 <span data-ttu-id="4e4af-105">O exemplo a seguir anima três marcas de gradiente dentro de um <xref:System.Windows.Media.LinearGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="4e4af-105">The following example animates three gradient stops inside a <xref:System.Windows.Media.LinearGradientBrush>.</span></span> <span data-ttu-id="4e4af-106">O exemplo usa três animações, cada qual animando uma marca de gradiente diferente:</span><span class="sxs-lookup"><span data-stu-id="4e4af-106">The example uses three animations, each of which animates a different gradient stop:</span></span>  
  
-   <span data-ttu-id="4e4af-107">A primeira animação, um <xref:System.Windows.Media.Animation.DoubleAnimation>, anima a primeira parada gradiente <xref:System.Windows.Media.GradientStop.Offset%2A> de 0,0 a 1,0 e, em seguida, volta a 0.0.</span><span class="sxs-lookup"><span data-stu-id="4e4af-107">The first animation, a <xref:System.Windows.Media.Animation.DoubleAnimation>, animates the first gradient stop's <xref:System.Windows.Media.GradientStop.Offset%2A> from 0.0 to 1.0 and then back to 0.0.</span></span> <span data-ttu-id="4e4af-108">Como resultado, a primeira cor do gradiente muda do lado esquerdo para o lado direito do retângulo e, em seguida, volta para o lado esquerdo.</span><span class="sxs-lookup"><span data-stu-id="4e4af-108">As a result, the first color in the gradient shifts from the left side to the right side of the rectangle and then back to the left side.</span></span>  
  
-   <span data-ttu-id="4e4af-109">A segunda animação, um <xref:System.Windows.Media.Animation.ColorAnimation>, anima a parada de gradiente segundo <xref:System.Windows.Media.GradientStop.Color%2A> partir <xref:System.Windows.Media.Colors.Purple%2A> para <xref:System.Windows.Media.Colors.Yellow%2A> e, em seguida, de volta para <xref:System.Windows.Media.Colors.Purple%2A>.</span><span class="sxs-lookup"><span data-stu-id="4e4af-109">The second animation, a <xref:System.Windows.Media.Animation.ColorAnimation>, animates the second gradient stop's <xref:System.Windows.Media.GradientStop.Color%2A> from <xref:System.Windows.Media.Colors.Purple%2A> to <xref:System.Windows.Media.Colors.Yellow%2A> and then back to <xref:System.Windows.Media.Colors.Purple%2A>.</span></span> <span data-ttu-id="4e4af-110">Como resultado, a cor intermediária do gradiente muda de roxo para amarelo e de volta para roxo.</span><span class="sxs-lookup"><span data-stu-id="4e4af-110">As a result, the middle color in the gradient changes from purple to yellow and back to purple.</span></span>  
  
-   <span data-ttu-id="4e4af-111">A terceira animação, outro <xref:System.Windows.Media.Animation.ColorAnimation>, anima a opacidade da parada de gradiente terceiro <xref:System.Windows.Media.GradientStop.Color%2A> por -1 e, em seguida, de volta.</span><span class="sxs-lookup"><span data-stu-id="4e4af-111">The third animation, another <xref:System.Windows.Media.Animation.ColorAnimation>, animates the opacity of the third gradient stop's <xref:System.Windows.Media.GradientStop.Color%2A> by -1 and then back.</span></span> <span data-ttu-id="4e4af-112">Como resultado, a terceira cor do gradiente desaparece e, em seguida, se torna opaca novamente.</span><span class="sxs-lookup"><span data-stu-id="4e4af-112">As a result, the third color in the gradient fades away and then becomes opaque again.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 <span data-ttu-id="4e4af-113">Embora este exemplo usa uma <xref:System.Windows.Media.LinearGradientBrush>, o processo é o mesmo para animar <xref:System.Windows.Media.GradientStop> objetos dentro de um <xref:System.Windows.Media.RadialGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="4e4af-113">Although this example uses a <xref:System.Windows.Media.LinearGradientBrush>, the process is the same for animating <xref:System.Windows.Media.GradientStop> objects inside a <xref:System.Windows.Media.RadialGradientBrush>.</span></span>  
  
 <span data-ttu-id="4e4af-114">Para obter exemplos adicionais, consulte o [Exemplo de pincéis](https://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="4e4af-114">For additional examples, see the [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e4af-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4e4af-115">See Also</span></span>  
 <xref:System.Windows.Media.GradientStop>  
 [<span data-ttu-id="4e4af-116">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="4e4af-116">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="4e4af-117">Visão geral de storyboards</span><span class="sxs-lookup"><span data-stu-id="4e4af-117">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
