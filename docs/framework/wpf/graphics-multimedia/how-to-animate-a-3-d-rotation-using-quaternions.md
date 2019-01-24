---
title: 'Como: Animar uma rotação 3D usando Quaternions'
ms.date: 03/30/2017
helpviewer_keywords:
- quaternions [WPF]
- animation [WPF], 3-D translations [WPF], with quaternions
- 3-D translations [WPF], animating [WPF], with quaternions
ms.assetid: adca9cb1-066b-4de8-abbb-6b4007579ee7
ms.openlocfilehash: df51db324bffc038bc585b6d977a82d54feefb3b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550923"
---
# <a name="how-to-animate-a-3-d-rotation-using-quaternions"></a>Como: Animar uma rotação 3D usando Quaternions
Este exemplo mostra como animar uma rotação de um objeto 3D usando quaternions.  
  
 O código a seguir mostra uma <xref:System.Windows.Media.Media3D.QuaternionRotation3D> usado como o valor para o <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> propriedade de um <xref:System.Windows.Media.Media3D.RotateTransform3D>.  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline1)]  
  
 Isso <xref:System.Windows.Media.Media3D.QuaternionRotation3D> é animado com uma <xref:System.Windows.Media.Animation.QuaternionAnimation> dentro de um <xref:System.Windows.Media.Animation.Storyboard> usando o código a seguir.  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline2)]  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra o exemplo completo.  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexamplewholepage)]  
  
## <a name="see-also"></a>Consulte também
- [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [Criar uma cena 3D](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)
- [Visão geral de elementos gráficos 3D](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
- [Visão geral de transformações](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
- [Animar uma rotação 3D usando storyboards](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-storyboards.md)
- [Animar uma rotação 3D usando Rotation3DAnimation](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
