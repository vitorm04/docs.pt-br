---
title: 'Como: Aplicar material emissivo a um objeto 3D'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- EmissiveMaterial [WPF], applying to 3-D objects
- 3-D objects [WPF], applying EmissiveMaterial
ms.assetid: fd442cc2-5adc-487a-ba70-e45ed54bb3b4
ms.openlocfilehash: b898148fa07950e3ad1eddcaf9206f7d6a837241
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163111"
---
# <a name="how-to-apply-emissive-material-to-a-3-d-object"></a>Como: Aplicar material emissivo a um objeto 3D
O exemplo a seguir mostra como usar <xref:System.Windows.Media.Media3D.EmissiveMaterial> para adicionar cores a um Material existente igual à cor do pincel do EmissiveMaterial. O código a seguir mostra <xref:System.Windows.Media.Media3D.DiffuseMaterial> e <xref:System.Windows.Media.Media3D.EmissiveMaterial> aplicado em combinação para adicionar o azul a aparência de DiffuseMaterial.  
  
 [!code-xaml[3DGallery_snip#EmmisiveMaterialAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emmisivematerialanimationexampleinline1)]  
  
 No código de procedimento:  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexampleinline1)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexampleinline1)]  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra o exemplo completo em XAML.  
  
 [!code-xaml[3DGallery_snip#EmissiveMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emissivematerialexamplewholepage)]  
  
## <a name="example"></a>Exemplo  
 Abaixo está o exemplo inteiro no código de procedimento.  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexamplewholepage)]  
  
## <a name="see-also"></a>Consulte também

- [Criar uma cena 3D](how-to-create-a-3-d-scene.md)
- [Visão geral de elementos gráficos 3D](3-d-graphics-overview.md)
- [Animar propriedades de material em uma cena 3D](how-to-animate-material-properties-in-a-3-d-scene.md)
- [Aplicar material à frente e ao verso de um objeto 3D](how-to-apply-material-to-the-front-and-back-of-a-3-d-object.md)
