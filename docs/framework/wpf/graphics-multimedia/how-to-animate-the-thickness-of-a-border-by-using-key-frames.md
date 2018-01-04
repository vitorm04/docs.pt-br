---
title: Como animar a espessura de uma borda usando quadros-chave
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], border thickness with key frames
- key frames [WPF], animating border thickness with
- border thickness [WPF], animating with key frames
ms.assetid: 3a9cb463-0a63-407d-aae7-3fbb1a559947
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0f255ff38ec7ee79f02a0cd40a3f0143c36e1c58
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-the-thickness-of-a-border-by-using-key-frames"></a><span data-ttu-id="a8356-102">Como animar a espessura de uma borda usando quadros-chave</span><span class="sxs-lookup"><span data-stu-id="a8356-102">How to: Animate the Thickness of a Border by Using Key Frames</span></span>
<span data-ttu-id="a8356-103">Este exemplo mostra como animar a <xref:System.Windows.Controls.Control.BorderThickness%2A> propriedade de um <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="a8356-103">This example shows how to animate the <xref:System.Windows.Controls.Control.BorderThickness%2A> property of a <xref:System.Windows.Controls.Border>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8356-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a8356-104">Example</span></span>  
 <span data-ttu-id="a8356-105">O exemplo a seguir usa o <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> classe para animar a <xref:System.Windows.Controls.Control.BorderThickness%2A> propriedade de um <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="a8356-105">The following example uses the <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Controls.Control.BorderThickness%2A> property of a <xref:System.Windows.Controls.Border>.</span></span> <span data-ttu-id="a8356-106">Essa animação usa três quadros-chave da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="a8356-106">This animation uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="a8356-107">Durante a primeira metade de segundo, usa uma instância do <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> classe gradualmente aumentar a espessura da borda.</span><span class="sxs-lookup"><span data-stu-id="a8356-107">During the first half second, uses an instance of the <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> class to gradually increase the thickness of the border.</span></span> <span data-ttu-id="a8356-108">O exemplo usa <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> para criar um aumento linear suave entre valores.</span><span class="sxs-lookup"><span data-stu-id="a8356-108">The example uses <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> to create a smooth linear increase between values.</span></span>  
  
2.  <span data-ttu-id="a8356-109">No final do próximo meio segundo, usa uma instância do <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> classe para aumentar a espessura da borda repentinamente.</span><span class="sxs-lookup"><span data-stu-id="a8356-109">At the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> class to suddenly increase the thickness of the border.</span></span> <span data-ttu-id="a8356-110">Quadros chave discretos, como aqueles que são derivam de <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> criar saltos repentinos entre valores, ou seja, a movimentação da animação é uma.</span><span class="sxs-lookup"><span data-stu-id="a8356-110">Discrete key frames like those derived from <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
3.  <span data-ttu-id="a8356-111">Durante os últimos dois segundos, usa uma instância do <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> classe para diminuir a espessura da borda.</span><span class="sxs-lookup"><span data-stu-id="a8356-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> class to decrease the thickness of the border.</span></span> <span data-ttu-id="a8356-112">Quadros chave de spline como aqueles que são derivados de <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> criar uma transição de variável entre valores de acordo com os valores de <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="a8356-112">Spline key frames like those derived from <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="a8356-113">Neste quadro-chave, a animação começa lentamente e acelera exponencialmente na direção do final do segmento de tempo.</span><span class="sxs-lookup"><span data-stu-id="a8356-113">In this key frame, the animation starts off slow and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-xaml[keyframes_snip#ThicknessAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ThicknessAnimationUsingKeyFramesExample.xaml#thicknessanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="a8356-114">Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](http://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="a8356-114">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8356-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a8356-115">See Also</span></span>  
 <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>  
 [<span data-ttu-id="a8356-116">Visão geral das animações de quadro-chave</span><span class="sxs-lookup"><span data-stu-id="a8356-116">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="a8356-117">Tópicos explicativos sobre quadros-chave</span><span class="sxs-lookup"><span data-stu-id="a8356-117">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)  
 [<span data-ttu-id="a8356-118">Animar um valor de BorderThickness</span><span class="sxs-lookup"><span data-stu-id="a8356-118">Animate a BorderThickness Value</span></span>](../../../../docs/framework/wpf/controls/how-to-animate-a-borderthickness-value.md)
