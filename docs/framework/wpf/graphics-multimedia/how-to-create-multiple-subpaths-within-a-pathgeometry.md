---
title: 'Como: Criar vários subcaminhos dentro de um PathGeometry'
ms.date: 03/30/2017
helpviewer_keywords:
- multiple subpaths [WPF]
- graphics [WPF], subpaths
- subpaths [WPF]
ms.assetid: 104a862c-dde2-4e62-ac87-80660dd1681c
ms.openlocfilehash: 286075448cd6a343f8a7b15b2b5005f840f68e1d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61904716"
---
# <a name="how-to-create-multiple-subpaths-within-a-pathgeometry"></a><span data-ttu-id="786cb-102">Como: Criar vários subcaminhos dentro de um PathGeometry</span><span class="sxs-lookup"><span data-stu-id="786cb-102">How to: Create Multiple Subpaths Within a PathGeometry</span></span>
<span data-ttu-id="786cb-103">Este exemplo mostra como criar vários subcaminhos em um <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="786cb-103">This example shows how to create multiple subpaths in a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="786cb-104">Para criar vários subcaminhos, você cria um <xref:System.Windows.Media.PathFigure> para cada subcaminho.</span><span class="sxs-lookup"><span data-stu-id="786cb-104">To create multiple subpaths, you create a <xref:System.Windows.Media.PathFigure> for each subpath.</span></span>  
  
## <a name="example"></a><span data-ttu-id="786cb-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="786cb-105">Example</span></span>  
 <span data-ttu-id="786cb-106">O exemplo a seguir cria dois subcaminhos, cada um de um triângulo.</span><span class="sxs-lookup"><span data-stu-id="786cb-106">The following example creates two subpaths, each one a triangle.</span></span>  
  
 [!code-xaml[GeometrySample#38](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#38)]  
  
 <span data-ttu-id="786cb-107">O exemplo a seguir mostra como criar vários subcaminhos usando um <xref:System.Windows.Shapes.Path> e [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sintaxe de atributo.</span><span class="sxs-lookup"><span data-stu-id="786cb-107">The following example shows how to create multiple subpaths by using a <xref:System.Windows.Shapes.Path> and [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attribute syntax.</span></span> <span data-ttu-id="786cb-108">Cada `M` cria um novo subcaminho para que o exemplo cria dois subcaminhos que cada Desenha um triângulo.</span><span class="sxs-lookup"><span data-stu-id="786cb-108">Each `M` creates a new subpath so that the example creates two subpaths that each draw a triangle.</span></span>  
  
 [!code-xaml[GeometrySample#58](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#58)]  
  
 <span data-ttu-id="786cb-109">(Observe que essa sintaxe de atributo na verdade cria um <xref:System.Windows.Media.StreamGeometry>, uma versão leve de um <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="786cb-109">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="786cb-110">Para obter mais informações, consulte o [sintaxe de marcação de caminho](path-markup-syntax.md) página.)</span><span class="sxs-lookup"><span data-stu-id="786cb-110">For more information, see the [Path Markup Syntax](path-markup-syntax.md) page.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="786cb-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="786cb-111">See also</span></span>

- [<span data-ttu-id="786cb-112">Visão geral de geometria</span><span class="sxs-lookup"><span data-stu-id="786cb-112">Geometry Overview</span></span>](geometry-overview.md)
