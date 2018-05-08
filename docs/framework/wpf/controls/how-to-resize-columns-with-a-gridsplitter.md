---
title: Como redimensionar colunas com um GridSplitter
ms.date: 03/30/2017
helpviewer_keywords:
- grid columns [WPF], resizing
- GridSplitter control [WPF], resizing grid columns
- resizing grid columns [WPF]
ms.assetid: 47b20fe6-7adc-4aa6-9693-b4e184eef74b
ms.openlocfilehash: b4652c06cfe6f048f6c75a11b9447d70d6820e4f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-resize-columns-with-a-gridsplitter"></a>Como redimensionar colunas com um GridSplitter
Este exemplo mostra como criar um vertical <xref:System.Windows.Controls.GridSplitter> para redistribuir o espaço entre duas colunas em uma <xref:System.Windows.Controls.Grid> sem alterar as dimensões do <xref:System.Windows.Controls.Grid>.  
  
## <a name="example"></a>Exemplo  
 **Como criar um GridSplitter que sobrepõe a borda de uma coluna**  
  
 Para especificar um <xref:System.Windows.Controls.GridSplitter> que redimensiona colunas adjacentes em uma <xref:System.Windows.Controls.Grid>, defina o <xref:System.Windows.Controls.Grid.Column%2A> propriedade anexada a uma das colunas que você deseja redimensionar. Se seu <xref:System.Windows.Controls.Grid> tem mais de uma linha, defina a <xref:System.Windows.Controls.Grid.RowSpan%2A> propriedade anexada ao número de linhas. Em seguida, defina o <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> propriedade <xref:System.Windows.HorizontalAlignment.Left> ou <xref:System.Windows.HorizontalAlignment.Right> (o alinhamento que você define depende de quais duas colunas você deseja redimensionar). Finalmente, defina o <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> propriedade <xref:System.Windows.VerticalAlignment.Stretch>.  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterColumnOverlay](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplittercolumnoverlay)]  
  
 Um <xref:System.Windows.Controls.GridSplitter> que não tem sua própria coluna podem ser encobertas por outros controles no <xref:System.Windows.Controls.Grid>. Para obter mais informações sobre como evitar esse problema, consulte [Verifique se um GridSplitter está visível](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).  
  
 **Como criar um GridSplitter que ocupa uma coluna**  
  
 Para especificar um <xref:System.Windows.Controls.GridSplitter> que ocupa uma coluna em uma <xref:System.Windows.Controls.Grid>, defina o <xref:System.Windows.Controls.Grid.Column%2A> propriedade anexada a uma das colunas que você deseja redimensionar. Se a grade tem mais de uma linha, defina a <xref:System.Windows.Controls.Grid.RowSpan%2A> propriedade anexada ao número de linhas. Em seguida, defina o <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> para <xref:System.Windows.HorizontalAlignment.Center>, defina o <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> propriedade <xref:System.Windows.VerticalAlignment.Stretch>e defina o <xref:System.Windows.Controls.ColumnDefinition.Width%2A> da coluna que contém o <xref:System.Windows.Controls.GridSplitter> para <xref:System.Windows.GridLength.Auto%2A>.  
  
 O exemplo a seguir mostra como definir um vertical <xref:System.Windows.Controls.GridSplitter> que ocupa uma coluna e redimensiona as colunas em dos lados.  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart2)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.GridSplitter>  
 [Tópicos de instruções](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
