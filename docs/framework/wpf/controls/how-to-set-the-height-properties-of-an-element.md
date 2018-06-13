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
ms.openlocfilehash: 467cd57c728be015fb9eb9b974ca6e81e4fd7754
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33554834"
---
# <a name="how-to-set-the-height-properties-of-an-element"></a>Como definir as propriedades de altura de um elemento
## <a name="example"></a>Exemplo  
 Este exemplo mostra visualmente as diferenças no comportamento de renderização entre as quatro propriedades relacionadas à altura em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 O <xref:System.Windows.FrameworkElement> classe expõe quatro propriedades que descrevem as características de altura de um elemento. Essas quatro propriedades podem conflitar e quando isso acontece, o valor que tem precedência é determinado como segue: o <xref:System.Windows.FrameworkElement.MinHeight%2A> valor tem precedência sobre o <xref:System.Windows.FrameworkElement.MaxHeight%2A> valor, que por sua vez, tem precedência sobre o <xref:System.Windows.FrameworkElement.Height%2A> valor. Uma propriedade quarta, <xref:System.Windows.FrameworkElement.ActualHeight%2A>, é somente leitura e relata a altura real como determinado pelas interações com o processo de layout.  
  
 O seguinte [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemplos desenham um <xref:System.Windows.Shapes.Rectangle> elemento (`rect1`) como um filho de <xref:System.Windows.Controls.Canvas>. Você pode alterar as propriedades de altura de um <xref:System.Windows.Shapes.Rectangle> usando uma série de <xref:System.Windows.Controls.ListBox> elementos que representam os valores de propriedade de <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, e <xref:System.Windows.FrameworkElement.Height%2A>. Dessa forma, a precedência de cada propriedade é exibida visualmente.  
  
 [!code-xaml[HeightMinHeightMaxHeight#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#1)]  
[!code-xaml[HeightMinHeightMaxHeight#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#2)]  
  
 Os exemplos a seguir por trás do código manipulam os eventos que o <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> gera eventos. Cada manipulador recebe entrada do <xref:System.Windows.Controls.ListBox>, analisa o valor como um <xref:System.Double>e aplica o valor à propriedade de altura especificada. Os valores de altura também são convertidos em uma cadeia de caracteres e gravados em várias <xref:System.Windows.Controls.TextBlock> elementos (a definição desses elementos não é mostrada no XAML selecionado).  
  
 [!code-csharp[HeightMinHeightMaxHeight#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml.cs#3)]
 [!code-vb[HeightMinHeightMaxHeight#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HeightMinHeightMaxHeight/VisualBasic/Window1.xaml.vb#3)]  
  
 Para a amostra completa, consulte [Amostra de propriedades de altura](http://go.microsoft.com/fwlink/?LinkID=159993).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.FrameworkElement.ActualHeight%2A>  
 <xref:System.Windows.FrameworkElement.MaxHeight%2A>  
 <xref:System.Windows.FrameworkElement.MinHeight%2A>  
 <xref:System.Windows.FrameworkElement.Height%2A>  
 [Definir as propriedades de largura de um elemento](../../../../docs/framework/wpf/controls/how-to-set-the-width-properties-of-an-element.md)  
 [Visão geral de painéis](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Exemplo de propriedades de altura](http://go.microsoft.com/fwlink/?LinkID=159993)
