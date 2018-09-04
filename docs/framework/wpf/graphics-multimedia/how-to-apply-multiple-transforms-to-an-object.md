---
title: Como aplicar várias transformações a um objeto
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- grouping Transform objects [WPF]
- Transform objects [WPF], grouping
- graphics [WPF], grouping Transform objects
- TransformGroup [WPF]
ms.assetid: 98cd1921-12bc-4bf5-8193-529228fb7402
ms.openlocfilehash: 0700a7ae3f18f745b0d479ace3acbf2d7fbd9722
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43659620"
---
# <a name="how-to-apply-multiple-transforms-to-an-object"></a><span data-ttu-id="99984-102">Como aplicar várias transformações a um objeto</span><span class="sxs-lookup"><span data-stu-id="99984-102">How to: Apply Multiple Transforms to an Object</span></span>
<span data-ttu-id="99984-103">Este exemplo mostra como usar um <xref:System.Windows.Media.TransformGroup> para agrupar dois ou mais <xref:System.Windows.Media.Transform> objetos em uma única composição <xref:System.Windows.Media.Transform>.</span><span class="sxs-lookup"><span data-stu-id="99984-103">This example shows how to use a <xref:System.Windows.Media.TransformGroup> to group two or more <xref:System.Windows.Media.Transform> objects into a single composite <xref:System.Windows.Media.Transform>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99984-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="99984-104">Example</span></span>  
 <span data-ttu-id="99984-105">O exemplo a seguir usa uma <xref:System.Windows.Media.TransformGroup> para aplicar uma <xref:System.Windows.Media.ScaleTransform> e uma <xref:System.Windows.Media.RotateTransform> para um <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="99984-105">The following example uses a <xref:System.Windows.Media.TransformGroup> to apply a <xref:System.Windows.Media.ScaleTransform> and a <xref:System.Windows.Media.RotateTransform> to a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-xaml[Transforms_snip#MultipleTransformExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MultipleTransformExample.xaml#multipletransformexamplewholepage)]  
  
 [!code-csharp[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/MultipleTransformsExample.cs#multipletransformscodeexamplewholepage)]
 [!code-vb[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/MultipleTransformsExample.vb#multipletransformscodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="99984-106">Consulte também</span><span class="sxs-lookup"><span data-stu-id="99984-106">See Also</span></span>  
 <xref:System.Windows.UIElement.RenderTransform%2A>  
 <xref:System.Windows.Media.TransformGroup>  
 [<span data-ttu-id="99984-107">Visão geral de transformações</span><span class="sxs-lookup"><span data-stu-id="99984-107">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="99984-108">Exemplo de transformações 2D</span><span class="sxs-lookup"><span data-stu-id="99984-108">2-D Transforms Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=158252)
