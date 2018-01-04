---
title: Como animar propriedades de material em uma cena 3D
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Material properties [WPF], animating in 3-D scenes
- animation [WPF], Material properties in 3-D scenes
- 3-D scenes [WPF], animating Material properties
ms.assetid: 229fd6eb-7401-4992-b0c9-8b28de230c0f
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 16d7ba089730a58106448d8a6889b362042532e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-material-properties-in-a-3-d-scene"></a>Como animar propriedades de material em uma cena 3D
Este exemplo mostra como animar a <xref:System.Windows.Media.Brush.Opacity%2A> propriedade o <xref:System.Windows.Media.Media3D.Material> aplicado a um [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] modelo.  
  
 O exemplo de código a seguir define o <xref:System.Windows.Media.LinearGradientBrush> usado como o <xref:System.Windows.Media.Media3D.Material> aplicado ao objeto 3D.  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline1)]  
  
 O <xref:System.Windows.Media.Brush.Opacity%2A> propriedade deste <xref:System.Windows.Media.LinearGradientBrush> é animada usando o exemplo de código abaixo.  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline2)]  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra o exemplo completo.  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexamplewholepage)]  
  
## <a name="see-also"></a>Consulte também  
 [Criar uma cena 3D](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [Visão geral de elementos gráficos 3D](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
