---
title: Como girar um objeto usando um caminho geométrico (animação de matriz)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
- matrix animation [WPF]
ms.assetid: 877dc9aa-6bdc-4beb-8772-3efaec32c0f0
ms.openlocfilehash: 3a35f6dda05cfe65811de16d76b288c8fbd618a7
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44133604"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation"></a><span data-ttu-id="06d4b-102">Como girar um objeto usando um caminho geométrico (animação de matriz)</span><span class="sxs-lookup"><span data-stu-id="06d4b-102">How to: Rotate an Object by Using a Geometric Path (Matrix Animation)</span></span>
<span data-ttu-id="06d4b-103">Este exemplo mostra como usar um <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> e uma <xref:System.Windows.Media.MatrixTransform> para girar um objeto ao longo de um caminho geométrico definido por um <xref:System.Windows.Media.PathGeometry> objeto.</span><span class="sxs-lookup"><span data-stu-id="06d4b-103">This example shows how to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> and a <xref:System.Windows.Media.MatrixTransform> to rotate (pivot) an object along a geometric path defined by a <xref:System.Windows.Media.PathGeometry> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06d4b-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="06d4b-104">Example</span></span>  
 <span data-ttu-id="06d4b-105">O exemplo a seguir usa o <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> objeto para animar a <xref:System.Windows.Media.MatrixTransform.Matrix%2A> propriedade de um <xref:System.Windows.Media.MatrixTransform>.</span><span class="sxs-lookup"><span data-stu-id="06d4b-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="06d4b-106">O <xref:System.Windows.Media.MatrixTransform> é aplicado a um botão e faz com que ele se mova ao longo de um caminho curvo.</span><span class="sxs-lookup"><span data-stu-id="06d4b-106">The <xref:System.Windows.Media.MatrixTransform> is applied to a button and causes it to move along a curved path.</span></span> <span data-ttu-id="06d4b-107">Porque o <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> estiver definida como `true`, o retângulo gira junto da tangente do caminho.</span><span class="sxs-lookup"><span data-stu-id="06d4b-107">Because the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> property is set to `true`, the rectangle rotates along the tangent of the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 <span data-ttu-id="06d4b-108">Para o exemplo completo, consulte [exemplo de animação de caminho](https://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="06d4b-108">For the complete sample, see [Path Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160028).</span></span>  
  
 <span data-ttu-id="06d4b-109">A versão de código do exemplo anterior usada um <xref:System.Windows.Media.Animation.Storyboard> animar o <xref:System.Windows.Media.EllipseGeometry>, mesmo que apenas uma animação foi aplicada.</span><span class="sxs-lookup"><span data-stu-id="06d4b-109">The code version of the preceding sample used a <xref:System.Windows.Media.Animation.Storyboard> to animate the <xref:System.Windows.Media.EllipseGeometry>, even though only one animation was applied.</span></span> <span data-ttu-id="06d4b-110">Uma maneira fácil de aplicar uma única animação a uma propriedade no código é usar o <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> método.</span><span class="sxs-lookup"><span data-stu-id="06d4b-110">An easier way to apply a single animation to a property in code is to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method.</span></span> <span data-ttu-id="06d4b-111">Para obter um exemplo, consulte [Animar uma propriedade sem usar um storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="06d4b-111">For an example, see [Animate a Property Without Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06d4b-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="06d4b-112">See Also</span></span>  
 [<span data-ttu-id="06d4b-113">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="06d4b-113">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="06d4b-114">Tópicos explicativos de animação do caminho</span><span class="sxs-lookup"><span data-stu-id="06d4b-114">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)  
 [<span data-ttu-id="06d4b-115">Exemplo de animação de caminho</span><span class="sxs-lookup"><span data-stu-id="06d4b-115">Path Animation Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160028)
