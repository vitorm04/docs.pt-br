---
title: Como definir as propriedades de altura de um elemento
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- height properties [WPF]
- Panel control [WPF], height properties of elements
ms.assetid: 5ab9e781-dbb8-469a-a3c8-cf38ce312647
ms.openlocfilehash: 6500af3c637092820e538d79894d600d617953bf
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124280"
---
# <a name="how-to-set-the-height-properties-of-an-element"></a>Como definir as propriedades de altura de um elemento
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
 Este exemplo mostra visualmente as diferenças no comportamento de renderização entre as quatro propriedades relacionadas à altura em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 A classe <xref:System.Windows.FrameworkElement> expõe quatro propriedades que descrevem as características de altura de um elemento. Essas quatro propriedades podem entrar em conflito e, quando fazem isso, o valor que tem precedência é determinado da seguinte maneira: o valor <xref:System.Windows.FrameworkElement.MinHeight%2A> tem precedência sobre o valor <xref:System.Windows.FrameworkElement.MaxHeight%2A>, que, por sua vez, tem precedência sobre o valor <xref:System.Windows.FrameworkElement.Height%2A>. Uma quarta Propriedade, <xref:System.Windows.FrameworkElement.ActualHeight%2A>, é somente leitura e relata a altura real, conforme determinado pelas interações com o processo de layout.  
  
 Os exemplos de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a seguir desenham um elemento <xref:System.Windows.Shapes.Rectangle> (`rect1`) como um filho de <xref:System.Windows.Controls.Canvas>. Você pode alterar as propriedades de altura de um <xref:System.Windows.Shapes.Rectangle> usando uma série de elementos <xref:System.Windows.Controls.ListBox> que representam os valores de propriedade de <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>e <xref:System.Windows.FrameworkElement.Height%2A>. Desta forma, a prioridade de cada propriedade é exibida visualmente.  
  
 [!code-xaml[HeightMinHeightMaxHeight#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#1)]  
[!code-xaml[HeightMinHeightMaxHeight#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#2)]  
  
 Os exemplos de code-behind a seguir tratam dos eventos que o evento de <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> gera. Cada manipulador usa a entrada do <xref:System.Windows.Controls.ListBox>, analisa o valor como um <xref:System.Double>e aplica o valor à propriedade relacionada à altura especificada. Os valores de altura também são convertidos em uma cadeia de caracteres e gravados em vários elementos de <xref:System.Windows.Controls.TextBlock> (a definição desses elementos não é mostrada no XAML selecionado).  
  
 [!code-csharp[HeightMinHeightMaxHeight#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml.cs#3)]
 [!code-vb[HeightMinHeightMaxHeight#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HeightMinHeightMaxHeight/VisualBasic/Window1.xaml.vb#3)]  
  
 Para a amostra completa, consulte [Amostra de propriedades de altura](https://github.com/microsoft/WPF-Samples/tree/master/Elements/HeightProperties).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement.ActualHeight%2A>
- <xref:System.Windows.FrameworkElement.MaxHeight%2A>
- <xref:System.Windows.FrameworkElement.MinHeight%2A>
- <xref:System.Windows.FrameworkElement.Height%2A>
- [Definir as propriedades de largura de um elemento](how-to-set-the-width-properties-of-an-element.md)
- [Visão geral de painéis](panels-overview.md)
- [Exemplo de propriedades de altura](https://github.com/microsoft/WPF-Samples/tree/master/Elements/HeightProperties)
