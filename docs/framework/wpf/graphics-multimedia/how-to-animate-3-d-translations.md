---
title: 'Como: Animar translações 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3-D translations
- 3-D translations [WPF], animating
ms.assetid: d4eece1f-0cd2-4a2c-8370-293354c380e4
ms.openlocfilehash: 3e27c2d5f0cd44235a1d897b1b8f057808ae6bd8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61762196"
---
# <a name="how-to-animate-3-d-translations"></a><span data-ttu-id="1c014-102">Como: Animar translações 3D</span><span class="sxs-lookup"><span data-stu-id="1c014-102">How to: Animate 3-D Translations</span></span>
<span data-ttu-id="1c014-103">Este tópico demonstra como animar uma transformação de conversão definida em um [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] modelo.</span><span class="sxs-lookup"><span data-stu-id="1c014-103">This topic demonstrates how to animate a translation transformation set on a [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] model.</span></span>  
  
 <span data-ttu-id="1c014-104">O código a seguir mostra o aplicativo de um <xref:System.Windows.Media.Media3D.TranslateTransform3D> do objeto para o <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> propriedade de um <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span><span class="sxs-lookup"><span data-stu-id="1c014-104">The code below shows the application of a <xref:System.Windows.Media.Media3D.TranslateTransform3D> object to the <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline1)]  
  
 <span data-ttu-id="1c014-105">O <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> propriedade deste <xref:System.Windows.Media.Media3D.TranslateTransform3D> objeto é animado usando o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="1c014-105">The <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> property of this <xref:System.Windows.Media.Media3D.TranslateTransform3D> object is animated using the code below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline2)]  
  
## <a name="example"></a><span data-ttu-id="1c014-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c014-106">Example</span></span>  
 <span data-ttu-id="1c014-107">O código a seguir mostra o exemplo completo.</span><span class="sxs-lookup"><span data-stu-id="1c014-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="1c014-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1c014-108">See also</span></span>

- [<span data-ttu-id="1c014-109">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="1c014-109">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="1c014-110">Criar uma cena 3D</span><span class="sxs-lookup"><span data-stu-id="1c014-110">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="1c014-111">Visão geral de elementos gráficos 3D</span><span class="sxs-lookup"><span data-stu-id="1c014-111">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="1c014-112">Visão geral de transformações</span><span class="sxs-lookup"><span data-stu-id="1c014-112">Transforms Overview</span></span>](transforms-overview.md)
