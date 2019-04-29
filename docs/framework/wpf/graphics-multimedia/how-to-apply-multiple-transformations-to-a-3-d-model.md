---
title: 'Como: Aplicar várias transformações a um modelo 3D'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3-D models [WPF], applying multiple transformations to
ms.assetid: cb72245a-5560-4c96-9f58-593c66296992
ms.openlocfilehash: 7a6a0dd4942eb2430ff79ab5df4a171a4064ac1c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698935"
---
# <a name="how-to-apply-multiple-transformations-to-a-3-d-model"></a><span data-ttu-id="3179b-102">Como: Aplicar várias transformações a um modelo 3D</span><span class="sxs-lookup"><span data-stu-id="3179b-102">How to: Apply Multiple Transformations to a 3-D Model</span></span>
<span data-ttu-id="3179b-103">Este exemplo mostra como usar um <xref:System.Windows.Media.Media3D.RotateTransform3D> e um <xref:System.Windows.Media.Media3D.ScaleTransform3D> para girar e alterar a escala de um modelo 3D.</span><span class="sxs-lookup"><span data-stu-id="3179b-103">This sample shows how to use a <xref:System.Windows.Media.Media3D.RotateTransform3D> and a <xref:System.Windows.Media.Media3D.ScaleTransform3D> to rotate and change the scale of a 3-D model.</span></span> <span data-ttu-id="3179b-104">O código a seguir mostra como aplicar essas transformações para o <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> propriedade de um <xref:System.Windows.Media.Media3D.GeometryModel3D> em XAML.</span><span class="sxs-lookup"><span data-stu-id="3179b-104">The code below shows how to apply these transforms to the <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D> in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#Multiple3DTransformationsExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/MultipleTransformationsExample.xaml#multiple3dtransformationsexampleinline1)]  
  
 <span data-ttu-id="3179b-105">No código:</span><span class="sxs-lookup"><span data-stu-id="3179b-105">In code:</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/MultipleTransformationsExample.cs#multiple3dtransformationscodeexampleinline1)]
 [!code-vb[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/multipletransformationsexample.vb#multiple3dtransformationscodeexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="3179b-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3179b-106">Example</span></span>  
 <span data-ttu-id="3179b-107">O código a seguir mostra o exemplo completo em XAML.</span><span class="sxs-lookup"><span data-stu-id="3179b-107">The following code shows the entire sample in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#Multiple3DTransformationsExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/MultipleTransformationsExample.xaml#multiple3dtransformationsexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="3179b-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3179b-108">Example</span></span>  
 <span data-ttu-id="3179b-109">Abaixo está o exemplo inteiro no código.</span><span class="sxs-lookup"><span data-stu-id="3179b-109">Below is the entire sample in code.</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/MultipleTransformationsExample.cs#multiple3dtransformationscodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/multipletransformationsexample.vb#multiple3dtransformationscodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="3179b-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3179b-110">See also</span></span>

- [<span data-ttu-id="3179b-111">Transformar a escala de um modelo 3D</span><span class="sxs-lookup"><span data-stu-id="3179b-111">Transform the Scale of a 3-D Model</span></span>](how-to-transform-the-scale-of-a-3-d-model.md)
