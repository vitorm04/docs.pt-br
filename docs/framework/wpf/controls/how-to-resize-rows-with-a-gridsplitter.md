---
title: 'Como: Redimensionar linhas com um GridSplitter'
ms.date: 03/30/2017
helpviewer_keywords:
- resizing grid rows [WPF]
- grid rows [WPF], resizing
- GridSplitter control [WPF], resizing grid rows
ms.assetid: 2413a9f2-1d81-46ed-95cb-95ec8233eea2
ms.openlocfilehash: b05bda6cd33d3cdd0dda6288f30821d290c60cfc
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370040"
---
# <a name="how-to-resize-rows-with-a-gridsplitter"></a>Como: Redimensionar linhas com um GridSplitter
Este exemplo mostra como usar um horizontal <xref:System.Windows.Controls.GridSplitter> redistribuir o espaço entre duas linhas em uma <xref:System.Windows.Controls.Grid> sem alterar as dimensões do <xref:System.Windows.Controls.Grid>.  
  
## <a name="example"></a>Exemplo  
 **Como criar um GridSplitter que sobrepõe a borda de uma linha**  
  
 Para especificar uma <xref:System.Windows.Controls.GridSplitter> que redimensiona linhas adjacentes em um <xref:System.Windows.Controls.Grid>, defina o <xref:System.Windows.Controls.Grid.Row%2A> propriedade anexada a uma das linhas que você deseja redimensionar. Se sua <xref:System.Windows.Controls.Grid> tiver mais de uma coluna, defina o <xref:System.Windows.Controls.Grid.ColumnSpan%2A> propriedade anexada para especificar o número de colunas. Em seguida, defina as <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> à <xref:System.Windows.VerticalAlignment.Top> ou <xref:System.Windows.VerticalAlignment.Bottom> (o alinhamento definido depende de quais duas linhas deseja redimensionar). Por fim, defina as <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> propriedade para <xref:System.Windows.HorizontalAlignment.Stretch>.  
  
 O exemplo a seguir mostra como definir um horizontal <xref:System.Windows.Controls.GridSplitter> que redimensiona linhas adjacentes.  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterRowOverlay](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterrowoverlay)]  
  
 Um <xref:System.Windows.Controls.GridSplitter> que não ocupa sua própria linha pode ser obscurecido por outros controles no <xref:System.Windows.Controls.Grid>. Para obter mais informações sobre como evitar esse problema, consulte [Verifique se um GridSplitter está visível](how-to-make-sure-that-a-gridsplitter-is-visible.md).  
  
 **Como criar um GridSplitter que ocupa uma linha**  
  
 Para especificar uma <xref:System.Windows.Controls.GridSplitter> que ocupa uma linha em uma <xref:System.Windows.Controls.Grid>, defina o <xref:System.Windows.Controls.Grid.Row%2A> propriedade anexada a uma das linhas que você deseja redimensionar. Se sua <xref:System.Windows.Controls.Grid> tiver mais de uma coluna, defina o <xref:System.Windows.Controls.Grid.ColumnSpan%2A> propriedade anexada como o número de colunas. Em seguida, defina a <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> para <xref:System.Windows.VerticalAlignment.Center>, defina o <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> propriedade a ser <xref:System.Windows.HorizontalAlignment.Stretch>e defina o <xref:System.Windows.Controls.RowDefinition.Height%2A> da linha que contém o <xref:System.Windows.Controls.GridSplitter> para <xref:System.Windows.GridLength.Auto%2A>.  
  
 O exemplo a seguir mostra como definir um horizontal <xref:System.Windows.Controls.GridSplitter> que ocupa uma linha e redimensiona as linhas em cada lado dele.  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart2](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart2)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Controls.GridSplitter>
- [Tópicos de instruções](gridsplitter-how-to-topics.md)
