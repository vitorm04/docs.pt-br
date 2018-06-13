---
title: Como animar uma rotação 3D usando storyboards
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF]
- 3-D translations [WPF], animating [WPF], with Storyboards
- animation [WPF], 3-D translations [WPF], with Storyboards
ms.assetid: 1020e44e-e21e-49a8-be53-53cbc1910e83
ms.openlocfilehash: a6cc8774c14d4b393b0d04822216c894e486ba66
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556699"
---
# <a name="how-to-animate-a-3-d-rotation-using-storyboards"></a>Como animar uma rotação 3D usando storyboards
O exemplo a seguir mostra como fazer com que um objeto 3D gire enquanto ele "vibra" pela animação de <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> e <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> propriedades de uma <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> objeto. Isso <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> objeto Especifica a transformação de rotação do objeto 3D e suas propriedades de animação assim cria o efeito de rotação desejado. Dentro do Storyboard, <xref:System.Windows.Media.Animation.DoubleAnimation> é usado para animar a <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> propriedade ao <xref:System.Windows.Media.Animation.Vector3DAnimation> é usado para animar a <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> propriedade.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[Animation3DGallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
## <a name="see-also"></a>Consulte também  
 [Animar uma rotação 3D usando Rotation3DAnimation](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)  
 [Animar uma rotação 3D usando quadros principais (Rotation3DAnimationUsingKeyFrames)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-key-frames.md)  
 [Visão geral de elementos gráficos 3D](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [Visão geral de storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
