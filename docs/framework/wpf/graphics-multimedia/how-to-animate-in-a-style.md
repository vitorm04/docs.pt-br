---
title: Como animar em um estilo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], properties [WPF], within styles
- styles [WPF], animating properties within
ms.assetid: 6a791f3d-6b1f-4972-a2f9-35880bcfd954
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 10cd243c633e7a7e458d2026fc5e3d91d2996427
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-animate-in-a-style"></a><span data-ttu-id="15730-102">Como animar em um estilo</span><span class="sxs-lookup"><span data-stu-id="15730-102">How to: Animate in a Style</span></span>
<span data-ttu-id="15730-103">Este exemplo mostra como animar propriedades em um estilo.</span><span class="sxs-lookup"><span data-stu-id="15730-103">This example shows how to animate properties within a style.</span></span> <span data-ttu-id="15730-104">Ao animar em um estilo, somente o elemento de estrutura para o qual o estilo está definido pode ser alvo diretamente.</span><span class="sxs-lookup"><span data-stu-id="15730-104">When animating within a style, only the framework element for which the style is defined can be targeted directly.</span></span> <span data-ttu-id="15730-105">Para direcionar um objeto freezable, é preciso fazer a "marcação" de uma propriedade do elemento.</span><span class="sxs-lookup"><span data-stu-id="15730-105">To target a freezable object, you must "dot down" from a property of the styled element.</span></span>  
  
 <span data-ttu-id="15730-106">No exemplo a seguir, diversas animações são definidas em um estilo e aplicadas a um <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="15730-106">In the following example, several animations are defined within a style and applied to a <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="15730-107">Quando o usuário move o mouse sobre o botão, ele passa de opaco a parcialmente translúcido e repete o processo.</span><span class="sxs-lookup"><span data-stu-id="15730-107">When the user moves the mouse over the button, it fades from opaque to partially translucent and back again, repeatedly.</span></span> <span data-ttu-id="15730-108">Quando o usuário move o mouse para fora do botão, este fica completamente opaco.</span><span class="sxs-lookup"><span data-stu-id="15730-108">When the user moves the mouse off the button, it becomes completely opaque.</span></span> <span data-ttu-id="15730-109">Quando o botão é clicado, sua cor da tela de fundo muda de laranja para branco e volta a cor original.</span><span class="sxs-lookup"><span data-stu-id="15730-109">When the button is clicked, its background color changes from orange to white and back again.</span></span> <span data-ttu-id="15730-110">Porque o <xref:System.Windows.Media.SolidColorBrush> usado para pintar o botão não pode ser direcionado diretamente, ele é acessado por "dotting down" com o botão <xref:System.Windows.Controls.Control.Background%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="15730-110">Because the <xref:System.Windows.Media.SolidColorBrush> used to paint the button can't be targeted directly, it is accessed by dotting down from the button's <xref:System.Windows.Controls.Control.Background%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15730-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="15730-111">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StyleStoryboardsExample.xaml#21)]  
  
 <span data-ttu-id="15730-112">Observe que ao animar dentro de um estilo, é possível segmentar objetos que não existem.</span><span class="sxs-lookup"><span data-stu-id="15730-112">Note that when animating within a style, it's possible to target objects that don't exist.</span></span> <span data-ttu-id="15730-113">Por exemplo, suponha que seu estilo utilize um <xref:System.Windows.Media.SolidColorBrush> definir a propriedade de plano de fundo de um botão, mas em algum momento o estilo é substituído e o plano de fundo do botão é definido com um <xref:System.Windows.Media.LinearGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="15730-113">For example, suppose your style uses a <xref:System.Windows.Media.SolidColorBrush> to set a Button's background property, but at some point the style is overridden and the button's background is set with a <xref:System.Windows.Media.LinearGradientBrush>.</span></span>  <span data-ttu-id="15730-114">Tentar animar a <xref:System.Windows.Media.SolidColorBrush> não lançará uma exceção; a animação simplesmente falhará silenciosamente.</span><span class="sxs-lookup"><span data-stu-id="15730-114">Trying to animate the <xref:System.Windows.Media.SolidColorBrush> won't throw an exception; the animation will simply fail silently.</span></span>  
  
 <span data-ttu-id="15730-115">Para mais informações sobre sintaxe de segmentação de storyboard, consulte [Visão Geral de Storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).</span><span class="sxs-lookup"><span data-stu-id="15730-115">Fore more information about storyboard targeting syntax, see the [Storyboards Overview](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).</span></span> <span data-ttu-id="15730-116">Para mais informações sobre animação, consulte [Visão Geral de Animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="15730-116">For more information about animation, see the [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span> <span data-ttu-id="15730-117">Para mais informações sobre estilos, consulte [Estilos e Modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="15730-117">For more information about styles, see the [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span>
