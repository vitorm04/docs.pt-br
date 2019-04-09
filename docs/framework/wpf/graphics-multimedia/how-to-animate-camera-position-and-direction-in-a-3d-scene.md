---
title: 'Como: Animar posição e direção da câmera em uma cena 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], camera position in 3-D scenes
- camera direction [WPF], animating in 3-D scenes
- 3-D scenes [WPF], animating camera position
- 3-D scenes [WPF], animating camera direction
- camera position [WPF], animating in 3-D scenes
- animation [WPF], camera direction in 3-D scenes
ms.assetid: 480224b7-a5e5-4165-ba7f-ef760ddff94a
ms.openlocfilehash: b64263a495ffe845a76317aad8f5b4a14e11b31e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59145997"
---
# <a name="how-to-animate-camera-position-and-direction-in-a-3d-scene"></a>Como: Animar posição e direção da câmera em uma cena 3D
O exemplo a seguir mostra como animar a posição de uma câmera e animar a direção em que ele está apontando em uma cena 3D. Isso é feito por meio <xref:System.Windows.Media.Animation.Point3DAnimation> e <xref:System.Windows.Media.Animation.Vector3DAnimation> animar o <xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A> e <xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A> propriedades respectivamente do <xref:System.Windows.Media.Media3D.PerspectiveCamera>. Você pode usar uma animação como este para alterar de observador de uma cena em resposta a um evento.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationExample.xaml#pointvector3danimationexamplewholepage)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.Animation.Vector3DAnimation>
- <xref:System.Windows.Media.Animation.Point3DAnimation>
- [Animar a posição e a direção da câmera usando quadros principais](how-to-animate-camera-position-and-direction-using-key-frames.md)
- [Visão geral de elementos gráficos 3D](3-d-graphics-overview.md)
