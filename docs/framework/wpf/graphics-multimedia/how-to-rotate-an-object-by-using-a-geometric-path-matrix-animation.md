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
ms.openlocfilehash: 63dc873a2b840ea3f870a8c60c5691ab271c1c9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187407"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation"></a><span data-ttu-id="28341-102">Como girar um objeto usando um caminho geométrico (animação de matriz)</span><span class="sxs-lookup"><span data-stu-id="28341-102">How to: Rotate an Object by Using a Geometric Path (Matrix Animation)</span></span>
<span data-ttu-id="28341-103">Este exemplo mostra como <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> usar <xref:System.Windows.Media.MatrixTransform> a e a para girar (pivô) <xref:System.Windows.Media.PathGeometry> um objeto ao longo de um caminho geométrico definido por um objeto.</span><span class="sxs-lookup"><span data-stu-id="28341-103">This example shows how to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> and a <xref:System.Windows.Media.MatrixTransform> to rotate (pivot) an object along a geometric path defined by a <xref:System.Windows.Media.PathGeometry> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28341-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="28341-104">Example</span></span>  
 <span data-ttu-id="28341-105">O exemplo a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> seguir usa <xref:System.Windows.Media.MatrixTransform.Matrix%2A> o objeto <xref:System.Windows.Media.MatrixTransform>para animar a propriedade de um .</span><span class="sxs-lookup"><span data-stu-id="28341-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="28341-106">O <xref:System.Windows.Media.MatrixTransform> é aplicado a um botão e faz com que ele se mova ao longo de um caminho curvo.</span><span class="sxs-lookup"><span data-stu-id="28341-106">The <xref:System.Windows.Media.MatrixTransform> is applied to a button and causes it to move along a curved path.</span></span> <span data-ttu-id="28341-107">Como <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> a propriedade `true`está definida para , o retângulo gira ao longo da tangente do caminho.</span><span class="sxs-lookup"><span data-stu-id="28341-107">Because the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> property is set to `true`, the rectangle rotates along the tangent of the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 <span data-ttu-id="28341-108">Para obter a amostra completa, consulte [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span><span class="sxs-lookup"><span data-stu-id="28341-108">For the complete sample, see [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span></span>  
  
 <span data-ttu-id="28341-109">A versão de código da <xref:System.Windows.Media.Animation.Storyboard> amostra anterior <xref:System.Windows.Media.EllipseGeometry>usou um para animar o , embora apenas uma animação foi aplicada.</span><span class="sxs-lookup"><span data-stu-id="28341-109">The code version of the preceding sample used a <xref:System.Windows.Media.Animation.Storyboard> to animate the <xref:System.Windows.Media.EllipseGeometry>, even though only one animation was applied.</span></span> <span data-ttu-id="28341-110">Uma maneira mais fácil de aplicar uma única animação <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> a uma propriedade em código é usar o método.</span><span class="sxs-lookup"><span data-stu-id="28341-110">An easier way to apply a single animation to a property in code is to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method.</span></span> <span data-ttu-id="28341-111">Por exemplo, consulte [Animar uma propriedade sem usar um storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="28341-111">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28341-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="28341-112">See also</span></span>

- [<span data-ttu-id="28341-113">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="28341-113">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="28341-114">Tópicos explicativos de animação do caminho</span><span class="sxs-lookup"><span data-stu-id="28341-114">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
- [<span data-ttu-id="28341-115">Exemplo de animação de caminho</span><span class="sxs-lookup"><span data-stu-id="28341-115">Path Animation Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
