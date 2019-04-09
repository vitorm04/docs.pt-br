---
title: 'Como: Animar uma cadeia de caracteres usando quadros principais'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], strings with key frames
- strings [WPF], animating with key frames
- key frames [WPF], animating strings with
ms.assetid: c62bc9fd-c09a-4227-bce0-0a1ab82049dd
ms.openlocfilehash: 4a37408ad90fda12a95e66c1b44018967b376837
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204166"
---
# <a name="how-to-animate-a-string-by-using-key-frames"></a><span data-ttu-id="a590e-102">Como: Animar uma cadeia de caracteres usando quadros principais</span><span class="sxs-lookup"><span data-stu-id="a590e-102">How to: Animate a String by Using Key Frames</span></span>
<span data-ttu-id="a590e-103">Este exemplo mostra como animar uma cadeia de caracteres, que neste exemplo é o <xref:System.Windows.Controls.ContentControl.Content%2A> propriedade de um <xref:System.Windows.Controls.Button> controle usando quadros-chave.</span><span class="sxs-lookup"><span data-stu-id="a590e-103">This example shows how to animate a string, which in this example is the <xref:System.Windows.Controls.ContentControl.Content%2A> property of a <xref:System.Windows.Controls.Button> control, by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a590e-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a590e-104">Example</span></span>  
 <span data-ttu-id="a590e-105">O exemplo a seguir usa o <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames> classe para animar a <xref:System.Windows.Controls.ContentControl.Content%2A> propriedade de um <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="a590e-105">The following example uses the <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Controls.ContentControl.Content%2A> property of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="a590e-106">Todos os quadros chave neste exemplo usam uma instância da <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> classe porque uma animação de cadeia de caracteres que é criada com quadros chave só pode usar quadros-chave discretos.</span><span class="sxs-lookup"><span data-stu-id="a590e-106">All the key frames in this example use an instance of the <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> class because a string animation that is created with key frames can only use discrete key frames.</span></span> <span data-ttu-id="a590e-107">Quadros chave discretos como <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> criam saltos repentinos entre valores, ou seja, as alterações para a animação ocorrem rapidamente e não são sutis.</span><span class="sxs-lookup"><span data-stu-id="a590e-107">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> create sudden jumps between values, that is, changes to the animation occur quickly and are not subtle.</span></span>  
  
 [!code-xaml[keyframes_snip#StringAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/StringAnimationUsingKeyFramesExample.xaml#stringanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="a590e-108">Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="a590e-108">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a590e-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a590e-109">See also</span></span>

- <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.ContentControl.Content%2A>
- <xref:System.Windows.Controls.Button>
- <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>
- [<span data-ttu-id="a590e-110">Visão geral das animações de quadro-chave</span><span class="sxs-lookup"><span data-stu-id="a590e-110">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="a590e-111">Tópicos explicativos sobre quadros-chave</span><span class="sxs-lookup"><span data-stu-id="a590e-111">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
