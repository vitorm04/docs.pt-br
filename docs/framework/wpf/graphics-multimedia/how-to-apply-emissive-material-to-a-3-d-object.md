---
title: 'Como: Aplicar material emissivo a um objeto 3D'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- EmissiveMaterial [WPF], applying to 3D objects
- 3D objects [WPF], applying EmissiveMaterial
ms.assetid: fd442cc2-5adc-487a-ba70-e45ed54bb3b4
ms.openlocfilehash: bf32b41ec2410c01ad137ec0ca9311f7c2b70061
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112148"
---
# <a name="how-to-apply-emissive-material-to-a-3d-object"></a>Como: Aplicar material emissivo a um objeto 3D
O exemplo a seguir <xref:System.Windows.Media.Media3D.EmissiveMaterial> mostra como usar para adicionar cor a um material existente igual à cor do pincel do EmissiveMaterial. O código <xref:System.Windows.Media.Media3D.DiffuseMaterial> abaixo <xref:System.Windows.Media.Media3D.EmissiveMaterial> mostra e é aplicado em combinação para adicionar azul à aparência do DiffuseMaterial.  
  
 [!code-xaml[3DGallery_snip#EmmisiveMaterialAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emmisivematerialanimationexampleinline1)]  
  
 Em código processual:  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexampleinline1)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexampleinline1)]  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra toda a amostra em XAML.  
  
 [!code-xaml[3DGallery_snip#EmissiveMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emissivematerialexamplewholepage)]  
  
## <a name="example"></a>Exemplo  
 Abaixo está toda a amostra em código processual.  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexamplewholepage)]  
  
## <a name="see-also"></a>Confira também

- [Criar uma cena 3D](how-to-create-a-3-d-scene.md)
- [Visão geral de gráficos 3D](3-d-graphics-overview.md)
- [Propriedades de material animado em uma cena 3D](how-to-animate-material-properties-in-a-3-d-scene.md)
- [Aplique material na frente e atrás de um objeto 3D](how-to-apply-material-to-the-front-and-back-of-a-3-d-object.md)
