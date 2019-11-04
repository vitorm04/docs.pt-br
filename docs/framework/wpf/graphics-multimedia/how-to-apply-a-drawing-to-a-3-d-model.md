---
title: Como aplicar um desenho a um modelo 3D
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 311a3ac1d9fa219a3a365d506d9d0c3e8b6bc229
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459372"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a><span data-ttu-id="0d5e2-102">Como aplicar um desenho a um modelo 3D</span><span class="sxs-lookup"><span data-stu-id="0d5e2-102">How to: Apply a Drawing to a 3-D Model</span></span>

<span data-ttu-id="0d5e2-103">Este exemplo mostra como usar um <xref:System.Windows.Media.DrawingBrush> como o <xref:System.Windows.Media.Media3D.Material> aplicado a um modelo 3D.</span><span class="sxs-lookup"><span data-stu-id="0d5e2-103">This example shows how to use a <xref:System.Windows.Media.DrawingBrush> as the <xref:System.Windows.Media.Media3D.Material> applied to a 3-D model.</span></span>

<span data-ttu-id="0d5e2-104">O código a seguir define um <xref:System.Windows.Media.DrawingGroup> como o conteúdo de um <xref:System.Windows.Media.DrawingBrush>.</span><span class="sxs-lookup"><span data-stu-id="0d5e2-104">The following code defines a <xref:System.Windows.Media.DrawingGroup> as the content of a <xref:System.Windows.Media.DrawingBrush>.</span></span>  <span data-ttu-id="0d5e2-105">O <xref:System.Windows.Media.DrawingBrush> é definido como a propriedade <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> do <xref:System.Windows.Media.Media3D.DiffuseMaterial> aplicado a um plano 3D.</span><span class="sxs-lookup"><span data-stu-id="0d5e2-105">The <xref:System.Windows.Media.DrawingBrush> is set as the <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> property of the <xref:System.Windows.Media.Media3D.DiffuseMaterial> applied to a 3-D plane.</span></span>

> [!NOTE]
> <span data-ttu-id="0d5e2-106">Geralmente, é desejável definir objetos e valores complexos, como o desenho abaixo, como recursos que podem ser reutilizados e simplificar seu código.</span><span class="sxs-lookup"><span data-stu-id="0d5e2-106">It is often desirable to define complex objects and values like the drawing below as resources which can be reused and simplify your code.</span></span> <span data-ttu-id="0d5e2-107">Consulte [recursos XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="0d5e2-107">See [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md) for more information.</span></span>

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]

## <a name="example"></a><span data-ttu-id="0d5e2-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0d5e2-108">Example</span></span>

<span data-ttu-id="0d5e2-109">O código a seguir mostra a amostra inteira.</span><span class="sxs-lookup"><span data-stu-id="0d5e2-109">The following code shows the entire sample.</span></span>

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]

## <a name="see-also"></a><span data-ttu-id="0d5e2-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d5e2-110">See also</span></span>

- [<span data-ttu-id="0d5e2-111">Recursos XAML</span><span class="sxs-lookup"><span data-stu-id="0d5e2-111">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="0d5e2-112">Criar uma cena 3D</span><span class="sxs-lookup"><span data-stu-id="0d5e2-112">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="0d5e2-113">Visão geral dos objetos de desenho</span><span class="sxs-lookup"><span data-stu-id="0d5e2-113">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="0d5e2-114">Visão geral de elementos gráficos 3D</span><span class="sxs-lookup"><span data-stu-id="0d5e2-114">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
