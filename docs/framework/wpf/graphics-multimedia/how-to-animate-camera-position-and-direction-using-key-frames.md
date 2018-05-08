---
title: Como animar a posição e a direção da câmera usando quadros-chave
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], camera direction with key frames
- key frames [WPF], animating camera direction
- animation [WPF], camera position with key frames
- camera position [WPF], animating with key frames
- key frames [WPF], animating camera position
- camera direction [WPF], animating with key frames
ms.assetid: 5753024e-0057-454d-947f-43ea686879c7
ms.openlocfilehash: 5be14513755c3b5c80c13cbc5cae889cc4663cec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-animate-camera-position-and-direction-using-key-frames"></a>Como animar a posição e a direção da câmera usando quadros-chave
No exemplo a seguir, <xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames> é usado para animar a posição de um <xref:System.Windows.Media.Media3D.PerspectiveCamera> em uma cena 3D. Além disso, <xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames> é usado para animar a direção da câmera está apontando na cena 3D. Essas animações usam vários quadros-chave que cria uma série de efeitos de animação:  
  
1.  <xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame> e <xref:System.Windows.Media.Animation.LinearVector3DKeyFrame> são usados para criar uma interpolação linear suave entre valores.  
  
2.  <xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame> e <xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame> são usados para criar "saltos" repentinos entre valores (sem interpolação).  
  
3.  <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame> e <xref:System.Windows.Media.Animation.SplineVector3DKeyFrame> são usados para criar uma transição de variável entre valores dependendo do <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A> propriedade. No exemplo a seguir, a animação começa lentamente mas até o fim do segmento de tempo, acelera exponencialmente.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationUsingKeyFramesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationUsingKeyFramesExample.xaml#pointvector3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>Consulte também  
 [Animar posição e direção da câmera em uma cena 3D](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-camera-position-and-direction-in-a-3d-scene.md)  
 [Visão geral de elementos gráficos 3D](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
