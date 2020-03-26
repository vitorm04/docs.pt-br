---
title: 'Como: Animar uma rotação 3D usando quadros-chave (QuaternionAnimationUsingKeyFrames)'
ms.date: 03/30/2017
helpviewer_keywords:
- 3D translations [WPF], animating [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
- key frames [WPF], QuaternionAnimationUsingKeyFrames
- animation [WPF], 3D translations [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
ms.assetid: 09e5707b-7523-4a08-9aa7-bb13cbedccdf
ms.openlocfilehash: 5273183aaa49a743cc401dec0b4b16bae09e3129
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112291"
---
# <a name="how-to-animate-a-3d-rotation-using-key-frames-quaternionanimationusingkeyframes"></a>Como: Animar uma rotação 3D usando quadros-chave (QuaternionAnimationUsingKeyFrames)
No exemplo a <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> seguir, é usado para fazer um objeto 3D girar. Esta animação usa os seguintes quadros-chave:  
  
1. <xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame>é usado para criar uma interpolação suave e linear entre valores.  
  
2. <xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame>é usado para criar "saltos" repentinos entre valores (sem interpolação).  
  
3. <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame>é usado para criar uma transição <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> variável entre valores dependendo da propriedade. No exemplo abaixo, esta parte da animação começa lenta, mas no final do segmento de tempo, acelera exponencialmente.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationUsingKeyFramesExample.xaml#quaternionanimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>Confira também

- [Animar uma rotação 3D usando storyboards](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [Animar uma rotação 3D usando rotation3DAnimation](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [Animar uma rotação 3D usando quaternions](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [Animar uma rotação 3D usando quadros-chave (Rotation3DAnimationUsingKeyFrames)](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [Visão geral de gráficos 3D](3-d-graphics-overview.md)
- [Visão geral das animações de quadro-chave](key-frame-animations-overview.md)
