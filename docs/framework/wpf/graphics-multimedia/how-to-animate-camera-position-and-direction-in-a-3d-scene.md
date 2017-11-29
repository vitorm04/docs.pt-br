---
title: "Como animar posição e direção da câmera em uma cena 3D"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], camera position in 3-D scenes
- camera direction [WPF], animating in 3-D scenes
- 3-D scenes [WPF], animating camera position
- 3-D scenes [WPF], animating camera direction
- camera position [WPF], animating in 3-D scenes
- animation [WPF], camera direction in 3-D scenes
ms.assetid: 480224b7-a5e5-4165-ba7f-ef760ddff94a
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 790260f974dcb0be398af202cc7156fc91efed91
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-camera-position-and-direction-in-a-3d-scene"></a>Como animar posição e direção da câmera em uma cena 3D
O exemplo a seguir mostra como animar a posição de uma câmera e animar a direção que ele está apontando em uma cena 3D. Isso é feito usando <xref:System.Windows.Media.Animation.Point3DAnimation> e <xref:System.Windows.Media.Animation.Vector3DAnimation> para animar a <xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A> e <xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A> propriedades respectivamente a <xref:System.Windows.Media.Media3D.PerspectiveCamera>. Você pode usar uma animação assim para alterar a exibição do observador de uma cena em resposta a um evento.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationExample.xaml#pointvector3danimationexamplewholepage)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.Animation.Vector3DAnimation>  
 <xref:System.Windows.Media.Animation.Point3DAnimation>  
 [Animar a posição e a direção da câmera usando quadros principais](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-camera-position-and-direction-using-key-frames.md)  
 [Visão geral de elementos gráficos 3D](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
