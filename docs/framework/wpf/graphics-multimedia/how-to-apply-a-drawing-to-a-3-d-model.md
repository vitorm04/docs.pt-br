---
title: 'Como: Aplicar um desenho a um modelo 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3D models
- 3D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 5b10630ab674fa9489cdf7ad53516a680f19da08
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112174"
---
# <a name="how-to-apply-a-drawing-to-a-3d-model"></a><span data-ttu-id="ffaaa-102">Como: Aplicar um desenho a um modelo 3D</span><span class="sxs-lookup"><span data-stu-id="ffaaa-102">How to: Apply a Drawing to a 3D Model</span></span>

<span data-ttu-id="ffaaa-103">Este exemplo mostra como <xref:System.Windows.Media.DrawingBrush> usar <xref:System.Windows.Media.Media3D.Material> um como o aplicado a um modelo 3D.</span><span class="sxs-lookup"><span data-stu-id="ffaaa-103">This example shows how to use a <xref:System.Windows.Media.DrawingBrush> as the <xref:System.Windows.Media.Media3D.Material> applied to a 3D model.</span></span>

<span data-ttu-id="ffaaa-104">O código a <xref:System.Windows.Media.DrawingGroup> seguir define a <xref:System.Windows.Media.DrawingBrush>como o conteúdo de a .</span><span class="sxs-lookup"><span data-stu-id="ffaaa-104">The following code defines a <xref:System.Windows.Media.DrawingGroup> as the content of a <xref:System.Windows.Media.DrawingBrush>.</span></span>  <span data-ttu-id="ffaaa-105">O <xref:System.Windows.Media.DrawingBrush> é definido <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> como <xref:System.Windows.Media.Media3D.DiffuseMaterial> propriedade do aplicado a um plano 3D.</span><span class="sxs-lookup"><span data-stu-id="ffaaa-105">The <xref:System.Windows.Media.DrawingBrush> is set as the <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> property of the <xref:System.Windows.Media.Media3D.DiffuseMaterial> applied to a 3D plane.</span></span>

> [!NOTE]
> <span data-ttu-id="ffaaa-106">Muitas vezes é desejável definir objetos e valores complexos como o desenho abaixo como recursos que podem ser reutilizados e simplificar seu código.</span><span class="sxs-lookup"><span data-stu-id="ffaaa-106">It is often desirable to define complex objects and values like the drawing below as resources which can be reused and simplify your code.</span></span> <span data-ttu-id="ffaaa-107">Consulte [os recursos xaml](../../../desktop-wpf/fundamentals/xaml-resources-define.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="ffaaa-107">See [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md) for more information.</span></span>

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]

## <a name="example"></a><span data-ttu-id="ffaaa-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ffaaa-108">Example</span></span>

<span data-ttu-id="ffaaa-109">O código a seguir mostra toda a amostra.</span><span class="sxs-lookup"><span data-stu-id="ffaaa-109">The following code shows the entire sample.</span></span>

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]

## <a name="see-also"></a><span data-ttu-id="ffaaa-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="ffaaa-110">See also</span></span>

- [<span data-ttu-id="ffaaa-111">Recursos XAML</span><span class="sxs-lookup"><span data-stu-id="ffaaa-111">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="ffaaa-112">Criar uma cena 3D</span><span class="sxs-lookup"><span data-stu-id="ffaaa-112">Create a 3D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="ffaaa-113">Visão geral dos objetos de desenho</span><span class="sxs-lookup"><span data-stu-id="ffaaa-113">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="ffaaa-114">Visão geral de gráficos 3D</span><span class="sxs-lookup"><span data-stu-id="ffaaa-114">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
