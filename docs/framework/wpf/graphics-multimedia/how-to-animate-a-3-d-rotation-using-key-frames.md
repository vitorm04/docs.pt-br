---
title: 'Como: Animar uma rotação 3D usando quadros-chave'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3D translations [WPF], with key frames (Rotation3DAnimation)
- key frames [WPF], Rotation3DAnimation
- 3D translations [WPF], animating [WPF], with key frames (Rotation3DAnimation)
ms.assetid: 6f671b95-7f30-4836-9a4f-aeb7dc30121f
ms.openlocfilehash: 2b9059df079125c34c70237c0f600751020044c6
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112304"
---
# <a name="how-to-animate-a-3d-rotation-using-key-frames"></a>Como: Animar uma rotação 3D usando quadros-chave
No exemplo a <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> seguir, é usado para fazer um objeto 3D girar enquanto seu eixo de rotação anima resultando em uma "oscilação". Esta animação usa os seguintes quadros-chave:  
  
1. <xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame>é usado para criar uma interpolação suave e linear entre valores.  
  
2. <xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame>é usado para criar "saltos" repentinos entre valores (sem interpolação).  
  
3. <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame>é usado para criar uma transição <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> variável entre valores dependendo da propriedade. No exemplo abaixo, esta parte da animação começa lenta, mas no final do segmento de tempo, acelera exponencialmente.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[Animation3DGallery_snip#Rotation3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotation3DAnimationUsingKeyFramesExample.xaml#rotation3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>Confira também

- [Visão geral de gráficos 3D](3-d-graphics-overview.md)
- [Visão geral das animações de quadro-chave](key-frame-animations-overview.md)
- [Animar uma rotação 3D usando storyboards](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [Animar uma rotação 3D usando rotation3DAnimation](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [Animar uma rotação 3D usando quaternions](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [Animar uma rotação 3D usando quadros-chave (QuaternionAnimationUsingKeyFrames)](animate-a-3-d-rotation-quaternionanimationusingkeyframes.md)
