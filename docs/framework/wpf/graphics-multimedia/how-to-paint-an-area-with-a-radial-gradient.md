---
title: "Como pintar uma área com um gradiente radial"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with radial gradients
- radial gradients [WPF], painting with
- painting [WPF], with radial gradients
ms.assetid: b5d0fc8a-8986-4796-b003-a75b41a48928
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 55b707e4738a77a8fb093071ef6f5105b2200c16
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-paint-an-area-with-a-radial-gradient"></a><span data-ttu-id="d3977-102">Como pintar uma área com um gradiente radial</span><span class="sxs-lookup"><span data-stu-id="d3977-102">How to: Paint an Area with a Radial Gradient</span></span>
<span data-ttu-id="d3977-103">Este exemplo mostra como usar o <xref:System.Windows.Media.RadialGradientBrush> classe para pintar uma área com um gradiente radial.</span><span class="sxs-lookup"><span data-stu-id="d3977-103">This example shows how to use the <xref:System.Windows.Media.RadialGradientBrush> class to paint an area with a radial gradient.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3977-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d3977-104">Example</span></span>  
 <span data-ttu-id="d3977-105">O exemplo a seguir usa um <xref:System.Windows.Media.RadialGradientBrush> para desenhar um retângulo com um gradiente radial que faz a transição de amarelo para vermelho para azul para verde limão.</span><span class="sxs-lookup"><span data-stu-id="d3977-105">The following example uses a <xref:System.Windows.Media.RadialGradientBrush> to paint a rectangle with a radial gradient that transitions from yellow to red to blue to lime green.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xaml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 <span data-ttu-id="d3977-106">A ilustração a seguir mostra o gradiente do exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="d3977-106">The following illustration shows the gradient from the preceding example.</span></span> <span data-ttu-id="d3977-107">Do gradiente foram realçado.</span><span class="sxs-lookup"><span data-stu-id="d3977-107">The gradient's stops have been highlighted.</span></span>  
  
 <span data-ttu-id="d3977-108">![Marcas de gradiente em um gradiente radial](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")</span><span class="sxs-lookup"><span data-stu-id="d3977-108">![Gradient stops in a radial gradient](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3977-109">Os exemplos neste tópico usam o sistema de coordenadas padrão para definir pontos de controle.</span><span class="sxs-lookup"><span data-stu-id="d3977-109">The examples in this topic use the default coordinate system for setting control points.</span></span> <span data-ttu-id="d3977-110">O sistema de coordenadas padrão é relativo a uma caixa delimitadora: 0 indica 0% da caixa delimitadora e 1 indica 100% da caixa delimitadora.</span><span class="sxs-lookup"><span data-stu-id="d3977-110">The default coordinate system is relative to a bounding box: 0 indicates 0 percent of the bounding box, and 1 indicates 100 percent of the bounding box.</span></span> <span data-ttu-id="d3977-111">Você pode alterar esse sistema de coordenadas definindo a <xref:System.Windows.Media.GradientBrush.MappingMode%2A> propriedade para o valor <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span><span class="sxs-lookup"><span data-stu-id="d3977-111">You can change this coordinate system by setting the <xref:System.Windows.Media.GradientBrush.MappingMode%2A> property to the value <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span></span> <span data-ttu-id="d3977-112">Um sistema de coordenadas absoluto não é relativo a uma caixa delimitadora.</span><span class="sxs-lookup"><span data-stu-id="d3977-112">An absolute coordinate system is not relative to a bounding box.</span></span> <span data-ttu-id="d3977-113">Os valores são interpretados diretamente no espaço local.</span><span class="sxs-lookup"><span data-stu-id="d3977-113">Values are interpreted directly in local space.</span></span>  
  
 <span data-ttu-id="d3977-114">Para mais <xref:System.Windows.Media.RadialGradientBrush> exemplos, consulte o [exemplo pincéis](http://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="d3977-114">For additional <xref:System.Windows.Media.RadialGradientBrush> examples, see the [Brushes Sample](http://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="d3977-115">Para obter mais informações sobre gradientes e outros tipos de pincéis, veja [Visão geral de pintura com cores sólidas e gradientes](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d3977-115">For more information about gradients and other types of brushes, see [Painting with Solid Colors and Gradients Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span></span>
