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
ms.openlocfilehash: 9b4a620ea58026c3be1b09d01a595e965e4c2b45
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46002938"
---
# <a name="how-to-animate-a-rectangle-geometry-by-using-key-frames"></a><span data-ttu-id="a2f1d-102">Como animar uma geometria de retângulo usando quadros-chave</span><span class="sxs-lookup"><span data-stu-id="a2f1d-102">How to: Animate a Rectangle Geometry by Using Key Frames</span></span>
<span data-ttu-id="a2f1d-103">Este exemplo mostra como animar a <xref:System.Windows.Media.RectangleGeometry.Rect%2A> propriedade de um <xref:System.Windows.Media.RectangleGeometry> usando quadros-chave.</span><span class="sxs-lookup"><span data-stu-id="a2f1d-103">This example shows how to animate the <xref:System.Windows.Media.RectangleGeometry.Rect%2A> property of a <xref:System.Windows.Media.RectangleGeometry> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2f1d-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a2f1d-104">Example</span></span>  
 <span data-ttu-id="a2f1d-105">O exemplo a seguir usa o <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> classe para animar a <xref:System.Windows.Media.RectangleGeometry.Rect%2A> propriedade de um <xref:System.Windows.Media.RectangleGeometry>.</span><span class="sxs-lookup"><span data-stu-id="a2f1d-105">The following example uses the <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.RectangleGeometry.Rect%2A> property of a <xref:System.Windows.Media.RectangleGeometry>.</span></span> <span data-ttu-id="a2f1d-106">Essa animação usa três quadros-chave da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="a2f1d-106">This animation uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="a2f1d-107">Durante os primeiros dois segundos, usa uma instância da <xref:System.Windows.Media.Animation.LinearRectKeyFrame> classe para animar uma alteração gradual na posição, largura e altura de um retângulo.</span><span class="sxs-lookup"><span data-stu-id="a2f1d-107">During the first two seconds, uses an instance of the <xref:System.Windows.Media.Animation.LinearRectKeyFrame> class to animate a gradual change in the position, width, and height of a rectangle.</span></span> <span data-ttu-id="a2f1d-108">Quadros-chave lineares como <xref:System.Windows.Media.Animation.LinearRectKeyFrame> criam uma transição linear suave entre valores.</span><span class="sxs-lookup"><span data-stu-id="a2f1d-108">Linear key frames like <xref:System.Windows.Media.Animation.LinearRectKeyFrame> create a smooth linear transition between values.</span></span>  
  
2.  <span data-ttu-id="a2f1d-109">Durante o final do próximo meio segundo, usa uma instância da <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> classe para diminuir repentinamente a altura do retângulo.</span><span class="sxs-lookup"><span data-stu-id="a2f1d-109">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> class to suddenly decrease the height of the rectangle.</span></span> <span data-ttu-id="a2f1d-110">Quadros chave discretos como <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> criam alterações repentinas entre valores, ou seja, a redução de altura ocorre rapidamente e não é sutil.</span><span class="sxs-lookup"><span data-stu-id="a2f1d-110">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> create sudden changes between values, that is, the decrease in height occurs quickly and is not subtle.</span></span>  
  
3.  <span data-ttu-id="a2f1d-111">Durante os dois segundos finais, usa uma instância da <xref:System.Windows.Media.Animation.SplineRectKeyFrame> classe para alterar o retângulo de volta para seu tamanho e posição originais.</span><span class="sxs-lookup"><span data-stu-id="a2f1d-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineRectKeyFrame> class to change the rectangle back to its original size and position.</span></span> <span data-ttu-id="a2f1d-112">Como quadros-chave spline <xref:System.Windows.Media.Animation.SplineRectKeyFrame> criam uma transição variável entre valores de acordo com os valores da <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="a2f1d-112">Spline key frames like <xref:System.Windows.Media.Animation.SplineRectKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="a2f1d-113">Neste exemplo, a alteração começa lentamente e acelera exponencialmente na direção do final do segmento de tempo.</span><span class="sxs-lookup"><span data-stu-id="a2f1d-113">In this example, the change begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/RectAnimationUsingKeyFramesExample.cs#rectanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/rectanimationusingkeyframesexample.vb#rectanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/RectAnimationUsingKeyFramesExample.xaml#rectanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="a2f1d-114">Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="a2f1d-114">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2f1d-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a2f1d-115">See Also</span></span>  
 <xref:System.Windows.Media.RectangleGeometry>  
 <xref:System.Windows.Media.RectangleGeometry.Rect%2A>  
 <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>  
 [<span data-ttu-id="a2f1d-116">Visão geral das animações de quadro-chave</span><span class="sxs-lookup"><span data-stu-id="a2f1d-116">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="a2f1d-117">Tópicos explicativos sobre quadros-chave</span><span class="sxs-lookup"><span data-stu-id="a2f1d-117">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
