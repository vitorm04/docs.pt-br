---
title: 'Como: Redimensionar colunas com um GridSplitter'
ms.date: 03/30/2017
helpviewer_keywords:
- grid columns [WPF], resizing
- GridSplitter control [WPF], resizing grid columns
- resizing grid columns [WPF]
ms.assetid: 47b20fe6-7adc-4aa6-9693-b4e184eef74b
ms.openlocfilehash: 93106ee25d98a056dfa5ba1a064c9803bebb072e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374122"
---
# <a name="how-to-resize-columns-with-a-gridsplitter"></a>Como: Redimensionar colunas com um GridSplitter
Este exemplo mostra como criar uma vertical <xref:System.Windows.Controls.GridSplitter> para redistribuir o espaço entre duas colunas em uma <xref:System.Windows.Controls.Grid> sem alterar as dimensões do <xref:System.Windows.Controls.Grid>.  
  
## <a name="example"></a>Exemplo  
 **Como criar um GridSplitter que sobrepõe a borda de uma coluna**  
  
 Para especificar uma <xref:System.Windows.Controls.GridSplitter> que redimensiona as colunas adjacentes em uma <xref:System.Windows.Controls.Grid>, defina o <xref:System.Windows.Controls.Grid.Column%2A> propriedade anexada a uma das colunas que você deseja redimensionar. Se sua <xref:System.Windows.Controls.Grid> tem mais de uma linha, defina o <xref:System.Windows.Controls.Grid.RowSpan%2A> propriedade anexada como o número de linhas. Em seguida, defina as <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> propriedade para <xref:System.Windows.HorizontalAlignment.Left> ou <xref:System.Windows.HorizontalAlignment.Right> (o alinhamento definido depende de quais duas colunas você deseja redimensionar). Por fim, defina as <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> propriedade para <xref:System.Windows.VerticalAlignment.Stretch>.  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterColumnOverlay](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplittercolumnoverlay)]  
  
 Um <xref:System.Windows.Controls.GridSplitter> que não tem sua própria coluna pode ser obscurecido por outros controles no <xref:System.Windows.Controls.Grid>. Para obter mais informações sobre como evitar esse problema, consulte [Verifique se um GridSplitter está visível](how-to-make-sure-that-a-gridsplitter-is-visible.md).  
  
 **Como criar um GridSplitter que ocupa uma coluna**  
  
 Para especificar uma <xref:System.Windows.Controls.GridSplitter> que ocupa uma coluna em uma <xref:System.Windows.Controls.Grid>, defina o <xref:System.Windows.Controls.Grid.Column%2A> propriedade anexada a uma das colunas que você deseja redimensionar. Se sua grade tiver mais de uma linha, defina o <xref:System.Windows.Controls.Grid.RowSpan%2A> propriedade anexada como o número de linhas. Em seguida, defina a <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> para <xref:System.Windows.HorizontalAlignment.Center>, defina o <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> propriedade a ser <xref:System.Windows.VerticalAlignment.Stretch>e defina o <xref:System.Windows.Controls.ColumnDefinition.Width%2A> da coluna que contém o <xref:System.Windows.Controls.GridSplitter> para <xref:System.Windows.GridLength.Auto%2A>.  
  
 O exemplo a seguir mostra como definir uma vertical <xref:System.Windows.Controls.GridSplitter> que ocupa uma coluna e redimensiona as colunas em cada lado dele.  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart2](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart2)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Controls.GridSplitter>
- [Tópicos de instruções](gridsplitter-how-to-topics.md)
