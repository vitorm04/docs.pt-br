---
title: 'Como: Animar uma rotação 3D usando storyboards'
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF]
- 3D translations [WPF], animating [WPF], with Storyboards
- animation [WPF], 3D translations [WPF], with Storyboards
ms.assetid: 1020e44e-e21e-49a8-be53-53cbc1910e83
ms.openlocfilehash: 088f1a33cfc73a706ffed55ffff6494adaf8fca4
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112201"
---
# <a name="how-to-animate-a-3d-rotation-using-storyboards"></a>Como: Animar uma rotação 3D usando storyboards
O exemplo a seguir mostra como fazer um objeto 3D girar <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> enquanto <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> ele "oscila" animando as propriedades de um objeto. Este <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> objeto especifica a transformação de rotação do objeto 3D e, portanto, animar suas propriedades cria o efeito de rotação do desejo. Dentro do <xref:System.Windows.Media.Animation.DoubleAnimation> Storyboard, é usado <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> para <xref:System.Windows.Media.Animation.Vector3DAnimation> animar a propriedade <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> enquanto é usado para animar a propriedade.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[Animation3DGallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
## <a name="see-also"></a>Confira também

- [Animar uma rotação 3D usando rotation3DAnimation](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [Animar uma rotação 3D usando quadros-chave (Rotation3DAnimationUsingKeyFrames)](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [Visão geral de gráficos 3D](3-d-graphics-overview.md)
- [Visão geral de storyboards](storyboards-overview.md)
