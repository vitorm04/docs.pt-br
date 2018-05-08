---
title: Como criar um giro do elemento in-loco
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: a37952af621c79d231b45a247c92d3576a533580
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-make-an-element-spin-in-place"></a>Como criar um giro do elemento in-loco
Este exemplo mostra como fazer um elemento girar usando um <xref:System.Windows.Media.RotateTransform> e um <xref:System.Windows.Media.Animation.DoubleAnimation>.  
  
 O exemplo a seguir se aplica a <xref:System.Windows.Media.RotateTransform> para o <xref:System.Windows.UIElement.RenderTransform%2A> propriedade do elemento. O exemplo usa um <xref:System.Windows.Media.Animation.DoubleAnimation> para animar a <xref:System.Windows.Media.RotateTransform.Angle%2A> do <xref:System.Windows.Media.RotateTransform>. Para fazer com que o elemento girar em vigor, o exemplo define o <xref:System.Windows.UIElement.RenderTransformOrigin%2A> propriedade do elemento para o ponto (0,5, 0,5).  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[transformanimations_snip#11](../../../../samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 Para o exemplo completo, que inclui mais exemplos de transformação, consulte [exemplo de transformações 2D](http://go.microsoft.com/fwlink/?LinkID=158252).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Visão geral de transformações](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
