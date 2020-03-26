---
title: 'Como: Animar uma rotação 3D usando quaternions'
ms.date: 03/30/2017
helpviewer_keywords:
- quaternions [WPF]
- animation [WPF], 3D translations [WPF], with quaternions
- 3D translations [WPF], animating [WPF], with quaternions
ms.assetid: adca9cb1-066b-4de8-abbb-6b4007579ee7
ms.openlocfilehash: 0d229b0a714cc53459943fae751ab4d4f787d7d8
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112239"
---
# <a name="how-to-animate-a-3d-rotation-using-quaternions"></a>Como: Animar uma rotação 3D usando quaternions
Este exemplo mostra como animar uma rotação de um objeto 3D usando quaternions.  
  
 O código abaixo <xref:System.Windows.Media.Media3D.QuaternionRotation3D> mostra um usado <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> como <xref:System.Windows.Media.Media3D.RotateTransform3D>o valor para a propriedade de um .  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline1)]  
  
 Este <xref:System.Windows.Media.Media3D.QuaternionRotation3D> é animado <xref:System.Windows.Media.Animation.QuaternionAnimation> com <xref:System.Windows.Media.Animation.Storyboard> um dentro de um usando o código abaixo.  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline2)]  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra toda a amostra.  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexamplewholepage)]  
  
## <a name="see-also"></a>Confira também

- [Visão geral da animação](animation-overview.md)
- [Criar uma cena 3D](how-to-create-a-3-d-scene.md)
- [Visão geral de gráficos 3D](3-d-graphics-overview.md)
- [Visão geral de transformações](transforms-overview.md)
- [Animar uma rotação 3D usando storyboards](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [Animar uma rotação 3D usando rotation3DAnimation](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
