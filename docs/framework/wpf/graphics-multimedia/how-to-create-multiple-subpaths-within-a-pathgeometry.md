---
title: 'Como: Criar vários subcaminhos dentro de um PathGeometry'
ms.date: 03/30/2017
helpviewer_keywords:
- multiple subpaths [WPF]
- graphics [WPF], subpaths
- subpaths [WPF]
ms.assetid: 104a862c-dde2-4e62-ac87-80660dd1681c
ms.openlocfilehash: d7b3d24f8d947d342a2af5484a6620c8379ac664
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638347"
---
# <a name="how-to-create-multiple-subpaths-within-a-pathgeometry"></a><span data-ttu-id="4f077-102">Como: Criar vários subcaminhos dentro de um PathGeometry</span><span class="sxs-lookup"><span data-stu-id="4f077-102">How to: Create Multiple Subpaths Within a PathGeometry</span></span>
<span data-ttu-id="4f077-103">Este exemplo mostra como criar vários subcaminhos em um <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="4f077-103">This example shows how to create multiple subpaths in a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="4f077-104">Para criar vários subcaminhos, você cria um <xref:System.Windows.Media.PathFigure> para cada subcaminho.</span><span class="sxs-lookup"><span data-stu-id="4f077-104">To create multiple subpaths, you create a <xref:System.Windows.Media.PathFigure> for each subpath.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f077-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4f077-105">Example</span></span>  
 <span data-ttu-id="4f077-106">O exemplo a seguir cria dois subcaminhos, cada um de um triângulo.</span><span class="sxs-lookup"><span data-stu-id="4f077-106">The following example creates two subpaths, each one a triangle.</span></span>  
  
 [!code-xaml[GeometrySample#38](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#38)]  
  
 <span data-ttu-id="4f077-107">O exemplo a seguir mostra como criar vários subcaminhos usando um <xref:System.Windows.Shapes.Path> e [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sintaxe de atributo.</span><span class="sxs-lookup"><span data-stu-id="4f077-107">The following example shows how to create multiple subpaths by using a <xref:System.Windows.Shapes.Path> and [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attribute syntax.</span></span> <span data-ttu-id="4f077-108">Cada `M` cria um novo subcaminho para que o exemplo cria dois subcaminhos que cada Desenha um triângulo.</span><span class="sxs-lookup"><span data-stu-id="4f077-108">Each `M` creates a new subpath so that the example creates two subpaths that each draw a triangle.</span></span>  
  
 [!code-xaml[GeometrySample#58](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#58)]  
  
 <span data-ttu-id="4f077-109">(Observe que essa sintaxe de atributo na verdade cria um <xref:System.Windows.Media.StreamGeometry>, uma versão leve de um <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="4f077-109">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="4f077-110">Para obter mais informações, consulte o [sintaxe de marcação de caminho](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) página.)</span><span class="sxs-lookup"><span data-stu-id="4f077-110">For more information, see the [Path Markup Syntax](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) page.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f077-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f077-111">See also</span></span>
- [<span data-ttu-id="4f077-112">Visão geral de geometria</span><span class="sxs-lookup"><span data-stu-id="4f077-112">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
