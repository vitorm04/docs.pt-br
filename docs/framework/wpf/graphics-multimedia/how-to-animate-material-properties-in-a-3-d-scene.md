---
title: 'Como: Animar propriedades de material em uma cena 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- Material properties [WPF], animating in 3-D scenes
- animation [WPF], Material properties in 3-D scenes
- 3-D scenes [WPF], animating Material properties
ms.assetid: 229fd6eb-7401-4992-b0c9-8b28de230c0f
ms.openlocfilehash: 58e880a2828d21ee76f7fac6bdcf313e8454e65b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090895"
---
# <a name="how-to-animate-material-properties-in-a-3-d-scene"></a><span data-ttu-id="3c181-102">Como: Animar propriedades de material em uma cena 3D</span><span class="sxs-lookup"><span data-stu-id="3c181-102">How to: Animate Material Properties in a 3-D Scene</span></span>
<span data-ttu-id="3c181-103">Este exemplo mostra como animar a <xref:System.Windows.Media.Brush.Opacity%2A> propriedade do <xref:System.Windows.Media.Media3D.Material> aplicados a um [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] modelo.</span><span class="sxs-lookup"><span data-stu-id="3c181-103">This example shows how to animate the <xref:System.Windows.Media.Brush.Opacity%2A> property of the <xref:System.Windows.Media.Media3D.Material> applied to a [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] model.</span></span>  
  
 <span data-ttu-id="3c181-104">O exemplo de código a seguir define o <xref:System.Windows.Media.LinearGradientBrush> usado como o <xref:System.Windows.Media.Media3D.Material> aplicado ao objeto 3D.</span><span class="sxs-lookup"><span data-stu-id="3c181-104">The following code example defines the <xref:System.Windows.Media.LinearGradientBrush> used as the <xref:System.Windows.Media.Media3D.Material> applied to the 3D object.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline1)]  
  
 <span data-ttu-id="3c181-105">O <xref:System.Windows.Media.Brush.Opacity%2A> propriedade deste <xref:System.Windows.Media.LinearGradientBrush> é animada usando o exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="3c181-105">The <xref:System.Windows.Media.Brush.Opacity%2A> property of this <xref:System.Windows.Media.LinearGradientBrush> is animated using the code example below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline2)]  
  
## <a name="example"></a><span data-ttu-id="3c181-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3c181-106">Example</span></span>  
 <span data-ttu-id="3c181-107">O código a seguir mostra o exemplo completo.</span><span class="sxs-lookup"><span data-stu-id="3c181-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="3c181-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3c181-108">See also</span></span>

- [<span data-ttu-id="3c181-109">Criar uma cena 3D</span><span class="sxs-lookup"><span data-stu-id="3c181-109">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="3c181-110">Visão geral de elementos gráficos 3D</span><span class="sxs-lookup"><span data-stu-id="3c181-110">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
