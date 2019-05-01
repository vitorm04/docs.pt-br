---
title: 'Como: Animar um ponto usando quadros principais'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating Points with
- Points [WPF], animating with key frames
- animation [WPF], Points with key frames
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
ms.openlocfilehash: b706568a0e8221aac737780592882f728f0f9e9c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62010157"
---
# <a name="how-to-animate-a-point-by-using-key-frames"></a><span data-ttu-id="a8a3e-102">Como: Animar um ponto usando quadros principais</span><span class="sxs-lookup"><span data-stu-id="a8a3e-102">How to: Animate a Point by Using Key Frames</span></span>
<span data-ttu-id="a8a3e-103">Este exemplo mostra como usar o <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> classe para animar um <xref:System.Windows.Point>.</span><span class="sxs-lookup"><span data-stu-id="a8a3e-103">This example shows how to use the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> class to animate a <xref:System.Windows.Point>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8a3e-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a8a3e-104">Example</span></span>  
 <span data-ttu-id="a8a3e-105">O exemplo a seguir move uma elipse ao longo de um caminho triangular.</span><span class="sxs-lookup"><span data-stu-id="a8a3e-105">The following example moves an ellipse along a triangular path.</span></span> <span data-ttu-id="a8a3e-106">O exemplo usa o <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> classe para animar a <xref:System.Windows.Media.EllipseGeometry.Center%2A> propriedade de um <xref:System.Windows.Media.EllipseGeometry>.</span><span class="sxs-lookup"><span data-stu-id="a8a3e-106">The example uses the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.EllipseGeometry.Center%2A> property of an <xref:System.Windows.Media.EllipseGeometry>.</span></span> <span data-ttu-id="a8a3e-107">Essa animação usa três quadros-chave da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="a8a3e-107">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="a8a3e-108">Durante o primeiro meio segundo, usa uma instância da <xref:System.Windows.Media.Animation.LinearPointKeyFrame> classe para mover a elipse ao longo de um caminho a uma taxa constante de sua posição inicial.</span><span class="sxs-lookup"><span data-stu-id="a8a3e-108">During the first half second, uses an instance of the <xref:System.Windows.Media.Animation.LinearPointKeyFrame> class to move the ellipse along a path at a steady rate from its starting position.</span></span> <span data-ttu-id="a8a3e-109">Quadros-chave lineares como <xref:System.Windows.Media.Animation.LinearPointKeyFrame> criam uma interpolação linear suave entre valores.</span><span class="sxs-lookup"><span data-stu-id="a8a3e-109">Linear key frames like <xref:System.Windows.Media.Animation.LinearPointKeyFrame> create a smooth linear interpolation between values.</span></span>  
  
2. <span data-ttu-id="a8a3e-110">Durante o final do próximo meio segundo, usa uma instância da <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> classe para mover repentinamente a elipse ao longo do caminho para a próxima posição.</span><span class="sxs-lookup"><span data-stu-id="a8a3e-110">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> class to suddenly move the ellipse along the path to the next position.</span></span> <span data-ttu-id="a8a3e-111">Quadros chave discretos como <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> criam saltos repentinos entre valores.</span><span class="sxs-lookup"><span data-stu-id="a8a3e-111">Discrete key frames like <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> create sudden jumps between values.</span></span>  
  
3. <span data-ttu-id="a8a3e-112">Durante os dois segundos finais, usa uma instância da <xref:System.Windows.Media.Animation.SplinePointKeyFrame> classe para mover a elipse de volta para sua posição inicial.</span><span class="sxs-lookup"><span data-stu-id="a8a3e-112">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplinePointKeyFrame> class to move the ellipse back to its starting position.</span></span> <span data-ttu-id="a8a3e-113">Como quadros-chave spline <xref:System.Windows.Media.Animation.SplinePointKeyFrame> criam uma transição variável entre valores de acordo com os valores da <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="a8a3e-113">Spline key frames like <xref:System.Windows.Media.Animation.SplinePointKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="a8a3e-114">Neste exemplo, a animação começa lentamente e acelera exponencialmente na direção do final do segmento de tempo.</span><span class="sxs-lookup"><span data-stu-id="a8a3e-114">In this example, the animation begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="a8a3e-115">Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="a8a3e-115">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
 <span data-ttu-id="a8a3e-116">Para consistência com outros exemplos de animação, as versões de código deste exemplo usam um <xref:System.Windows.Media.Animation.Storyboard> objeto ao qual aplicar o <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>.</span><span class="sxs-lookup"><span data-stu-id="a8a3e-116">For consistency with other animation examples, the code versions of this example use a <xref:System.Windows.Media.Animation.Storyboard> object to apply the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>.</span></span> <span data-ttu-id="a8a3e-117">No entanto, ao aplicar uma única animação no código, é mais simples usar o <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> método em vez de usar um <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="a8a3e-117">However, when applying a single animation in code, it's simpler to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method instead of using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="a8a3e-118">Para obter um exemplo, consulte [Animar uma propriedade sem usar um storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="a8a3e-118">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8a3e-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a8a3e-119">See also</span></span>

- <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>
- <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=nameWithType>
- <xref:System.Windows.Media.EllipseGeometry>
- [<span data-ttu-id="a8a3e-120">Visão geral das animações de quadro-chave</span><span class="sxs-lookup"><span data-stu-id="a8a3e-120">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="a8a3e-121">Tópicos explicativos sobre quadros-chave</span><span class="sxs-lookup"><span data-stu-id="a8a3e-121">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
