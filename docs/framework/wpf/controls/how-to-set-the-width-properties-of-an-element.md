---
title: 'Como: Definir as propriedades de largura de um elemento'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- width properties [WPF]
- Panel control [WPF], width properties of elements
ms.assetid: 6ee04a9d-63f0-4f5b-a406-0a8cd4c35729
ms.openlocfilehash: a5ed67ba20176398a863a1e9826b1eab71b182f2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59096869"
---
# <a name="how-to-set-the-width-properties-of-an-element"></a>Como: Definir as propriedades de largura de um elemento
## <a name="example"></a>Exemplo  
 Este exemplo mostra visualmente as diferenças no comportamento de renderização entre as quatro propriedades relacionadas à largura no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 O <xref:System.Windows.FrameworkElement> classe expõe quatro propriedades que descrevem as características de largura de um elemento. Essas quatro propriedades podem conflitar e quando isso acontece, o valor que tem precedência é determinado da seguinte maneira: o <xref:System.Windows.FrameworkElement.MinWidth%2A> valor tem precedência sobre a <xref:System.Windows.FrameworkElement.MaxWidth%2A> valor, que por sua vez, tem precedência sobre o <xref:System.Windows.FrameworkElement.Width%2A> valor. Uma quarta propriedade, <xref:System.Windows.FrameworkElement.ActualWidth%2A>, é somente leitura e relata a largura real conforme determinado pelas interações com o processo de layout.  
  
 O seguinte [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemplos de desenham uma <xref:System.Windows.Shapes.Rectangle> elemento (`rect1`) como um filho de <xref:System.Windows.Controls.Canvas>. Você pode alterar as propriedades de largura de um <xref:System.Windows.Shapes.Rectangle> por meio de uma série de <xref:System.Windows.Controls.ListBox> elementos que representam os valores de propriedade de <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>, e <xref:System.Windows.FrameworkElement.Width%2A>. Dessa forma, a precedência de cada propriedade é exibida visualmente.  
  
 [!code-xaml[WidthMinWidthMaxWidth#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#1)]  
[!code-xaml[WidthMinWidthMaxWidth#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#2)]  
  
 Os seguintes exemplos de code-behind manipulam os eventos que o <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> aciona eventos. Cada método personalizado recebe entrada do <xref:System.Windows.Controls.ListBox>, analisa o valor como um <xref:System.Double>e aplica o valor à propriedade relacionada à largura especificada. Os valores de largura também são convertidos em uma cadeia de caracteres e gravados em vários <xref:System.Windows.Controls.TextBlock> elementos (a definição desses elementos não é mostrada o XAML selecionado).  
  
 [!code-csharp[WidthMinWidthMaxWidth#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml.cs#3)]
 [!code-vb[WidthMinWidthMaxWidth#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WidthMinWidthMaxWidth/VisualBasic/Window1.xaml.vb#3)]  
  
 Para ver o exemplo completo, confira [Exemplo de comparação de propriedades de largura](https://go.microsoft.com/fwlink/?LinkID=160050).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.ActualWidth%2A>
- <xref:System.Windows.FrameworkElement.MaxWidth%2A>
- <xref:System.Windows.FrameworkElement.MinWidth%2A>
- <xref:System.Windows.FrameworkElement.Width%2A>
- [Visão geral de painéis](panels-overview.md)
- [Definir as propriedades de altura de um elemento](how-to-set-the-height-properties-of-an-element.md)
- [Exemplo de comparação de propriedades de largura](https://go.microsoft.com/fwlink/?LinkID=160050)
