---
title: Como animar uma matriz usando quadros-chave
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
ms.openlocfilehash: eb596cf728f8a7cc1964963b8509f42bdd7a392a
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344917"
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a><span data-ttu-id="6d3fa-102">Como animar uma matriz usando quadros-chave</span><span class="sxs-lookup"><span data-stu-id="6d3fa-102">How to: Animate a Matrix by Using Key Frames</span></span>
<span data-ttu-id="6d3fa-103">Este exemplo mostra como <xref:System.Windows.Media.MatrixTransform.Matrix%2A> animar a <xref:System.Windows.Media.MatrixTransform> propriedade de a usando quadros-chave.</span><span class="sxs-lookup"><span data-stu-id="6d3fa-103">This example shows how to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d3fa-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d3fa-104">Example</span></span>  
 <span data-ttu-id="6d3fa-105">O exemplo a <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> seguir usa <xref:System.Windows.Media.MatrixTransform.Matrix%2A> a classe <xref:System.Windows.Media.MatrixTransform>para animar a propriedade de um .</span><span class="sxs-lookup"><span data-stu-id="6d3fa-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="6d3fa-106">O exemplo <xref:System.Windows.Media.MatrixTransform> usa o objeto para transformar <xref:System.Windows.Controls.Button>a aparência e a posição de um .</span><span class="sxs-lookup"><span data-stu-id="6d3fa-106">The example uses the <xref:System.Windows.Media.MatrixTransform> object to transform the appearance and position of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="6d3fa-107">Esta animação <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> usa a classe para criar dois quadros-chave e faz o seguinte com eles:</span><span class="sxs-lookup"><span data-stu-id="6d3fa-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> class to create two key frames and does the following with them:</span></span>  
  
1. <span data-ttu-id="6d3fa-108">Anima o primeiro <xref:System.Windows.Media.Matrix> durante os primeiros 0,2 segundos.</span><span class="sxs-lookup"><span data-stu-id="6d3fa-108">Animates the first <xref:System.Windows.Media.Matrix> during the first 0.2 seconds.</span></span> <span data-ttu-id="6d3fa-109">O exemplo <xref:System.Windows.Media.Matrix.M11%2A> altera <xref:System.Windows.Media.Matrix.M12%2A> as <xref:System.Windows.Media.Matrix>propriedades do .</span><span class="sxs-lookup"><span data-stu-id="6d3fa-109">The example changes the <xref:System.Windows.Media.Matrix.M11%2A> and <xref:System.Windows.Media.Matrix.M12%2A> properties of the <xref:System.Windows.Media.Matrix>.</span></span> <span data-ttu-id="6d3fa-110">Essa alteração faz com que o botão se alongue e fique achatado.</span><span class="sxs-lookup"><span data-stu-id="6d3fa-110">This change causes the button to stretch and become skewed.</span></span> <span data-ttu-id="6d3fa-111">O exemplo também <xref:System.Windows.Media.Matrix.OffsetX%2A> <xref:System.Windows.Media.Matrix.OffsetY%2A> altera as propriedades e propriedades para que o botão mude de posição.</span><span class="sxs-lookup"><span data-stu-id="6d3fa-111">The example also changes the <xref:System.Windows.Media.Matrix.OffsetX%2A> and <xref:System.Windows.Media.Matrix.OffsetY%2A> properties so that the button changes position.</span></span>  
  
2. <span data-ttu-id="6d3fa-112">Anima o segundo <xref:System.Windows.Media.Matrix> em 1,0 segundos.</span><span class="sxs-lookup"><span data-stu-id="6d3fa-112">Animates the second <xref:System.Windows.Media.Matrix> at 1.0 seconds.</span></span> <span data-ttu-id="6d3fa-113">O botão muda para outra posição enquanto o botão não é mais distorcido ou alongado.</span><span class="sxs-lookup"><span data-stu-id="6d3fa-113">The button moves to another position while the button is no longer skewed or stretched.</span></span>  
  
3. <span data-ttu-id="6d3fa-114">Repete a animação indefinidamente.</span><span class="sxs-lookup"><span data-stu-id="6d3fa-114">Repeats the animation indefinitely.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6d3fa-115">Quadros-chave que <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> derivam do objeto criam saltos repentinos entre os valores, ou seja, o movimento da animação é jerky.</span><span class="sxs-lookup"><span data-stu-id="6d3fa-115">Key frames that derive from the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> object create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="6d3fa-116">Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="6d3fa-116">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d3fa-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="6d3fa-117">See also</span></span>

- <xref:System.Windows.Media.MatrixTransform.Matrix%2A>
- <xref:System.Windows.Media.MatrixTransform>
- [<span data-ttu-id="6d3fa-118">Visão geral das animações de quadro-chave</span><span class="sxs-lookup"><span data-stu-id="6d3fa-118">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="6d3fa-119">Tópicos explicativos sobre quadros-chave</span><span class="sxs-lookup"><span data-stu-id="6d3fa-119">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
