---
title: Como criar um giro do elemento in-loco
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: a1b515822391de08ec8ed8ff0ff1f0086874dc02
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112070"
---
# <a name="how-to-make-an-element-spin-in-place"></a>Como criar um giro do elemento in-loco
Este exemplo mostra como fazer um <xref:System.Windows.Media.RotateTransform> elemento <xref:System.Windows.Media.Animation.DoubleAnimation>girar usando a e a .  
  
 O exemplo a <xref:System.Windows.Media.RotateTransform> seguir <xref:System.Windows.UIElement.RenderTransform%2A> aplica-se à propriedade do elemento. O exemplo <xref:System.Windows.Media.Animation.DoubleAnimation> usa um <xref:System.Windows.Media.RotateTransform.Angle%2A> para <xref:System.Windows.Media.RotateTransform>animar o do . Para fazer o elemento girar no <xref:System.Windows.UIElement.RenderTransformOrigin%2A> lugar, o exemplo define a propriedade do elemento ao ponto (0,5, 0,5).  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[transformanimations_snip#11](~/samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 Para a amostra completa, que inclui mais exemplos de transformação, consulte [2D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).  
  
## <a name="see-also"></a>Confira também

- [Visão geral da animação](animation-overview.md)
- [Visão geral de transformações](transforms-overview.md)
