---
title: "Como criar vários subcaminhos dentro de um PathGeometry"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multiple subpaths [WPF]
- graphics [WPF], subpaths
- subpaths [WPF]
ms.assetid: 104a862c-dde2-4e62-ac87-80660dd1681c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7945728386c01d6137cbc422f0d7fb410a18d57e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-multiple-subpaths-within-a-pathgeometry"></a><span data-ttu-id="772b5-102">Como criar vários subcaminhos dentro de um PathGeometry</span><span class="sxs-lookup"><span data-stu-id="772b5-102">How to: Create Multiple Subpaths Within a PathGeometry</span></span>
<span data-ttu-id="772b5-103">Este exemplo mostra como criar vários subcaminhos em um <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="772b5-103">This example shows how to create multiple subpaths in a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="772b5-104">Para criar vários subcaminhos, você cria um <xref:System.Windows.Media.PathFigure> para cada subcaminho.</span><span class="sxs-lookup"><span data-stu-id="772b5-104">To create multiple subpaths, you create a <xref:System.Windows.Media.PathFigure> for each subpath.</span></span>  
  
## <a name="example"></a><span data-ttu-id="772b5-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="772b5-105">Example</span></span>  
 <span data-ttu-id="772b5-106">O exemplo a seguir cria dois subcaminhos, cada uma um triângulo.</span><span class="sxs-lookup"><span data-stu-id="772b5-106">The following example creates two subpaths, each one a triangle.</span></span>  
  
 [!code-xaml[GeometrySample#38](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#38)]  
  
 <span data-ttu-id="772b5-107">O exemplo a seguir mostra como criar vários subcaminhos usando um <xref:System.Windows.Shapes.Path> e [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sintaxe de atributo.</span><span class="sxs-lookup"><span data-stu-id="772b5-107">The following example shows how to create multiple subpaths by using a <xref:System.Windows.Shapes.Path> and [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attribute syntax.</span></span> <span data-ttu-id="772b5-108">Cada `M` cria um novo subcaminho para que o exemplo cria dois subcaminhos tal que cada Desenha um triângulo.</span><span class="sxs-lookup"><span data-stu-id="772b5-108">Each `M` creates a new subpath so that the example creates two subpaths that each draw a triangle.</span></span>  
  
 [!code-xaml[GeometrySample#58](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#58)]  
  
 <span data-ttu-id="772b5-109">(Observe que esta sintaxe de atributo, na verdade, cria um <xref:System.Windows.Media.StreamGeometry>, uma versão leve de um <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="772b5-109">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="772b5-110">Para obter mais informações, consulte o [sintaxe de marcação de caminho](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) página.)</span><span class="sxs-lookup"><span data-stu-id="772b5-110">For more information, see the [Path Markup Syntax](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) page.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="772b5-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="772b5-111">See Also</span></span>  
 [<span data-ttu-id="772b5-112">Visão geral de geometria</span><span class="sxs-lookup"><span data-stu-id="772b5-112">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
