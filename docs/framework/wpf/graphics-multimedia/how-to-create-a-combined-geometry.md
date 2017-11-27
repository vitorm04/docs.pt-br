---
title: Como criar uma geometria combinada
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- combining geometries [WPF]
- graphics [WPF], combining geometries
- geometries [WPF], combining
ms.assetid: 54c3277c-6b6e-4b25-91be-fda0bbc706b4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2be0471f27d26b145cc29847a08bf3bc3b1d51ff
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-create-a-combined-geometry"></a><span data-ttu-id="a1b6e-102">Como criar uma geometria combinada</span><span class="sxs-lookup"><span data-stu-id="a1b6e-102">How to: Create a Combined Geometry</span></span>
<span data-ttu-id="a1b6e-103">Este exemplo mostra como combinar geometrias.</span><span class="sxs-lookup"><span data-stu-id="a1b6e-103">This example shows how to combine geometries.</span></span> <span data-ttu-id="a1b6e-104">Para combinar duas geometrias, use um <xref:System.Windows.Media.CombinedGeometry> objeto.</span><span class="sxs-lookup"><span data-stu-id="a1b6e-104">To combine two geometries, use a <xref:System.Windows.Media.CombinedGeometry> object.</span></span> <span data-ttu-id="a1b6e-105">Definir seu <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> e <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> propriedades com as duas geometrias para combinar e definir o <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> propriedade, que determina como as geometrias serão combinadas em conjunto, para `Union`, `Intersect`, `Exclude`, ou `Xor`.</span><span class="sxs-lookup"><span data-stu-id="a1b6e-105">Set its <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> properties  with the two geometries to combine, and set the <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> property, which determines how the geometries will be combined together, to `Union`, `Intersect`, `Exclude`, or `Xor`.</span></span>  
  
 <span data-ttu-id="a1b6e-106">Para criar uma geometria composta de duas ou mais geometrias, use um <xref:System.Windows.Media.GeometryGroup>.</span><span class="sxs-lookup"><span data-stu-id="a1b6e-106">To create a composite geometry from two or more geometries, use a <xref:System.Windows.Media.GeometryGroup>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1b6e-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a1b6e-107">Example</span></span>  
 <span data-ttu-id="a1b6e-108">No exemplo a seguir, uma <xref:System.Windows.Media.CombinedGeometry> está definida com um modo de combinação de geometria de `Exclude`.</span><span class="sxs-lookup"><span data-stu-id="a1b6e-108">In the following example, a <xref:System.Windows.Media.CombinedGeometry> is defined with a geometry combine mode of `Exclude`.</span></span>  <span data-ttu-id="a1b6e-109">Ambos <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> e <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> são definidos como círculos de mesmo raio, mas com centros de deslocamento por 50.</span><span class="sxs-lookup"><span data-stu-id="a1b6e-109">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#21)]  
  
 <span data-ttu-id="a1b6e-110">![Resultados da Excluir modo de combinação](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-exclude.PNG "mil_task_combined_geometry_exclude")</span><span class="sxs-lookup"><span data-stu-id="a1b6e-110">![Results of the Exclude combine mode](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-exclude.PNG "mil_task_combined_geometry_exclude")</span></span>  
<span data-ttu-id="a1b6e-111">Geometria combinada Exclude</span><span class="sxs-lookup"><span data-stu-id="a1b6e-111">Combined Geometry Exclude</span></span>  
  
 <span data-ttu-id="a1b6e-112">Na marcação a seguir, uma <xref:System.Windows.Media.CombinedGeometry> está definida com um modo combinar de `Intersect`.</span><span class="sxs-lookup"><span data-stu-id="a1b6e-112">In the following markup, a <xref:System.Windows.Media.CombinedGeometry> is defined with a combine mode of `Intersect`.</span></span>  <span data-ttu-id="a1b6e-113">Ambos <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> e <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> são definidos como círculos de mesmo raio, mas com centros de deslocamento por 50.</span><span class="sxs-lookup"><span data-stu-id="a1b6e-113">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#22)]  
  
 <span data-ttu-id="a1b6e-114">![Resultados da interseção combinam modo](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-intersect.PNG "mil_task_combined_geometry_intersect")</span><span class="sxs-lookup"><span data-stu-id="a1b6e-114">![Results of the Intersect combine mode](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-intersect.PNG "mil_task_combined_geometry_intersect")</span></span>  
<span data-ttu-id="a1b6e-115">Geometria combinada Intersect</span><span class="sxs-lookup"><span data-stu-id="a1b6e-115">Combined Geometry Intersect</span></span>  
  
 <span data-ttu-id="a1b6e-116">Na marcação a seguir, uma <xref:System.Windows.Media.CombinedGeometry> está definida com um modo combinar de `Union`.</span><span class="sxs-lookup"><span data-stu-id="a1b6e-116">In the following markup, a <xref:System.Windows.Media.CombinedGeometry> is defined with a combine mode of `Union`.</span></span>  <span data-ttu-id="a1b6e-117">Ambos <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> e <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> são definidos como círculos de mesmo raio, mas com centros de deslocamento por 50.</span><span class="sxs-lookup"><span data-stu-id="a1b6e-117">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 <span data-ttu-id="a1b6e-118">![Resultados do modo de combinar de União](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")</span><span class="sxs-lookup"><span data-stu-id="a1b6e-118">![Results of the Union combine mode](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")</span></span>  
<span data-ttu-id="a1b6e-119">União de geometria combinada</span><span class="sxs-lookup"><span data-stu-id="a1b6e-119">Combined Geometry Union</span></span>  
  
 <span data-ttu-id="a1b6e-120">Na marcação a seguir, uma <xref:System.Windows.Media.CombinedGeometry> está definida com um modo combinar de `Xor`.</span><span class="sxs-lookup"><span data-stu-id="a1b6e-120">In the following markup, a <xref:System.Windows.Media.CombinedGeometry> is defined with a combine mode of `Xor`.</span></span>  <span data-ttu-id="a1b6e-121">Ambos <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> e <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> são definidos como círculos de mesmo raio, mas com centros de deslocamento por 50.</span><span class="sxs-lookup"><span data-stu-id="a1b6e-121">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 <span data-ttu-id="a1b6e-122">![Resultados do modo de combinar de Xor](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")</span><span class="sxs-lookup"><span data-stu-id="a1b6e-122">![Results of the Xor combine mode](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")</span></span>  
<span data-ttu-id="a1b6e-123">Geometria combinada Xor</span><span class="sxs-lookup"><span data-stu-id="a1b6e-123">Combined Geometry Xor</span></span>
