---
title: 'Como: Aplicar um desenho a um modelo 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 14470d0adeb948ea46a0720b5713c20fb7d8e6d8
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855872"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a><span data-ttu-id="aff77-102">Como: Aplicar um desenho a um modelo 3D</span><span class="sxs-lookup"><span data-stu-id="aff77-102">How to: Apply a Drawing to a 3-D Model</span></span>

<span data-ttu-id="aff77-103">Este exemplo mostra como usar um <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.Media3D.Material> como aplicado a um modelo 3D.</span><span class="sxs-lookup"><span data-stu-id="aff77-103">This example shows how to use a <xref:System.Windows.Media.DrawingBrush> as the <xref:System.Windows.Media.Media3D.Material> applied to a 3-D model.</span></span>

<span data-ttu-id="aff77-104">O código a seguir define <xref:System.Windows.Media.DrawingGroup> um como o conteúdo de <xref:System.Windows.Media.DrawingBrush>um.</span><span class="sxs-lookup"><span data-stu-id="aff77-104">The following code defines a <xref:System.Windows.Media.DrawingGroup> as the content of a <xref:System.Windows.Media.DrawingBrush>.</span></span>  <span data-ttu-id="aff77-105">O <xref:System.Windows.Media.DrawingBrush> é definido como a <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> propriedade de <xref:System.Windows.Media.Media3D.DiffuseMaterial> aplicado a um plano 3D.</span><span class="sxs-lookup"><span data-stu-id="aff77-105">The <xref:System.Windows.Media.DrawingBrush> is set as the <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> property of the <xref:System.Windows.Media.Media3D.DiffuseMaterial> applied to a 3-D plane.</span></span>

> [!NOTE]
> <span data-ttu-id="aff77-106">Geralmente, é desejável definir objetos e valores complexos, como o desenho abaixo, como recursos que podem ser reutilizados e simplificar seu código.</span><span class="sxs-lookup"><span data-stu-id="aff77-106">It is often desirable to define complex objects and values like the drawing below as resources which can be reused and simplify your code.</span></span> <span data-ttu-id="aff77-107">Consulte [recursos XAML](../advanced/xaml-resources.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="aff77-107">See [XAML Resources](../advanced/xaml-resources.md) for more information.</span></span>

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]

## <a name="example"></a><span data-ttu-id="aff77-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aff77-108">Example</span></span>

<span data-ttu-id="aff77-109">O código a seguir mostra a amostra inteira.</span><span class="sxs-lookup"><span data-stu-id="aff77-109">The following code shows the entire sample.</span></span>

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]

## <a name="see-also"></a><span data-ttu-id="aff77-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aff77-110">See also</span></span>

- [<span data-ttu-id="aff77-111">Recursos XAML</span><span class="sxs-lookup"><span data-stu-id="aff77-111">XAML Resources</span></span>](../advanced/xaml-resources.md)
- [<span data-ttu-id="aff77-112">Criar uma cena 3D</span><span class="sxs-lookup"><span data-stu-id="aff77-112">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="aff77-113">Visão geral dos objetos de desenho</span><span class="sxs-lookup"><span data-stu-id="aff77-113">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="aff77-114">Visão geral de elementos gráficos 3D</span><span class="sxs-lookup"><span data-stu-id="aff77-114">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
