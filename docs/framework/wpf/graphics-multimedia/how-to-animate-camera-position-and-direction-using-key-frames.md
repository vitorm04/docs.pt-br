---
title: 'Como: Animar a posição e a direção da câmera usando quadros principais'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], camera direction with key frames
- key frames [WPF], animating camera direction
- animation [WPF], camera position with key frames
- camera position [WPF], animating with key frames
- key frames [WPF], animating camera position
- camera direction [WPF], animating with key frames
ms.assetid: 5753024e-0057-454d-947f-43ea686879c7
ms.openlocfilehash: 44464cc314d649516998338e36c1b523101ac4e2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651331"
---
# <a name="how-to-animate-camera-position-and-direction-using-key-frames"></a>Como: Animar a posição e a direção da câmera usando quadros principais
No exemplo a seguir <xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames> é usado para animar a posição de um <xref:System.Windows.Media.Media3D.PerspectiveCamera> em uma cena 3D. Além disso, <xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames> é usado para animar a direção da câmera está apontando na cena 3D. Ambas essas animações usam vários quadros-chave que cria uma série de efeitos de animação:  
  
1. <xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame> e <xref:System.Windows.Media.Animation.LinearVector3DKeyFrame> são usados para criar uma interpolação linear suave entre valores.  
  
2. <xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame> e <xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame> são usados para criar "saltos" repentinos entre valores (sem interpolação).  
  
3. <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame> e <xref:System.Windows.Media.Animation.SplineVector3DKeyFrame> são usados para criar uma transição variável entre valores de acordo o <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A> propriedade. No exemplo a seguir, a animação começa lentamente, mas na direção do final do segmento de tempo, acelera exponencialmente.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationUsingKeyFramesExample.xaml#pointvector3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>Consulte também

- [Animar posição e direção da câmera em uma cena 3D](how-to-animate-camera-position-and-direction-in-a-3d-scene.md)
- [Visão geral de elementos gráficos 3D](3-d-graphics-overview.md)
