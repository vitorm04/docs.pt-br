---
title: 'Como: Animar uma rotação 3D usando quadros principais (QuaternionAnimationUsingKeyFrames)'
ms.date: 03/30/2017
helpviewer_keywords:
- 3-D translations [WPF], animating [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
- key frames [WPF], QuaternionAnimationUsingKeyFrames
- animation [WPF], 3-D translations [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
ms.assetid: 09e5707b-7523-4a08-9aa7-bb13cbedccdf
ms.openlocfilehash: 87176df26405a69cb2c3d63620def0575b750b52
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59338014"
---
# <a name="how-to-animate-a-3-d-rotation-using-key-frames-quaternionanimationusingkeyframes"></a>Como: Animar uma rotação 3D usando quadros principais (QuaternionAnimationUsingKeyFrames)
No exemplo a seguir, <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> é usado para fazer com que um objeto 3D girar. Essa animação usa quadros-chave a seguir:  
  
1. <xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> é usado para criar uma interpolação linear suave entre valores.  
  
2. <xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> é usado para criar "saltos" repentinos entre valores (sem interpolação).  
  
3. <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> é usado para criar uma transição variável entre valores de acordo o <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> propriedade. No exemplo a seguir, essa parte da animação começa lentamente, mas na direção do final do segmento de tempo, acelera exponencialmente.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationUsingKeyFramesExample.xaml#quaternionanimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>Consulte também

- [Animar uma rotação 3D usando storyboards](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [Animar uma rotação 3D usando Rotation3DAnimation](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [Animar uma rotação 3D usando Quaternions](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [Animar uma rotação 3D usando quadros principais (Rotation3DAnimationUsingKeyFrames)](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [Visão geral de elementos gráficos 3D](3-d-graphics-overview.md)
- [Visão geral das animações de quadro-chave](key-frame-animations-overview.md)
