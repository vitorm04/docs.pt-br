---
title: Como definir as propriedades de largura de um elemento
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- width properties [WPF]
- Panel control [WPF], width properties of elements
ms.assetid: 6ee04a9d-63f0-4f5b-a406-0a8cd4c35729
ms.openlocfilehash: 682929625612114d042e4619d8388617988b3c48
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124267"
---
# <a name="how-to-set-the-width-properties-of-an-element"></a>Como definir as propriedades de largura de um elemento
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
 Este exemplo mostra visualmente as diferenças no comportamento de renderização entre as quatro propriedades relacionadas à largura no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 A classe <xref:System.Windows.FrameworkElement> expõe quatro propriedades que descrevem as características de largura de um elemento. Essas quatro propriedades podem entrar em conflito e, quando fazem isso, o valor que tem precedência é determinado da seguinte maneira: o valor <xref:System.Windows.FrameworkElement.MinWidth%2A> tem precedência sobre o valor <xref:System.Windows.FrameworkElement.MaxWidth%2A>, que, por sua vez, tem precedência sobre o valor <xref:System.Windows.FrameworkElement.Width%2A>. Uma quarta Propriedade, <xref:System.Windows.FrameworkElement.ActualWidth%2A>, é somente leitura e relata a largura real, conforme determinado pelas interações com o processo de layout.  
  
 Os exemplos de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a seguir desenham um elemento <xref:System.Windows.Shapes.Rectangle> (`rect1`) como um filho de <xref:System.Windows.Controls.Canvas>. Você pode alterar as propriedades de largura de um <xref:System.Windows.Shapes.Rectangle> usando uma série de elementos <xref:System.Windows.Controls.ListBox> que representam os valores de propriedade de <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>e <xref:System.Windows.FrameworkElement.Width%2A>. Desta forma, a prioridade de cada propriedade é exibida visualmente.  
  
 [!code-xaml[WidthMinWidthMaxWidth#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#1)]  
[!code-xaml[WidthMinWidthMaxWidth#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#2)]  
  
 Os exemplos de code-behind a seguir tratam dos eventos que o evento de <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> gera. Cada método personalizado usa a entrada do <xref:System.Windows.Controls.ListBox>, analisa o valor como um <xref:System.Double>e aplica o valor à propriedade relacionada à largura especificada. Os valores de largura também são convertidos em uma cadeia de caracteres e gravados em vários elementos de <xref:System.Windows.Controls.TextBlock> (a definição desses elementos não é mostrada no XAML selecionado).  
  
 [!code-csharp[WidthMinWidthMaxWidth#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml.cs#3)]
 [!code-vb[WidthMinWidthMaxWidth#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WidthMinWidthMaxWidth/VisualBasic/Window1.xaml.vb#3)]  
  
 Para ver o exemplo completo, confira [Exemplo de comparação de propriedades de largura](https://github.com/Microsoft/WPF-Samples/tree/master/Elements/WidthProperties).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.ActualWidth%2A>
- <xref:System.Windows.FrameworkElement.MaxWidth%2A>
- <xref:System.Windows.FrameworkElement.MinWidth%2A>
- <xref:System.Windows.FrameworkElement.Width%2A>
- [Visão geral de painéis](panels-overview.md)
- [Definir as propriedades de altura de um elemento](how-to-set-the-height-properties-of-an-element.md)
- [Exemplo de comparação de propriedades de largura](https://github.com/Microsoft/WPF-Samples/tree/master/Elements/WidthProperties)
