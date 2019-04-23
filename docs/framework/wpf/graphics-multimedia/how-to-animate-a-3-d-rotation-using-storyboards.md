---
title: 'Como: Animar uma rotação 3D usando storyboards'
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF]
- 3-D translations [WPF], animating [WPF], with Storyboards
- animation [WPF], 3-D translations [WPF], with Storyboards
ms.assetid: 1020e44e-e21e-49a8-be53-53cbc1910e83
ms.openlocfilehash: 03b01205f1a31426a01b09533b350682c384df4b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59146192"
---
# <a name="how-to-animate-a-3-d-rotation-using-storyboards"></a>Como: Animar uma rotação 3D usando storyboards
O exemplo a seguir mostra como fazer com que um objeto 3D gire enquanto ele "vibra" pela animação a <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> e <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> propriedades de um <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> objeto. Isso <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> objeto Especifica a transformação de rotação do objeto 3D e portanto animando suas propriedades cria o efeito de rotação desejado. Dentro do Storyboard <xref:System.Windows.Media.Animation.DoubleAnimation> é usado para animar a <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> propriedade enquanto <xref:System.Windows.Media.Animation.Vector3DAnimation> é usado para animar o <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> propriedade.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[Animation3DGallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
## <a name="see-also"></a>Consulte também

- [Animar uma rotação 3D usando Rotation3DAnimation](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [Animar uma rotação 3D usando quadros principais (Rotation3DAnimationUsingKeyFrames)](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [Visão geral de elementos gráficos 3D](3-d-graphics-overview.md)
- [Visão geral de storyboards](storyboards-overview.md)
