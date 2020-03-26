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
ms.openlocfilehash: 28471f9b42140a6c75b043d33939503528b63194
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112161"
---
# <a name="how-to-animate-camera-position-and-direction-using-key-frames"></a>Como animar a posição e a direção da câmera usando quadros-chave
No exemplo a <xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames> seguir, é usado para <xref:System.Windows.Media.Media3D.PerspectiveCamera> animar a posição de a em uma cena 3D. Além disso, <xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames> é usado para animar a direção que a câmera está apontando na cena 3D. Ambas as animações usam vários quadros-chave que criam uma série de efeitos de animação:  
  
1. <xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame>e <xref:System.Windows.Media.Animation.LinearVector3DKeyFrame> são usados para criar uma interpolação suave e linear entre valores.  
  
2. <xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame>e <xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame> são usados para criar "saltos" repentinos entre valores (sem interpolação).  
  
3. <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame>e <xref:System.Windows.Media.Animation.SplineVector3DKeyFrame> são usados para criar uma <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A> transição variável entre valores dependendo da propriedade. No exemplo abaixo, a animação começa lenta, mas no final do segmento de tempo, acelera exponencialmente.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationUsingKeyFramesExample.xaml#pointvector3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>Confira também

- [Animar posição e direção da câmera em uma cena 3D](how-to-animate-camera-position-and-direction-in-a-3d-scene.md)
- [Visão geral de gráficos 3D](3-d-graphics-overview.md)
