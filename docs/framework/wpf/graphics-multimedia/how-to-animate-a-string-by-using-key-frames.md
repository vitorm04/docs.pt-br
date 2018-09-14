---
title: Como animar uma cadeia de caracteres usando quadros-chave
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], strings with key frames
- strings [WPF], animating with key frames
- key frames [WPF], animating strings with
ms.assetid: c62bc9fd-c09a-4227-bce0-0a1ab82049dd
ms.openlocfilehash: 1b55afd5938073a326789e67b66fec9cfce12015
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45596189"
---
# <a name="how-to-animate-a-string-by-using-key-frames"></a><span data-ttu-id="5f410-102">Como animar uma cadeia de caracteres usando quadros-chave</span><span class="sxs-lookup"><span data-stu-id="5f410-102">How to: Animate a String by Using Key Frames</span></span>
<span data-ttu-id="5f410-103">Este exemplo mostra como animar uma cadeia de caracteres, que neste exemplo é o <xref:System.Windows.Controls.ContentControl.Content%2A> propriedade de um <xref:System.Windows.Controls.Button> controle usando quadros-chave.</span><span class="sxs-lookup"><span data-stu-id="5f410-103">This example shows how to animate a string, which in this example is the <xref:System.Windows.Controls.ContentControl.Content%2A> property of a <xref:System.Windows.Controls.Button> control, by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f410-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5f410-104">Example</span></span>  
 <span data-ttu-id="5f410-105">O exemplo a seguir usa o <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames> classe para animar a <xref:System.Windows.Controls.ContentControl.Content%2A> propriedade de um <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="5f410-105">The following example uses the <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Controls.ContentControl.Content%2A> property of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="5f410-106">Todos os quadros chave neste exemplo usam uma instância da <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> classe porque uma animação de cadeia de caracteres que é criada com quadros chave só pode usar quadros-chave discretos.</span><span class="sxs-lookup"><span data-stu-id="5f410-106">All the key frames in this example use an instance of the <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> class because a string animation that is created with key frames can only use discrete key frames.</span></span> <span data-ttu-id="5f410-107">Quadros chave discretos como <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> criam saltos repentinos entre valores, ou seja, as alterações para a animação ocorrem rapidamente e não são sutis.</span><span class="sxs-lookup"><span data-stu-id="5f410-107">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> create sudden jumps between values, that is, changes to the animation occur quickly and are not subtle.</span></span>  
  
 [!code-xaml[keyframes_snip#StringAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/StringAnimationUsingKeyFramesExample.xaml#stringanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="5f410-108">Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="5f410-108">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f410-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5f410-109">See Also</span></span>  
 <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>  
 <xref:System.Windows.Controls.ContentControl.Content%2A>  
 <xref:System.Windows.Controls.Button>  
 <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>  
 [<span data-ttu-id="5f410-110">Visão geral das animações de quadro-chave</span><span class="sxs-lookup"><span data-stu-id="5f410-110">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="5f410-111">Tópicos explicativos sobre quadros-chave</span><span class="sxs-lookup"><span data-stu-id="5f410-111">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
