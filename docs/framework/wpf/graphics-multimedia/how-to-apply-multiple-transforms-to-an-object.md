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
ms.openlocfilehash: 544d0a26f24e5ad4ed7e2e3cfa25f8e15d1be446
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452825"
---
# <a name="how-to-apply-multiple-transforms-to-an-object"></a><span data-ttu-id="afbe3-102">Como aplicar várias transformações a um objeto</span><span class="sxs-lookup"><span data-stu-id="afbe3-102">How to: Apply Multiple Transforms to an Object</span></span>
<span data-ttu-id="afbe3-103">Este exemplo mostra como usar um <xref:System.Windows.Media.TransformGroup> para agrupar dois ou mais objetos <xref:System.Windows.Media.Transform> em um único <xref:System.Windows.Media.Transform>composto.</span><span class="sxs-lookup"><span data-stu-id="afbe3-103">This example shows how to use a <xref:System.Windows.Media.TransformGroup> to group two or more <xref:System.Windows.Media.Transform> objects into a single composite <xref:System.Windows.Media.Transform>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="afbe3-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="afbe3-104">Example</span></span>  
 <span data-ttu-id="afbe3-105">O exemplo a seguir usa uma <xref:System.Windows.Media.TransformGroup> para aplicar um <xref:System.Windows.Media.ScaleTransform> e um <xref:System.Windows.Media.RotateTransform> a um <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="afbe3-105">The following example uses a <xref:System.Windows.Media.TransformGroup> to apply a <xref:System.Windows.Media.ScaleTransform> and a <xref:System.Windows.Media.RotateTransform> to a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-xaml[Transforms_snip#MultipleTransformExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MultipleTransformExample.xaml#multipletransformexamplewholepage)]  
  
 [!code-csharp[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/MultipleTransformsExample.cs#multipletransformscodeexamplewholepage)]
 [!code-vb[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/MultipleTransformsExample.vb#multipletransformscodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="afbe3-106">Confira também</span><span class="sxs-lookup"><span data-stu-id="afbe3-106">See also</span></span>

- <xref:System.Windows.UIElement.RenderTransform%2A>
- <xref:System.Windows.Media.TransformGroup>
- [<span data-ttu-id="afbe3-107">Visão geral de transformações</span><span class="sxs-lookup"><span data-stu-id="afbe3-107">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="afbe3-108">Exemplo de transformações 2D</span><span class="sxs-lookup"><span data-stu-id="afbe3-108">2-D Transforms Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)
