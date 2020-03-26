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
ms.openlocfilehash: 3ef11104b2a4fc775d29d2a388c9a70a69a3f10f
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112109"
---
# <a name="how-to-apply-multiple-transforms-to-an-object"></a><span data-ttu-id="7fc83-102">Como aplicar várias transformações a um objeto</span><span class="sxs-lookup"><span data-stu-id="7fc83-102">How to: Apply Multiple Transforms to an Object</span></span>
<span data-ttu-id="7fc83-103">Este exemplo mostra como <xref:System.Windows.Media.TransformGroup> usar um <xref:System.Windows.Media.Transform> para agrupar <xref:System.Windows.Media.Transform>dois ou mais objetos em um único composto .</span><span class="sxs-lookup"><span data-stu-id="7fc83-103">This example shows how to use a <xref:System.Windows.Media.TransformGroup> to group two or more <xref:System.Windows.Media.Transform> objects into a single composite <xref:System.Windows.Media.Transform>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7fc83-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7fc83-104">Example</span></span>  
 <span data-ttu-id="7fc83-105">O exemplo a <xref:System.Windows.Media.TransformGroup> seguir <xref:System.Windows.Media.ScaleTransform> usa <xref:System.Windows.Media.RotateTransform> a <xref:System.Windows.Controls.Button>aplicar a e a a a .</span><span class="sxs-lookup"><span data-stu-id="7fc83-105">The following example uses a <xref:System.Windows.Media.TransformGroup> to apply a <xref:System.Windows.Media.ScaleTransform> and a <xref:System.Windows.Media.RotateTransform> to a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-xaml[Transforms_snip#MultipleTransformExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MultipleTransformExample.xaml#multipletransformexamplewholepage)]  
  
 [!code-csharp[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/MultipleTransformsExample.cs#multipletransformscodeexamplewholepage)]
 [!code-vb[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/MultipleTransformsExample.vb#multipletransformscodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="7fc83-106">Confira também</span><span class="sxs-lookup"><span data-stu-id="7fc83-106">See also</span></span>

- <xref:System.Windows.UIElement.RenderTransform%2A>
- <xref:System.Windows.Media.TransformGroup>
- [<span data-ttu-id="7fc83-107">Visão geral de transformações</span><span class="sxs-lookup"><span data-stu-id="7fc83-107">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="7fc83-108">2D transforma amostra</span><span class="sxs-lookup"><span data-stu-id="7fc83-108">2D Transforms Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)
