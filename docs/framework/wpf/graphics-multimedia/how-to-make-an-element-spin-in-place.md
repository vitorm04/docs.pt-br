---
title: Como criar um giro do elemento in-loco
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: 2e72389a11e48629c2763fcbd9f7b1945ffff5dd
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452786"
---
# <a name="how-to-make-an-element-spin-in-place"></a>Como criar um giro do elemento in-loco
Este exemplo mostra como fazer um elemento girar usando um <xref:System.Windows.Media.RotateTransform> e um <xref:System.Windows.Media.Animation.DoubleAnimation>.  
  
 O exemplo a seguir aplica o <xref:System.Windows.Media.RotateTransform> à propriedade <xref:System.Windows.UIElement.RenderTransform%2A> do elemento. O exemplo usa um <xref:System.Windows.Media.Animation.DoubleAnimation> para animar a <xref:System.Windows.Media.RotateTransform.Angle%2A> do <xref:System.Windows.Media.RotateTransform>. Para fazer com que o elemento gire no lugar, o exemplo define a propriedade <xref:System.Windows.UIElement.RenderTransformOrigin%2A> do elemento como o ponto (0,5, 0,5).  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[transformanimations_snip#11](~/samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 Para obter o exemplo completo, que inclui mais exemplos de transformação, consulte [amostra de transformações 2D](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).  
  
## <a name="see-also"></a>Confira também

- [Visão geral da animação](animation-overview.md)
- [Visão geral de transformações](transforms-overview.md)
