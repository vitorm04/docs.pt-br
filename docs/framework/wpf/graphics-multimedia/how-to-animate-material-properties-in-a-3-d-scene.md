---
title: 'Como: Animar propriedades materiais em uma cena 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- Material properties [WPF], animating in 3D scenes
- animation [WPF], Material properties in 3D scenes
- 3D scenes [WPF], animating Material properties
ms.assetid: 229fd6eb-7401-4992-b0c9-8b28de230c0f
ms.openlocfilehash: db59debcd7558cde52d8604cb04c8c4e68921825
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112187"
---
# <a name="how-to-animate-material-properties-in-a-3d-scene"></a>Como: Animar propriedades materiais em uma cena 3D
Este exemplo mostra como <xref:System.Windows.Media.Brush.Opacity%2A> animar a <xref:System.Windows.Media.Media3D.Material> propriedade do aplicado a um modelo 3D.  
  
 O exemplo de código <xref:System.Windows.Media.LinearGradientBrush> a <xref:System.Windows.Media.Media3D.Material> seguir define o usado como o aplicado ao objeto 3D.  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline1)]  
  
 A <xref:System.Windows.Media.Brush.Opacity%2A> propriedade <xref:System.Windows.Media.LinearGradientBrush> disso é animada usando o exemplo de código abaixo.  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline2)]  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra toda a amostra.  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexamplewholepage)]  
  
## <a name="see-also"></a>Confira também

- [Criar uma cena 3D](how-to-create-a-3-d-scene.md)
- [Visão geral de gráficos 3D](3-d-graphics-overview.md)
