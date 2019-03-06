---
title: 'Como: Animar o tamanho de um FrameworkElement'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], FrameworkElement size
- FrameworkElement [WPF], animating size of
ms.assetid: d4cd5a13-c20d-4a6f-a2ba-14f2c9ce4cef
ms.openlocfilehash: d1995deec5ab2c9bf405911af43b4d242d599119
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360986"
---
# <a name="how-to-animate-the-size-of-a-frameworkelement"></a>Como: Animar o tamanho de um FrameworkElement
Para animar o tamanho de um <xref:System.Windows.FrameworkElement>, você pode animar sua <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> propriedades ou use um animada <xref:System.Windows.Media.ScaleTransform>.  
  
 No exemplo a seguir anima o tamanho de dois botões usando estas duas abordagens. Um botão é redimensionado animando sua <xref:System.Windows.FrameworkElement.Width%2A> propriedade e outro é redimensionado animando um <xref:System.Windows.Media.ScaleTransform> aplicados a seus <xref:System.Windows.UIElement.RenderTransform%2A> propriedade. Cada botão contém algum texto. Inicialmente, o texto parece o mesmo em ambos os botões, mas como os botões são redimensionados, o texto no segundo botão fica distorcido.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[transformanimations_snip#1](~/samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/AnimatingSizeExample.xaml#1)]  
  
 Quando você transforma um elemento, o elemento inteiro e seu conteúdo serão transformados. Quando você altera diretamente o tamanho de um elemento, como no caso do primeiro botão, o conteúdo do elemento não será redimensionado, a menos que seu tamanho e posição dependam do tamanho de seu elemento pai.  
  
 Animando o tamanho de um elemento aplicando uma transformação animada à sua <xref:System.Windows.UIElement.RenderTransform%2A> propriedade fornece um desempenho melhor do que animar seu <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> diretamente, porque o <xref:System.Windows.UIElement.RenderTransform%2A> propriedade não dispara uma passagem de layout.  
  
 Para obter mais informações sobre animação de propriedades, consulte [Visão geral da animação](../graphics-multimedia/animation-overview.md). Para obter mais informações sobre transformações, consulte a [Visão geral das transformações](../graphics-multimedia/transforms-overview.md).
