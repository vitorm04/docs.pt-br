---
title: "Como aplicar várias transformações a um modelo 3D"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: 3-D models [WPF], applying multiple transformations to
ms.assetid: cb72245a-5560-4c96-9f58-593c66296992
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 26832827b0e92813802073adcb4c2db99dff0807
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-apply-multiple-transformations-to-a-3-d-model"></a><span data-ttu-id="099ed-102">Como aplicar várias transformações a um modelo 3D</span><span class="sxs-lookup"><span data-stu-id="099ed-102">How to: Apply Multiple Transformations to a 3-D Model</span></span>
<span data-ttu-id="099ed-103">Este exemplo mostra como usar um <xref:System.Windows.Media.Media3D.RotateTransform3D> e um <xref:System.Windows.Media.Media3D.ScaleTransform3D> para girar e alterar a escala de um modelo 3D.</span><span class="sxs-lookup"><span data-stu-id="099ed-103">This sample shows how to use a <xref:System.Windows.Media.Media3D.RotateTransform3D> and a <xref:System.Windows.Media.Media3D.ScaleTransform3D> to rotate and change the scale of a 3-D model.</span></span> <span data-ttu-id="099ed-104">O código a seguir mostra como aplicar essas transformações para o <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> propriedade de um <xref:System.Windows.Media.Media3D.GeometryModel3D> em XAML.</span><span class="sxs-lookup"><span data-stu-id="099ed-104">The code below shows how to apply these transforms to the <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D> in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#Multiple3DTransformationsExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/MultipleTransformationsExample.xaml#multiple3dtransformationsexampleinline1)]  
  
 <span data-ttu-id="099ed-105">No código:</span><span class="sxs-lookup"><span data-stu-id="099ed-105">In code:</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/MultipleTransformationsExample.cs#multiple3dtransformationscodeexampleinline1)]
 [!code-vb[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/multipletransformationsexample.vb#multiple3dtransformationscodeexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="099ed-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="099ed-106">Example</span></span>  
 <span data-ttu-id="099ed-107">O código a seguir mostra o exemplo completo em XAML.</span><span class="sxs-lookup"><span data-stu-id="099ed-107">The following code shows the entire sample in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#Multiple3DTransformationsExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/MultipleTransformationsExample.xaml#multiple3dtransformationsexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="099ed-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="099ed-108">Example</span></span>  
 <span data-ttu-id="099ed-109">Abaixo está o exemplo inteiro no código.</span><span class="sxs-lookup"><span data-stu-id="099ed-109">Below is the entire sample in code.</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/MultipleTransformationsExample.cs#multiple3dtransformationscodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/multipletransformationsexample.vb#multiple3dtransformationscodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="099ed-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="099ed-110">See Also</span></span>  
 [<span data-ttu-id="099ed-111">Transformar a escala de um modelo 3D</span><span class="sxs-lookup"><span data-stu-id="099ed-111">Transform the Scale of a 3-D Model</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-transform-the-scale-of-a-3-d-model.md)
