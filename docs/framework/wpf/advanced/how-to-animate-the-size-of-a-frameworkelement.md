---
title: Como animar o tamanho de um FrameworkElement
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], FrameworkElement size
- FrameworkElement [WPF], animating size of
ms.assetid: d4cd5a13-c20d-4a6f-a2ba-14f2c9ce4cef
ms.openlocfilehash: 148e3d592e129984bd2f7ac062340c5169e48d30
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-animate-the-size-of-a-frameworkelement"></a>Como animar o tamanho de um FrameworkElement
Para animar o tamanho de um <xref:System.Windows.FrameworkElement>, é possível animar ou seu <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> propriedades ou use uma imagem <xref:System.Windows.Media.ScaleTransform>.  
  
 No exemplo a seguir anima o tamanho de dois botões usando estas duas abordagens. Um botão é redimensionado pela animação seu <xref:System.Windows.FrameworkElement.Width%2A> propriedade e outro é redimensionado pela animação um <xref:System.Windows.Media.ScaleTransform> aplicadas ao seu <xref:System.Windows.UIElement.RenderTransform%2A> propriedade. Cada botão contém algum texto. Inicialmente, o texto parece o mesmo em ambos os botões, mas como os botões são redimensionados, o texto no segundo botão fica distorcido.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[transformanimations_snip#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/AnimatingSizeExample.xaml#1)]  
  
 Quando você transforma um elemento, o elemento inteiro e seu conteúdo serão transformados. Quando você altera diretamente o tamanho de um elemento, como no caso do primeiro botão, o conteúdo do elemento não será redimensionado, a menos que seu tamanho e posição dependam do tamanho de seu elemento pai.  
  
 O tamanho de um elemento de animação, aplicando uma transformação animada a sua <xref:System.Windows.UIElement.RenderTransform%2A> propriedade fornece melhor desempenho do que a animação seu <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> diretamente, porque o <xref:System.Windows.UIElement.RenderTransform%2A> propriedade não aciona uma passagem de layout.  
  
 Para obter mais informações sobre animação de propriedades, consulte [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Para obter mais informações sobre transformações, consulte a [Visão geral das transformações](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).
