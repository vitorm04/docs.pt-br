---
title: Como animar um objeto usando quadros-chave
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5f513cda540b3337f1510ee0c46419a12023bcb6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a><span data-ttu-id="2c3bc-102">Como animar um objeto usando quadros-chave</span><span class="sxs-lookup"><span data-stu-id="2c3bc-102">How to: Animate an Object by Using Key Frames</span></span>
<span data-ttu-id="2c3bc-103">Este exemplo mostra como animar um objeto, que neste exemplo é o <xref:System.Windows.Controls.Page.Background%2A> propriedade de um <xref:System.Windows.Controls.Page> controle usando quadros-chave.</span><span class="sxs-lookup"><span data-stu-id="2c3bc-103">This example shows how to animate an object, which in this example is the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control, by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c3bc-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2c3bc-104">Example</span></span>  
 <span data-ttu-id="2c3bc-105">O exemplo a seguir usa o <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> classe animar cor muda para o <xref:System.Windows.Controls.Page.Background%2A> propriedade de um <xref:System.Windows.Controls.Page> controle.</span><span class="sxs-lookup"><span data-stu-id="2c3bc-105">The following example uses the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class to animate color changes for the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control.</span></span> <span data-ttu-id="2c3bc-106">A animação do exemplo muda para um pincel de tela de fundo diferente em intervalos regulares.</span><span class="sxs-lookup"><span data-stu-id="2c3bc-106">The example animation changes to a different background brush at regular intervals.</span></span> <span data-ttu-id="2c3bc-107">Esta animação usa a <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> classe para criar três quadros-chave diferentes.</span><span class="sxs-lookup"><span data-stu-id="2c3bc-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> class to create three different key frames.</span></span> <span data-ttu-id="2c3bc-108">A animação usa quadros-chave da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="2c3bc-108">The animation uses key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="2c3bc-109">No final do primeiro segundo, anima uma instância do <xref:System.Windows.Media.LinearGradientBrush> classe.</span><span class="sxs-lookup"><span data-stu-id="2c3bc-109">At the end of the first second, animates an instance of the <xref:System.Windows.Media.LinearGradientBrush> class.</span></span> <span data-ttu-id="2c3bc-110">Esta seção do exemplo aplica um gradiente linear à cor da tela de fundo para que a cor faça a transição de amarelo para laranja para vermelho.</span><span class="sxs-lookup"><span data-stu-id="2c3bc-110">This section of the example applies a linear gradient to the background color so that the color transitions from yellow to orange to red.</span></span>  
  
2.  <span data-ttu-id="2c3bc-111">No final do próximo segundo, anima uma instância do <xref:System.Windows.Media.RadialGradientBrush> classe.</span><span class="sxs-lookup"><span data-stu-id="2c3bc-111">At the end of the next second, animates an instance of the <xref:System.Windows.Media.RadialGradientBrush> class.</span></span> <span data-ttu-id="2c3bc-112">Esta seção do exemplo aplica um gradiente radial à cor da tela de fundo para que a cor faça a transição de branco para azul para preto.</span><span class="sxs-lookup"><span data-stu-id="2c3bc-112">This section of the example applies a radial gradient to the background color so that the color transitions from white to blue to black.</span></span>  
  
3.  <span data-ttu-id="2c3bc-113">No final do terceiro segundo, anima uma instância do <xref:System.Windows.Media.DrawingBrush> classe.</span><span class="sxs-lookup"><span data-stu-id="2c3bc-113">At the end of the third second, animates an instance of the <xref:System.Windows.Media.DrawingBrush> class.</span></span> <span data-ttu-id="2c3bc-114">Esta seção do exemplo aplica um padrão quadriculado à tela de fundo.</span><span class="sxs-lookup"><span data-stu-id="2c3bc-114">This section of the example applies a checkerboard pattern to the background.</span></span>  
  
4.  <span data-ttu-id="2c3bc-115">A animação começa novamente e repete indefinidamente.</span><span class="sxs-lookup"><span data-stu-id="2c3bc-115">The animation begins again and repeats indefinitely.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2c3bc-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>é o único tipo de quadro-chave que você pode usar com o <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> classe.</span><span class="sxs-lookup"><span data-stu-id="2c3bc-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> is the only type of key frame that you can use with the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class.</span></span> <span data-ttu-id="2c3bc-117">Quadros-chave como <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> criam alterações repentinas em valores, ou seja, as alterações de cores neste exemplo, de repente, ocorrerem.</span><span class="sxs-lookup"><span data-stu-id="2c3bc-117">Key frames like <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> create sudden changes in values, that is, the color changes in this example occur suddenly.</span></span>  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="2c3bc-118">Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](http://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="2c3bc-118">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c3bc-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2c3bc-119">See Also</span></span>  
 <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>  
 <xref:System.Windows.Controls.Page.Background%2A>  
 <xref:System.Windows.Controls.Page>  
 <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>  
 <xref:System.Windows.Media.LinearGradientBrush>  
 <xref:System.Windows.Media.RadialGradientBrush>  
 <xref:System.Windows.Media.DrawingBrush>  
 [<span data-ttu-id="2c3bc-120">Visão geral das animações de quadro-chave</span><span class="sxs-lookup"><span data-stu-id="2c3bc-120">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="2c3bc-121">Tópicos explicativos sobre quadros-chave</span><span class="sxs-lookup"><span data-stu-id="2c3bc-121">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
