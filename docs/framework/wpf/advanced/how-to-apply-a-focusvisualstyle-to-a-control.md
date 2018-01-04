---
title: Como aplicar um FocusVisualStyle a um controle
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- properties [WPF], FocusVisualStyle
- FocusVisualStyle property [WPF]
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 41895974b7e6c128d979e362f2dcef1c68e0a5c0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-apply-a-focusvisualstyle-to-a-control"></a><span data-ttu-id="b72e3-102">Como aplicar um FocusVisualStyle a um controle</span><span class="sxs-lookup"><span data-stu-id="b72e3-102">How to: Apply a FocusVisualStyle to a Control</span></span>
<span data-ttu-id="b72e3-103">Este exemplo mostra como criar um estilo visual de foco em recursos e aplicar o estilo a um controle, usando o <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="b72e3-103">This example shows you how to create a focus visual style in resources and apply the style to a control, using the <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b72e3-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b72e3-104">Example</span></span>  
 <span data-ttu-id="b72e3-105">O exemplo a seguir define um estilo que cria a composição de controle adicional que só se aplica quando esse controle é voltado para o teclado no [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b72e3-105">The following example defines a style that creates additional control compositing that only applies when that control is keyboard focused in the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span> <span data-ttu-id="b72e3-106">Isso é feito definindo um estilo com um <xref:System.Windows.Controls.ControlTemplate>, em seguida, fazer referência a esse estilo como um recurso ao definir o <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="b72e3-106">This is accomplished by defining a style with a <xref:System.Windows.Controls.ControlTemplate>, then referencing that style as a resource when setting the <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> property.</span></span>  
  
 <span data-ttu-id="b72e3-107">Um retângulo externo representando uma borda é colocado fora da área retangular.</span><span class="sxs-lookup"><span data-stu-id="b72e3-107">An external rectangle resembling a border is placed outside of the rectangular area.</span></span> <span data-ttu-id="b72e3-108">A menos que modificado de outra forma, o dimensionamento do estilo usa o <xref:System.Windows.FrameworkElement.ActualHeight%2A> e <xref:System.Windows.FrameworkElement.ActualWidth%2A> do controle retangular onde o estilo visual de foco é aplicado.</span><span class="sxs-lookup"><span data-stu-id="b72e3-108">Unless otherwise modified, the sizing of the style uses the <xref:System.Windows.FrameworkElement.ActualHeight%2A> and <xref:System.Windows.FrameworkElement.ActualWidth%2A> of the rectangular control where the focus visual style is applied.</span></span> <span data-ttu-id="b72e3-109">Este exemplo define valores negativos para o <xref:System.Windows.FrameworkElement.Margin%2A> para tornar a borda pareça estar ligeiramente fora do controle focalizado.</span><span class="sxs-lookup"><span data-stu-id="b72e3-109">This example sets negative values for the <xref:System.Windows.FrameworkElement.Margin%2A> to make the border appear slightly outside the focused control.</span></span>  
  
 [!code-xaml[FEFocusVisualStyle#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 <span data-ttu-id="b72e3-110">Um <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> é aditivo para qualquer estilo de modelo de controle que vem tanto de um estilo explícito ou um estilo de tema; o estilo primário para um controle pode ainda ser criado usando um <xref:System.Windows.Controls.ControlTemplate> e configurando esse estilo para o <xref:System.Windows.FrameworkElement.Style%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="b72e3-110">A <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> is additive to any control template style that comes either from an explicit style or a theme style; the primary style for a control can still be created by using a <xref:System.Windows.Controls.ControlTemplate> and setting that style to the <xref:System.Windows.FrameworkElement.Style%2A> property.</span></span>  
  
 <span data-ttu-id="b72e3-111">Estilos visuais de foco devem ser usados consistentemente em um tema ou uma interface do usuário, em vez de usar um diferente para cada elemento focalizável.</span><span class="sxs-lookup"><span data-stu-id="b72e3-111">Focus visual styles should be used consistently across a theme or a UI, rather than using a different one for each focusable element.</span></span> <span data-ttu-id="b72e3-112">Para obter detalhes, consulte [Estilos para foco em controles e FocusVisualStyle](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md).</span><span class="sxs-lookup"><span data-stu-id="b72e3-112">For details, see [Styling for Focus in Controls, and FocusVisualStyle](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b72e3-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b72e3-113">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>  
 [<span data-ttu-id="b72e3-114">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="b72e3-114">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="b72e3-115">Estilos para foco em controles e FocusVisualStyle</span><span class="sxs-lookup"><span data-stu-id="b72e3-115">Styling for Focus in Controls, and FocusVisualStyle</span></span>](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md)
