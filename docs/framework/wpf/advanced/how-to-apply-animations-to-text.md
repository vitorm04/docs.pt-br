---
title: "Como aplicar animações ao texto"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- typography [WPF], animations
- animation [WPF], text
ms.assetid: eec3d26c-0a21-420f-8012-671621c47089
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0298462db5897e955bf0a2551cca7fc81bb27d89
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-apply-animations-to-text"></a><span data-ttu-id="f45cf-102">Como aplicar animações ao texto</span><span class="sxs-lookup"><span data-stu-id="f45cf-102">How to: Apply Animations to Text</span></span>
<span data-ttu-id="f45cf-103">As animações podem alterar a exibição e a aparência do texto em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f45cf-103">Animations can alter the display and appearance of text in your application.</span></span> <span data-ttu-id="f45cf-104">Os exemplos a seguir usam diferentes tipos de animação para afetar a exibição do texto em uma <xref:System.Windows.Controls.TextBlock> controle.</span><span class="sxs-lookup"><span data-stu-id="f45cf-104">The following examples use different types of animations to affect the display of text in a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f45cf-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f45cf-105">Example</span></span>  
 <span data-ttu-id="f45cf-106">O exemplo a seguir usa um <xref:System.Windows.Media.Animation.DoubleAnimation> para animar a largura do bloco de texto.</span><span class="sxs-lookup"><span data-stu-id="f45cf-106">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the width of the text block.</span></span> <span data-ttu-id="f45cf-107">O valor da largura muda da largura do bloco de texto para 0 em um período de 10 segundos, depois inverte os valores de largura e continua.</span><span class="sxs-lookup"><span data-stu-id="f45cf-107">The width value changes from the width of the text block to 0 over a duration of 10 seconds, and then reverses the width values and continues.</span></span> <span data-ttu-id="f45cf-108">Este tipo de animação cria um efeito de revelação.</span><span class="sxs-lookup"><span data-stu-id="f45cf-108">This type of animation creates a wipe effect.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample1)]  
  
 <span data-ttu-id="f45cf-109">O exemplo a seguir usa um <xref:System.Windows.Media.Animation.DoubleAnimation> para animar a opacidade do bloco de texto.</span><span class="sxs-lookup"><span data-stu-id="f45cf-109">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the opacity of the text block.</span></span> <span data-ttu-id="f45cf-110">O valor de opacidade muda de 1,0 para 0 em um período de 5 segundos, depois reverte os valores de opacidade e continua.</span><span class="sxs-lookup"><span data-stu-id="f45cf-110">The opacity value changes from 1.0 to 0 over a duration of 5 seconds, and then reverses the opacity values and continues.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample2)]  
  
 <span data-ttu-id="f45cf-111">O diagrama a seguir mostra o efeito do <xref:System.Windows.Controls.TextBlock> controle alterando sua opacidade de `1.00` para `0.00` durante o intervalo de 5 segundos definido pelo <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.</span><span class="sxs-lookup"><span data-stu-id="f45cf-111">The following diagram shows the effect of the <xref:System.Windows.Controls.TextBlock> control changing its opacity from `1.00` to `0.00` during the 5-second interval defined by the <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.</span></span>  
  
 <span data-ttu-id="f45cf-112">![Texto alterando a opacidade de 1,00 para 0,00](../../../../docs/framework/wpf/advanced/media/fadedtext01.png "FadedText01")</span><span class="sxs-lookup"><span data-stu-id="f45cf-112">![Text changing opacity from 1.00 to 0.00](../../../../docs/framework/wpf/advanced/media/fadedtext01.png "FadedText01")</span></span>  
<span data-ttu-id="f45cf-113">Opacidade do texto mudando de 1,00 para 0,00</span><span class="sxs-lookup"><span data-stu-id="f45cf-113">Text Opacity changing from 1.00 to 0.00</span></span>  
  
 <span data-ttu-id="f45cf-114">O exemplo a seguir usa um <xref:System.Windows.Media.Animation.ColorAnimation> para animar a cor de primeiro plano do bloco de texto.</span><span class="sxs-lookup"><span data-stu-id="f45cf-114">The following example uses a <xref:System.Windows.Media.Animation.ColorAnimation> to animate the foreground color of the text block.</span></span> <span data-ttu-id="f45cf-115">O valor da cor de primeiro plano muda de uma cor para uma segunda cor em um período de 5 segundos, depois reverte os valores de cor e continua.</span><span class="sxs-lookup"><span data-stu-id="f45cf-115">The foreground color value changes from one color to a second color over a duration of 5 seconds, and then reverses the color values and continues.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample3)]  
  
 <span data-ttu-id="f45cf-116">O exemplo a seguir usa um <xref:System.Windows.Media.Animation.DoubleAnimation> para girar o bloco de texto.</span><span class="sxs-lookup"><span data-stu-id="f45cf-116">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to rotate the text block.</span></span> <span data-ttu-id="f45cf-117">O bloco de texto faz uma rotação completa em um período de 20 segundos e depois continua repetindo a rotação.</span><span class="sxs-lookup"><span data-stu-id="f45cf-117">The text block performs a full rotation over a duration of 20 seconds, and then continues to repeat the rotation.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample4)]  
  
## <a name="see-also"></a><span data-ttu-id="f45cf-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f45cf-118">See Also</span></span>  
 [<span data-ttu-id="f45cf-119">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="f45cf-119">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
