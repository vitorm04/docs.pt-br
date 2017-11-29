---
title: "Como animar translações 3D"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], 3-D translations
- 3-D translations [WPF], animating
ms.assetid: d4eece1f-0cd2-4a2c-8370-293354c380e4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a0477943b715a23a1d6992f7e9da885ffa01061c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-3-d-translations"></a>Como animar translações 3D
Este tópico demonstra como animar uma transformação de conversão definida em um [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] modelo.  
  
 O código a seguir mostra o aplicativo de um <xref:System.Windows.Media.Media3D.TranslateTransform3D> o objeto para o <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> propriedade de um <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline1)]  
  
 O <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> propriedade deste <xref:System.Windows.Media.Media3D.TranslateTransform3D> objeto é animado usando o código abaixo.  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline2)]  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra o exemplo completo.  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Criar uma cena 3D](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [Visão geral de elementos gráficos 3D](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [Visão geral de transformações](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
