---
title: Como animar translações 3D
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3-D translations
- 3-D translations [WPF], animating
ms.assetid: d4eece1f-0cd2-4a2c-8370-293354c380e4
ms.openlocfilehash: b9307e1c9ca13b465acd76091f364c538416a5b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-animate-3-d-translations"></a><span data-ttu-id="d82b6-102">Como animar translações 3D</span><span class="sxs-lookup"><span data-stu-id="d82b6-102">How to: Animate 3-D Translations</span></span>
<span data-ttu-id="d82b6-103">Este tópico demonstra como animar uma transformação de conversão definida em um [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] modelo.</span><span class="sxs-lookup"><span data-stu-id="d82b6-103">This topic demonstrates how to animate a translation transformation set on a [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] model.</span></span>  
  
 <span data-ttu-id="d82b6-104">O código a seguir mostra o aplicativo de um <xref:System.Windows.Media.Media3D.TranslateTransform3D> o objeto para o <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> propriedade de um <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span><span class="sxs-lookup"><span data-stu-id="d82b6-104">The code below shows the application of a <xref:System.Windows.Media.Media3D.TranslateTransform3D> object to the <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline1)]  
  
 <span data-ttu-id="d82b6-105">O <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> propriedade deste <xref:System.Windows.Media.Media3D.TranslateTransform3D> objeto é animado usando o código abaixo.</span><span class="sxs-lookup"><span data-stu-id="d82b6-105">The <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> property of this <xref:System.Windows.Media.Media3D.TranslateTransform3D> object is animated using the code below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline2)]  
  
## <a name="example"></a><span data-ttu-id="d82b6-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d82b6-106">Example</span></span>  
 <span data-ttu-id="d82b6-107">O código a seguir mostra o exemplo completo.</span><span class="sxs-lookup"><span data-stu-id="d82b6-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="d82b6-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d82b6-108">See Also</span></span>  
 [<span data-ttu-id="d82b6-109">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="d82b6-109">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="d82b6-110">Criar uma cena 3D</span><span class="sxs-lookup"><span data-stu-id="d82b6-110">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [<span data-ttu-id="d82b6-111">Visão geral de elementos gráficos 3D</span><span class="sxs-lookup"><span data-stu-id="d82b6-111">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [<span data-ttu-id="d82b6-112">Visão geral de transformações</span><span class="sxs-lookup"><span data-stu-id="d82b6-112">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
