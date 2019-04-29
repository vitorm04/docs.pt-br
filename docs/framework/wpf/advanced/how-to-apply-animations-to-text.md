---
title: 'Como: Aplicar animações ao texto'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], animations
- animation [WPF], text
ms.assetid: eec3d26c-0a21-420f-8012-671621c47089
ms.openlocfilehash: 38aa432fecc5b5e10d8eb90be9c1c596728ed613
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776870"
---
# <a name="how-to-apply-animations-to-text"></a><span data-ttu-id="9ae15-102">Como: Aplicar animações ao texto</span><span class="sxs-lookup"><span data-stu-id="9ae15-102">How to: Apply Animations to Text</span></span>
<span data-ttu-id="9ae15-103">As animações podem alterar a exibição e a aparência do texto em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9ae15-103">Animations can alter the display and appearance of text in your application.</span></span> <span data-ttu-id="9ae15-104">Os exemplos a seguir usam diferentes tipos de animação para afetar a exibição do texto em um <xref:System.Windows.Controls.TextBlock> controle.</span><span class="sxs-lookup"><span data-stu-id="9ae15-104">The following examples use different types of animations to affect the display of text in a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ae15-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9ae15-105">Example</span></span>  
 <span data-ttu-id="9ae15-106">O exemplo a seguir usa um <xref:System.Windows.Media.Animation.DoubleAnimation> para animar a largura do bloco de texto.</span><span class="sxs-lookup"><span data-stu-id="9ae15-106">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the width of the text block.</span></span> <span data-ttu-id="9ae15-107">O valor da largura muda da largura do bloco de texto para 0 em um período de 10 segundos, depois inverte os valores de largura e continua.</span><span class="sxs-lookup"><span data-stu-id="9ae15-107">The width value changes from the width of the text block to 0 over a duration of 10 seconds, and then reverses the width values and continues.</span></span> <span data-ttu-id="9ae15-108">Este tipo de animação cria um efeito de revelação.</span><span class="sxs-lookup"><span data-stu-id="9ae15-108">This type of animation creates a wipe effect.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample1)]  
  
 <span data-ttu-id="9ae15-109">O exemplo a seguir usa um <xref:System.Windows.Media.Animation.DoubleAnimation> para animar a opacidade do bloco de texto.</span><span class="sxs-lookup"><span data-stu-id="9ae15-109">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the opacity of the text block.</span></span> <span data-ttu-id="9ae15-110">O valor de opacidade muda de 1,0 para 0 em um período de 5 segundos, depois reverte os valores de opacidade e continua.</span><span class="sxs-lookup"><span data-stu-id="9ae15-110">The opacity value changes from 1.0 to 0 over a duration of 5 seconds, and then reverses the opacity values and continues.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample2)]  
  
 <span data-ttu-id="9ae15-111">O diagrama a seguir mostra o efeito do <xref:System.Windows.Controls.TextBlock> controle modificando sua opacidade de `1.00` à `0.00` durante o intervalo de 5 segundos definido pelo <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.</span><span class="sxs-lookup"><span data-stu-id="9ae15-111">The following diagram shows the effect of the <xref:System.Windows.Controls.TextBlock> control changing its opacity from `1.00` to `0.00` during the 5-second interval defined by the <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.</span></span>  
  
 ![Texto alterando a opacidade de 1,00 para 0,00.](./media/how-to-apply-animations-to-text/faded-text-opacity-change.png)  
   
 <span data-ttu-id="9ae15-113">O exemplo a seguir usa um <xref:System.Windows.Media.Animation.ColorAnimation> para animar a cor de primeiro plano do bloco de texto.</span><span class="sxs-lookup"><span data-stu-id="9ae15-113">The following example uses a <xref:System.Windows.Media.Animation.ColorAnimation> to animate the foreground color of the text block.</span></span> <span data-ttu-id="9ae15-114">O valor da cor de primeiro plano muda de uma cor para uma segunda cor em um período de 5 segundos, depois reverte os valores de cor e continua.</span><span class="sxs-lookup"><span data-stu-id="9ae15-114">The foreground color value changes from one color to a second color over a duration of 5 seconds, and then reverses the color values and continues.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample3)]  
  
 <span data-ttu-id="9ae15-115">O exemplo a seguir usa um <xref:System.Windows.Media.Animation.DoubleAnimation> para girar o bloco de texto.</span><span class="sxs-lookup"><span data-stu-id="9ae15-115">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to rotate the text block.</span></span> <span data-ttu-id="9ae15-116">O bloco de texto faz uma rotação completa em um período de 20 segundos e depois continua repetindo a rotação.</span><span class="sxs-lookup"><span data-stu-id="9ae15-116">The text block performs a full rotation over a duration of 20 seconds, and then continues to repeat the rotation.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample4)]  
  
## <a name="see-also"></a><span data-ttu-id="9ae15-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9ae15-117">See also</span></span>

- [<span data-ttu-id="9ae15-118">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="9ae15-118">Animation Overview</span></span>](../graphics-multimedia/animation-overview.md)
