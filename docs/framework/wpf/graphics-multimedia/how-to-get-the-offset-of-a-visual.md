---
title: 'Como: Obter o deslocamento de um visual'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting offset values from visual objects [WPF]
- offset values [WPF], retrieving from visual objects [WPF]
- visual objects [WPF], retrieving offset values from
- retrieving offset values from visual objects [WPF]
ms.assetid: 889a1dd6-1b11-445a-b351-fbb04c53ee34
ms.openlocfilehash: ad45dee5b72594f30b141e3affbb26706af645aa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645386"
---
# <a name="how-to-get-the-offset-of-a-visual"></a>Como: Obter o deslocamento de um visual
Esses exemplos mostram como recuperar o valor de deslocamento de um objeto visual que é relativo a seu pai ou a qualquer ancestral ou descendente.  
  
## <a name="example"></a>Exemplo  
 O exemplo de marcação a seguir mostra uma <xref:System.Windows.Controls.TextBlock> que é definida com <xref:System.Windows.FrameworkElement.Margin%2A> valor 4.  
  
 [!code-xaml[VisualSnippets#VisualSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet1)]  
  
 O exemplo de código a seguir mostra como usar o <xref:System.Windows.Media.VisualTreeHelper.GetOffset%2A> método para recuperar o deslocamento do <xref:System.Windows.Controls.TextBlock>. Os valores de deslocamento estão contidos dentro do retornado <xref:System.Windows.Vector> valor.  
  
 [!code-csharp[VisualSnippets#VisualSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet2)]
 [!code-vb[VisualSnippets#VisualSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet2)]  
  
 O deslocamento leva em consideração o <xref:System.Windows.FrameworkElement.Margin%2A> valor. Nesse caso, <xref:System.Windows.Vector.X%2A> for 4, e <xref:System.Windows.Vector.Y%2A> é 4.  
  
 O valor de deslocamento retornado é relativo ao pai do <xref:System.Windows.Media.Visual>. Se você quiser retornar um valor de deslocamento que não é relativo ao pai de um <xref:System.Windows.Media.Visual>, use o <xref:System.Windows.Media.Visual.TransformToAncestor%2A> método.  
  
## <a name="getting-the-offset-relative-to-an-ancestor"></a>Obtendo o deslocamento relativo a um ancestral  
 O exemplo de marcação a seguir mostra uma <xref:System.Windows.Controls.TextBlock> que está aninhado em dois <xref:System.Windows.Controls.StackPanel> objetos.  
  
 [!code-xaml[VisualSnippets#VisualSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window2.xaml#visualsnippet7)]  
  
 A ilustração a seguir mostra os resultados da marcação.  
  
 ![Valores de deslocamento de objetos](../../../../docs/framework/wpf/graphics-multimedia/media/visualoffset-01.png "VisualOffset_01")  
TextBlock aninhados em dois StackPanels  
  
 O exemplo de código a seguir mostra como usar o <xref:System.Windows.Media.Visual.TransformToAncestor%2A> método para recuperar o deslocamento do <xref:System.Windows.Controls.TextBlock> em relação ao que o contém <xref:System.Windows.Window>. Os valores de deslocamento estão contidos dentro do retornado <xref:System.Windows.Media.GeneralTransform> valor.  
  
 [!code-csharp[VisualSnippets#VisualSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet5)]
 [!code-vb[VisualSnippets#VisualSnippet5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet5)]  
  
 O deslocamento leva em conta as <xref:System.Windows.FrameworkElement.Margin%2A> valores para todos os objetos de recipiente <xref:System.Windows.Window>. Nesse caso, <xref:System.Windows.Vector.X%2A> é 28 (16 + 8 + 4), e <xref:System.Windows.Vector.Y%2A> é 28.  
  
 O valor de deslocamento retornado é relativo ao ancestral do <xref:System.Windows.Media.Visual>. Se você quiser retornar um valor de deslocamento é relativo ao ancestral de um <xref:System.Windows.Media.Visual>, use o <xref:System.Windows.Media.Visual.TransformToDescendant%2A> método.  
  
## <a name="getting-the-offset-relative-to-a-descendant"></a>Obtendo o deslocamento relativo a um descendente  
 O exemplo de marcação a seguir mostra uma <xref:System.Windows.Controls.TextBlock> que está contido em um <xref:System.Windows.Controls.StackPanel> objeto.  
  
 [!code-xaml[VisualSnippets#VisualSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet4)]  
  
 O exemplo de código a seguir mostra como usar o <xref:System.Windows.Media.Visual.TransformToDescendant%2A> método para recuperar o deslocamento do <xref:System.Windows.Controls.StackPanel> em relação ao seu filho <xref:System.Windows.Controls.TextBlock>. Os valores de deslocamento estão contidos dentro do retornado <xref:System.Windows.Media.GeneralTransform> valor.  
  
 [!code-csharp[VisualSnippets#VisualSnippet9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet9)]
 [!code-vb[VisualSnippets#VisualSnippet9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet9)]  
  
 O deslocamento leva em consideração o <xref:System.Windows.FrameworkElement.Margin%2A> valores para todos os objetos. Nesse caso, <xref:System.Windows.Vector.X%2A> é -4, e <xref:System.Windows.Vector.Y%2A> é -4. Os valores de deslocamento são valores negativos, visto que o objeto pai é deslocado negativamente em relação ao seu objeto filho.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.Media.VisualTreeHelper>
- [Visão geral de renderização de gráficos do WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
