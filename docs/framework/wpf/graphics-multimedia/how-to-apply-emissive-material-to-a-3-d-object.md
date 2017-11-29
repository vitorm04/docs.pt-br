---
title: Como aplicar material emissivo a um objeto 3D
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
helpviewer_keywords:
- EmissiveMaterial [WPF], applying to 3-D objects
- 3-D objects [WPF], applying EmissiveMaterial
ms.assetid: fd442cc2-5adc-487a-ba70-e45ed54bb3b4
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 069ab4e417d639a36a9168fa950f4b4f6df4c2c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-apply-emissive-material-to-a-3-d-object"></a><span data-ttu-id="1d868-102">Como aplicar material emissivo a um objeto 3D</span><span class="sxs-lookup"><span data-stu-id="1d868-102">How to: Apply Emissive Material to a 3-D Object</span></span>
<span data-ttu-id="1d868-103">O exemplo a seguir mostra como usar <xref:System.Windows.Media.Media3D.EmissiveMaterial> para adicionar a cor a um Material existente igual à cor do pincel do EmissiveMaterial.</span><span class="sxs-lookup"><span data-stu-id="1d868-103">The following example shows how to use <xref:System.Windows.Media.Media3D.EmissiveMaterial> to add color to an existing Material equal to the color of the EmissiveMaterial's brush.</span></span> <span data-ttu-id="1d868-104">O código abaixo mostra <xref:System.Windows.Media.Media3D.DiffuseMaterial> e <xref:System.Windows.Media.Media3D.EmissiveMaterial> aplicado em combinação para adicionar azul a aparência do DiffuseMaterial.</span><span class="sxs-lookup"><span data-stu-id="1d868-104">The code below shows <xref:System.Windows.Media.Media3D.DiffuseMaterial> and <xref:System.Windows.Media.Media3D.EmissiveMaterial> applied in combination to add blue to the DiffuseMaterial's appearance.</span></span>  
  
 [!code-xaml[3DGallery_snip#EmmisiveMaterialAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emmisivematerialanimationexampleinline1)]  
  
 <span data-ttu-id="1d868-105">No código de procedimento:</span><span class="sxs-lookup"><span data-stu-id="1d868-105">In procedural code:</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexampleinline1)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="1d868-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1d868-106">Example</span></span>  
 <span data-ttu-id="1d868-107">O código a seguir mostra o exemplo completo em XAML.</span><span class="sxs-lookup"><span data-stu-id="1d868-107">The following code shows the entire sample in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#EmissiveMaterialExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emissivematerialexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="1d868-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1d868-108">Example</span></span>  
 <span data-ttu-id="1d868-109">Abaixo está o exemplo inteiro no código de procedimento.</span><span class="sxs-lookup"><span data-stu-id="1d868-109">Below is the entire sample in procedural code.</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="1d868-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1d868-110">See Also</span></span>  
 [<span data-ttu-id="1d868-111">Criar uma cena 3D</span><span class="sxs-lookup"><span data-stu-id="1d868-111">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [<span data-ttu-id="1d868-112">Visão geral de elementos gráficos 3D</span><span class="sxs-lookup"><span data-stu-id="1d868-112">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [<span data-ttu-id="1d868-113">Animar propriedades de material em uma cena 3D</span><span class="sxs-lookup"><span data-stu-id="1d868-113">Animate Material Properties in a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-material-properties-in-a-3-d-scene.md)  
 [<span data-ttu-id="1d868-114">Aplicar material à frente e ao verso de um objeto 3D</span><span class="sxs-lookup"><span data-stu-id="1d868-114">Apply Material to the Front and Back of a 3-D Object</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-material-to-the-front-and-back-of-a-3-d-object.md)
