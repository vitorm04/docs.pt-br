---
title: 'Como: Criar uma geometria combinada'
ms.date: 03/30/2017
helpviewer_keywords:
- combining geometries [WPF]
- graphics [WPF], combining geometries
- geometries [WPF], combining
ms.assetid: 54c3277c-6b6e-4b25-91be-fda0bbc706b4
ms.openlocfilehash: c5ebe87abd4c2cf70f8fa17f1fcc773293f3ad27
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364782"
---
# <a name="how-to-create-a-combined-geometry"></a><span data-ttu-id="7d898-102">Como: Criar uma geometria combinada</span><span class="sxs-lookup"><span data-stu-id="7d898-102">How to: Create a Combined Geometry</span></span>
<span data-ttu-id="7d898-103">Este exemplo mostra como combinar geometrias.</span><span class="sxs-lookup"><span data-stu-id="7d898-103">This example shows how to combine geometries.</span></span> <span data-ttu-id="7d898-104">Para combinar duas geometrias, use um <xref:System.Windows.Media.CombinedGeometry> objeto.</span><span class="sxs-lookup"><span data-stu-id="7d898-104">To combine two geometries, use a <xref:System.Windows.Media.CombinedGeometry> object.</span></span> <span data-ttu-id="7d898-105">Defina suas <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> e <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> propriedades com as duas geometrias a serem combinadas e defina o <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> propriedade, que determina como as geometrias serão combinadas em conjunto, para `Union`, `Intersect`, `Exclude`, ou `Xor`.</span><span class="sxs-lookup"><span data-stu-id="7d898-105">Set its <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> properties  with the two geometries to combine, and set the <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> property, which determines how the geometries will be combined together, to `Union`, `Intersect`, `Exclude`, or `Xor`.</span></span>  
  
 <span data-ttu-id="7d898-106">Para criar uma geometria composta de duas ou mais geometrias, use um <xref:System.Windows.Media.GeometryGroup>.</span><span class="sxs-lookup"><span data-stu-id="7d898-106">To create a composite geometry from two or more geometries, use a <xref:System.Windows.Media.GeometryGroup>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d898-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7d898-107">Example</span></span>  
 <span data-ttu-id="7d898-108">No exemplo a seguir, uma <xref:System.Windows.Media.CombinedGeometry> é definido com um modo de combinação de geometria de `Exclude`.</span><span class="sxs-lookup"><span data-stu-id="7d898-108">In the following example, a <xref:System.Windows.Media.CombinedGeometry> is defined with a geometry combine mode of `Exclude`.</span></span>  <span data-ttu-id="7d898-109">Ambos <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> e o <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> são definidos como círculos de mesmo raio, mas com centros deslocados por 50.</span><span class="sxs-lookup"><span data-stu-id="7d898-109">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#21](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#21)]  
  
 <span data-ttu-id="7d898-110">![Modo de combinar os resultados de Exclude](./media/mil-task-combined-geometry-exclude.PNG "mil_task_combined_geometry_exclude")</span><span class="sxs-lookup"><span data-stu-id="7d898-110">![Results of the Exclude combine mode](./media/mil-task-combined-geometry-exclude.PNG "mil_task_combined_geometry_exclude")</span></span>  
<span data-ttu-id="7d898-111">Geometria combinada Exclude</span><span class="sxs-lookup"><span data-stu-id="7d898-111">Combined Geometry Exclude</span></span>  
  
 <span data-ttu-id="7d898-112">Na marcação a seguir, uma <xref:System.Windows.Media.CombinedGeometry> é definido com um modo de combinar de `Intersect`.</span><span class="sxs-lookup"><span data-stu-id="7d898-112">In the following markup, a <xref:System.Windows.Media.CombinedGeometry> is defined with a combine mode of `Intersect`.</span></span>  <span data-ttu-id="7d898-113">Ambos <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> e o <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> são definidos como círculos de mesmo raio, mas com centros deslocados por 50.</span><span class="sxs-lookup"><span data-stu-id="7d898-113">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#22](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#22)]  
  
 <span data-ttu-id="7d898-114">![Modo de combinar os resultados da interseção](./media/mil-task-combined-geometry-intersect.PNG "mil_task_combined_geometry_intersect")</span><span class="sxs-lookup"><span data-stu-id="7d898-114">![Results of the Intersect combine mode](./media/mil-task-combined-geometry-intersect.PNG "mil_task_combined_geometry_intersect")</span></span>  
<span data-ttu-id="7d898-115">Geometria combinada Intersect</span><span class="sxs-lookup"><span data-stu-id="7d898-115">Combined Geometry Intersect</span></span>  
  
 <span data-ttu-id="7d898-116">Na marcação a seguir, uma <xref:System.Windows.Media.CombinedGeometry> é definido com um modo de combinar de `Union`.</span><span class="sxs-lookup"><span data-stu-id="7d898-116">In the following markup, a <xref:System.Windows.Media.CombinedGeometry> is defined with a combine mode of `Union`.</span></span>  <span data-ttu-id="7d898-117">Ambos <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> e o <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> são definidos como círculos de mesmo raio, mas com centros deslocados por 50.</span><span class="sxs-lookup"><span data-stu-id="7d898-117">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#23](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 <span data-ttu-id="7d898-118">![Resultados do modo de combinar de União](./media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")</span><span class="sxs-lookup"><span data-stu-id="7d898-118">![Results of the Union combine mode](./media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")</span></span>  
<span data-ttu-id="7d898-119">União de geometria combinada</span><span class="sxs-lookup"><span data-stu-id="7d898-119">Combined Geometry Union</span></span>  
  
 <span data-ttu-id="7d898-120">Na marcação a seguir, uma <xref:System.Windows.Media.CombinedGeometry> é definido com um modo de combinar de `Xor`.</span><span class="sxs-lookup"><span data-stu-id="7d898-120">In the following markup, a <xref:System.Windows.Media.CombinedGeometry> is defined with a combine mode of `Xor`.</span></span>  <span data-ttu-id="7d898-121">Ambos <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> e o <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> são definidos como círculos de mesmo raio, mas com centros deslocados por 50.</span><span class="sxs-lookup"><span data-stu-id="7d898-121">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#24](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 <span data-ttu-id="7d898-122">![Resultados do modo de combinar de Xor](./media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")</span><span class="sxs-lookup"><span data-stu-id="7d898-122">![Results of the Xor combine mode](./media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")</span></span>  
<span data-ttu-id="7d898-123">Geometria combinada Xor</span><span class="sxs-lookup"><span data-stu-id="7d898-123">Combined Geometry Xor</span></span>
