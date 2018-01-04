---
title: "Como disparar uma animação quando o valor de uma propriedade é alterado"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], starting when property values change
- triggering animation [WPF]
- Storyboards [WPF], starting when property values change
ms.assetid: 12399c21-0300-4f4f-9e3a-d92d9907e5f5
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0eb4542d8baf86f01417eb1925028a00471b40b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-trigger-an-animation-when-a-property-value-changes"></a><span data-ttu-id="1ab0d-102">Como disparar uma animação quando o valor de uma propriedade é alterado</span><span class="sxs-lookup"><span data-stu-id="1ab0d-102">How to: Trigger an Animation When a Property Value Changes</span></span>
<span data-ttu-id="1ab0d-103">Este exemplo mostra como usar um <xref:System.Windows.Trigger> para iniciar um <xref:System.Windows.Media.Animation.Storyboard> quando um valor de propriedade é alterado.</span><span class="sxs-lookup"><span data-stu-id="1ab0d-103">This example shows how to use a <xref:System.Windows.Trigger> to start a <xref:System.Windows.Media.Animation.Storyboard> when a property value changes.</span></span> <span data-ttu-id="1ab0d-104">Você pode usar um <xref:System.Windows.Trigger> dentro de um <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, ou <xref:System.Windows.DataTemplate>.</span><span class="sxs-lookup"><span data-stu-id="1ab0d-104">You can use a <xref:System.Windows.Trigger> inside a <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, or <xref:System.Windows.DataTemplate>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ab0d-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1ab0d-105">Example</span></span>  
 <span data-ttu-id="1ab0d-106">O exemplo a seguir usa uma <xref:System.Windows.Trigger> para animar a <xref:System.Windows.UIElement.Opacity%2A> de um <xref:System.Windows.Controls.Button> quando seu <xref:System.Windows.UIElement.IsMouseOver%2A> propriedade torna-se `true`.</span><span class="sxs-lookup"><span data-stu-id="1ab0d-106">The following example uses a <xref:System.Windows.Trigger> to animate the <xref:System.Windows.UIElement.Opacity%2A> of a <xref:System.Windows.Controls.Button> when its <xref:System.Windows.UIElement.IsMouseOver%2A> property becomes `true`.</span></span>  
  
 [!code-xaml[AnimatePropertyStoryboards#PropertyTriggerExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/PropertyTriggerExample.xaml#propertytriggerexample)]  
  
 <span data-ttu-id="1ab0d-107">Animações aplicadas pela propriedade <xref:System.Windows.Trigger> objetos se comportam de maneira mais complexa que <xref:System.Windows.EventTrigger> animações ou animações iniciadas usando <xref:System.Windows.Media.Animation.Storyboard> métodos.</span><span class="sxs-lookup"><span data-stu-id="1ab0d-107">Animations applied by property <xref:System.Windows.Trigger> objects behave in a more complex fashion than <xref:System.Windows.EventTrigger> animations or animations started using <xref:System.Windows.Media.Animation.Storyboard> methods.</span></span>  <span data-ttu-id="1ab0d-108">Elas "entregam" animações definida por outros <xref:System.Windows.Trigger> objetos, mas se compõem com <xref:System.Windows.EventTrigger> e animações acionadas por método.</span><span class="sxs-lookup"><span data-stu-id="1ab0d-108">They "handoff" with animations defined by other <xref:System.Windows.Trigger> objects, but compose with <xref:System.Windows.EventTrigger> and method-triggered animations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ab0d-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ab0d-109">See Also</span></span>  
 <xref:System.Windows.Trigger>  
 [<span data-ttu-id="1ab0d-110">Visão geral das técnicas de animação da propriedade</span><span class="sxs-lookup"><span data-stu-id="1ab0d-110">Property Animation Techniques Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [<span data-ttu-id="1ab0d-111">Visão geral de storyboards</span><span class="sxs-lookup"><span data-stu-id="1ab0d-111">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
