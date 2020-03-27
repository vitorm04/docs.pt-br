---
title: Como animar uma geometria de retângulo usando quadros-chave
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating RectangleGeometry objects with
- RectangleGeometry objects [WPF], animating with key frames
- animation [WPF], RectangleGeometry objects with key frames
ms.assetid: a8b45ceb-0e32-4ba1-928f-df6d30db17c6
ms.openlocfilehash: bcc9e7f198b8a20ffe13daf6508fb8a735937652
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344688"
---
# <a name="how-to-animate-a-rectangle-geometry-by-using-key-frames"></a><span data-ttu-id="e2b81-102">Como animar uma geometria de retângulo usando quadros-chave</span><span class="sxs-lookup"><span data-stu-id="e2b81-102">How to: Animate a Rectangle Geometry by Using Key Frames</span></span>
<span data-ttu-id="e2b81-103">Este exemplo mostra como <xref:System.Windows.Media.RectangleGeometry.Rect%2A> animar a <xref:System.Windows.Media.RectangleGeometry> propriedade de a usando quadros-chave.</span><span class="sxs-lookup"><span data-stu-id="e2b81-103">This example shows how to animate the <xref:System.Windows.Media.RectangleGeometry.Rect%2A> property of a <xref:System.Windows.Media.RectangleGeometry> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2b81-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e2b81-104">Example</span></span>  
 <span data-ttu-id="e2b81-105">O exemplo a <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> seguir usa <xref:System.Windows.Media.RectangleGeometry.Rect%2A> a classe <xref:System.Windows.Media.RectangleGeometry>para animar a propriedade de um .</span><span class="sxs-lookup"><span data-stu-id="e2b81-105">The following example uses the <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.RectangleGeometry.Rect%2A> property of a <xref:System.Windows.Media.RectangleGeometry>.</span></span> <span data-ttu-id="e2b81-106">Essa animação usa três quadros-chave da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="e2b81-106">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="e2b81-107">Durante os dois primeiros segundos, <xref:System.Windows.Media.Animation.LinearRectKeyFrame> usa uma instância da classe para animar uma mudança gradual na posição, largura e altura de um retângulo.</span><span class="sxs-lookup"><span data-stu-id="e2b81-107">During the first two seconds, uses an instance of the <xref:System.Windows.Media.Animation.LinearRectKeyFrame> class to animate a gradual change in the position, width, and height of a rectangle.</span></span> <span data-ttu-id="e2b81-108">Quadros de <xref:System.Windows.Media.Animation.LinearRectKeyFrame> chaves lineares como criar uma transição linear suave entre os valores.</span><span class="sxs-lookup"><span data-stu-id="e2b81-108">Linear key frames like <xref:System.Windows.Media.Animation.LinearRectKeyFrame> create a smooth linear transition between values.</span></span>  
  
2. <span data-ttu-id="e2b81-109">Durante o final do segundo seguinte, usa <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> uma instância da classe para diminuir repentinamente a altura do retângulo.</span><span class="sxs-lookup"><span data-stu-id="e2b81-109">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> class to suddenly decrease the height of the rectangle.</span></span> <span data-ttu-id="e2b81-110">Quadros-chave discretos <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> como criar mudanças bruscas entre os valores, ou seja, a diminuição da altura ocorre rapidamente e não é sutil.</span><span class="sxs-lookup"><span data-stu-id="e2b81-110">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> create sudden changes between values, that is, the decrease in height occurs quickly and is not subtle.</span></span>  
  
3. <span data-ttu-id="e2b81-111">Durante os dois segundos finais, <xref:System.Windows.Media.Animation.SplineRectKeyFrame> usa uma instância da classe para alterar o retângulo de volta ao seu tamanho e posição originais.</span><span class="sxs-lookup"><span data-stu-id="e2b81-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineRectKeyFrame> class to change the rectangle back to its original size and position.</span></span> <span data-ttu-id="e2b81-112">Quadros-chave spline como <xref:System.Windows.Media.Animation.SplineRectKeyFrame> criar uma transição variável <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A> entre valores de acordo com os valores da propriedade.</span><span class="sxs-lookup"><span data-stu-id="e2b81-112">Spline key frames like <xref:System.Windows.Media.Animation.SplineRectKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="e2b81-113">Neste exemplo, a alteração começa lentamente e acelera exponencialmente na direção do final do segmento de tempo.</span><span class="sxs-lookup"><span data-stu-id="e2b81-113">In this example, the change begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/RectAnimationUsingKeyFramesExample.cs#rectanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/rectanimationusingkeyframesexample.vb#rectanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/RectAnimationUsingKeyFramesExample.xaml#rectanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="e2b81-114">Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="e2b81-114">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2b81-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="e2b81-115">See also</span></span>

- <xref:System.Windows.Media.RectangleGeometry>
- <xref:System.Windows.Media.RectangleGeometry.Rect%2A>
- <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>
- [<span data-ttu-id="e2b81-116">Visão geral das animações de quadro-chave</span><span class="sxs-lookup"><span data-stu-id="e2b81-116">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="e2b81-117">Tópicos explicativos sobre quadros-chave</span><span class="sxs-lookup"><span data-stu-id="e2b81-117">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
