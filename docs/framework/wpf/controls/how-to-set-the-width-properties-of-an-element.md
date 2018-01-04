---
title: Como definir as propriedades de largura de um elemento
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- width properties [WPF]
- Panel control [WPF], width properties of elements
ms.assetid: 6ee04a9d-63f0-4f5b-a406-0a8cd4c35729
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b27eb8f12e10f98d585f8f9bc445dba0118988fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-width-properties-of-an-element"></a>Como definir as propriedades de largura de um elemento
## <a name="example"></a>Exemplo  
 Este exemplo mostra visualmente as diferenças no comportamento de renderização entre as quatro propriedades relacionadas à largura no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 O <xref:System.Windows.FrameworkElement> classe expõe quatro propriedades que descrevem as características de largura de um elemento. Essas quatro propriedades podem conflitar e quando isso acontece, o valor que tem precedência é determinado como segue: o <xref:System.Windows.FrameworkElement.MinWidth%2A> valor tem precedência sobre o <xref:System.Windows.FrameworkElement.MaxWidth%2A> valor, que por sua vez, tem precedência sobre o <xref:System.Windows.FrameworkElement.Width%2A> valor. Uma propriedade quarta, <xref:System.Windows.FrameworkElement.ActualWidth%2A>, é somente leitura e relata a largura real como determinado pelas interações com o processo de layout.  
  
 O seguinte [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemplos desenham um <xref:System.Windows.Shapes.Rectangle> elemento (`rect1`) como um filho de <xref:System.Windows.Controls.Canvas>. Você pode alterar as propriedades de largura de uma <xref:System.Windows.Shapes.Rectangle> usando uma série de <xref:System.Windows.Controls.ListBox> elementos que representam os valores de propriedade de <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>, e <xref:System.Windows.FrameworkElement.Width%2A>. Dessa forma, a precedência de cada propriedade é exibida visualmente.  
  
 [!code-xaml[WidthMinWidthMaxWidth#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#1)]  
[!code-xaml[WidthMinWidthMaxWidth#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#2)]  
  
 Os exemplos a seguir por trás do código manipulam os eventos que o <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> gera eventos. Cada método personalizado recebe entrada do <xref:System.Windows.Controls.ListBox>, analisa o valor como um <xref:System.Double>e aplica o valor à propriedade de largura especificada. Os valores de largura também são convertidos em uma cadeia de caracteres e gravados em várias <xref:System.Windows.Controls.TextBlock> elementos (a definição desses elementos não é mostrada no XAML selecionado).  
  
 [!code-csharp[WidthMinWidthMaxWidth#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml.cs#3)]
 [!code-vb[WidthMinWidthMaxWidth#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WidthMinWidthMaxWidth/VisualBasic/Window1.xaml.vb#3)]  
  
 Para ver o exemplo completo, confira [Exemplo de comparação de propriedades de largura](http://go.microsoft.com/fwlink/?LinkID=160050).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.FrameworkElement.ActualWidth%2A>  
 <xref:System.Windows.FrameworkElement.MaxWidth%2A>  
 <xref:System.Windows.FrameworkElement.MinWidth%2A>  
 <xref:System.Windows.FrameworkElement.Width%2A>  
 [Visão geral de painéis](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Definir as propriedades de altura de um elemento](../../../../docs/framework/wpf/controls/how-to-set-the-height-properties-of-an-element.md)  
 [Exemplo de comparação de propriedades de largura](http://go.microsoft.com/fwlink/?LinkID=160050)
