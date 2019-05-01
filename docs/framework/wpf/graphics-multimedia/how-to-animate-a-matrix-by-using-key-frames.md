---
title: 'Como: Animar uma matriz usando quadros principais'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
ms.openlocfilehash: ff5320fa5b4441ae3e0f414b274ab9118b77ec50
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62020238"
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a><span data-ttu-id="3f437-102">Como: Animar uma matriz usando quadros principais</span><span class="sxs-lookup"><span data-stu-id="3f437-102">How to: Animate a Matrix by Using Key Frames</span></span>
<span data-ttu-id="3f437-103">Este exemplo mostra como animar a <xref:System.Windows.Media.MatrixTransform.Matrix%2A> propriedade de um <xref:System.Windows.Media.MatrixTransform> usando quadros-chave.</span><span class="sxs-lookup"><span data-stu-id="3f437-103">This example shows how to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f437-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3f437-104">Example</span></span>  
 <span data-ttu-id="3f437-105">O exemplo a seguir usa o <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> classe para animar a <xref:System.Windows.Media.MatrixTransform.Matrix%2A> propriedade de um <xref:System.Windows.Media.MatrixTransform>.</span><span class="sxs-lookup"><span data-stu-id="3f437-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="3f437-106">O exemplo usa o <xref:System.Windows.Media.MatrixTransform> objeto para transformar a aparência e a posição de um <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="3f437-106">The example uses the <xref:System.Windows.Media.MatrixTransform> object to transform the appearance and position of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="3f437-107">Essa animação usa o <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> de classe para criar dois quadros-chave e faz o seguinte com eles:</span><span class="sxs-lookup"><span data-stu-id="3f437-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> class to create two key frames and does the following with them:</span></span>  
  
1. <span data-ttu-id="3f437-108">Anima o primeiro <xref:System.Windows.Media.Matrix> durante o primeiro 0,2 segundo.</span><span class="sxs-lookup"><span data-stu-id="3f437-108">Animates the first <xref:System.Windows.Media.Matrix> during the first 0.2 seconds.</span></span> <span data-ttu-id="3f437-109">O exemplo altera o <xref:System.Windows.Media.Matrix.M11%2A> e <xref:System.Windows.Media.Matrix.M12%2A> propriedades do <xref:System.Windows.Media.Matrix>.</span><span class="sxs-lookup"><span data-stu-id="3f437-109">The example changes the <xref:System.Windows.Media.Matrix.M11%2A> and <xref:System.Windows.Media.Matrix.M12%2A> properties of the <xref:System.Windows.Media.Matrix>.</span></span> <span data-ttu-id="3f437-110">Essa alteração faz com que o botão se alongue e fique achatado.</span><span class="sxs-lookup"><span data-stu-id="3f437-110">This change causes the button to stretch and become skewed.</span></span> <span data-ttu-id="3f437-111">O exemplo também modifica o <xref:System.Windows.Media.Matrix.OffsetX%2A> e <xref:System.Windows.Media.Matrix.OffsetY%2A> propriedades para que o botão muda de posição.</span><span class="sxs-lookup"><span data-stu-id="3f437-111">The example also changes the <xref:System.Windows.Media.Matrix.OffsetX%2A> and <xref:System.Windows.Media.Matrix.OffsetY%2A> properties so that the button changes position.</span></span>  
  
2. <span data-ttu-id="3f437-112">Anima o segundo <xref:System.Windows.Media.Matrix> em 1,0 segundo.</span><span class="sxs-lookup"><span data-stu-id="3f437-112">Animates the second <xref:System.Windows.Media.Matrix> at 1.0 seconds.</span></span> <span data-ttu-id="3f437-113">O botão muda para outra posição enquanto o botão não é mais distorcido ou alongado.</span><span class="sxs-lookup"><span data-stu-id="3f437-113">The button moves to another position while the button is no longer skewed or stretched.</span></span>  
  
3. <span data-ttu-id="3f437-114">Repete a animação indefinidamente.</span><span class="sxs-lookup"><span data-stu-id="3f437-114">Repeats the animation indefinitely.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3f437-115">Quadros que derivam de chave a <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> objeto criam saltos repentinos entre valores, ou seja, o movimento da animação é brusco.</span><span class="sxs-lookup"><span data-stu-id="3f437-115">Key frames that derive from the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> object create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="3f437-116">Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="3f437-116">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f437-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3f437-117">See also</span></span>

- <xref:System.Windows.Media.MatrixTransform.Matrix%2A>
- <xref:System.Windows.Media.MatrixTransform>
- [<span data-ttu-id="3f437-118">Visão geral das animações de quadro-chave</span><span class="sxs-lookup"><span data-stu-id="3f437-118">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="3f437-119">Tópicos explicativos sobre quadros-chave</span><span class="sxs-lookup"><span data-stu-id="3f437-119">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
