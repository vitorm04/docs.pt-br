---
title: 'Como: Animar uma rotação 3D usando quadros-chave'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3-D translations [WPF], with key frames (Rotation3DAnimation)
- key frames [WPF], Rotation3DAnimation
- 3-D translations [WPF], animating [WPF], with key frames (Rotation3DAnimation)
ms.assetid: 6f671b95-7f30-4836-9a4f-aeb7dc30121f
ms.openlocfilehash: e72ec94f830f0f5001a77e7492aa1326a47b309d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61762144"
---
# <a name="how-to-animate-a-3-d-rotation-using-key-frames"></a>Como: Animar uma rotação 3D usando quadros-chave
No exemplo a seguir, <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> é usado para fazer com que um objeto 3D rotacionar enquanto seu eixo de rotação anima, resultando em uma "tremida". Essa animação usa quadros-chave a seguir:  
  
1. <xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> é usado para criar uma interpolação linear suave entre valores.  
  
2. <xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> é usado para criar "saltos" repentinos entre valores (sem interpolação).  
  
3. <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> é usado para criar uma transição variável entre valores de acordo o <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> propriedade. No exemplo a seguir, essa parte da animação começa lentamente, mas na direção do final do segmento de tempo, acelera exponencialmente.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[Animation3DGallery_snip#Rotation3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotation3DAnimationUsingKeyFramesExample.xaml#rotation3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de elementos gráficos 3D](3-d-graphics-overview.md)
- [Visão geral das animações de quadro-chave](key-frame-animations-overview.md)
- [Animar uma rotação 3D usando storyboards](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [Animar uma rotação 3D usando Rotation3DAnimation](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [Animar uma rotação 3D usando Quaternions](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [Animar uma rotação 3D usando quadros principais (QuaternionAnimationUsingKeyFrames)](animate-a-3-d-rotation-quaternionanimationusingkeyframes.md)
