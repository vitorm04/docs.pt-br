---
title: 'Como: Usar modelos para moldar um ListView que use GridView'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 94bf964b-96c8-4bdf-a0c3-f5271b7cb565
ms.openlocfilehash: 1caa652c4a2a3a7d0a8d40fe703df7a3e8038c9b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699117"
---
# <a name="how-to-use-templates-to-style-a-listview-that-uses-gridview"></a>Como: Usar modelos para moldar um ListView que use GridView
Este exemplo mostra como usar o <xref:System.Windows.DataTemplate> e <xref:System.Windows.Style> objetos para especificar a aparência de um <xref:System.Windows.Controls.ListView> controle que usa um <xref:System.Windows.Controls.GridView> modo de exibição.  
  
## <a name="example"></a>Exemplo  
 Os exemplos a seguir mostram <xref:System.Windows.Style> e <xref:System.Windows.DataTemplate> objetos que personalizam a aparência de um cabeçalho de coluna para um <xref:System.Windows.Controls.GridViewColumn>.  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheaderstyle)]  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheadertemplate)]  
  
 O exemplo a seguir mostra como usar esses <xref:System.Windows.Style> e <xref:System.Windows.DataTemplate> objetos para definir o <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> e <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> as propriedades de um <xref:System.Windows.Controls.GridViewColumn>. O <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> propriedade define o conteúdo das células da coluna.  
  
 [!code-xaml[ListViewTemplate#GridViewColumnTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcolumntemplate)]  
  
 O <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> e <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> são apenas duas das várias propriedades que você pode usar para personalizar a aparência do cabeçalho de coluna para um <xref:System.Windows.Controls.GridView> controle. Para obter mais informações, consulte [Visão geral de modelos e estilos de cabeçalho de coluna GridView](gridview-column-header-styles-and-templates-overview.md).  
  
 O exemplo a seguir mostra como definir um <xref:System.Windows.DataTemplate> que personaliza a aparência das células em uma <xref:System.Windows.Controls.GridViewColumn>.  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 O exemplo a seguir mostra como usar esse <xref:System.Windows.DataTemplate> para definir o conteúdo de um <xref:System.Windows.Controls.GridViewColumn> célula. Este modelo é usado em vez do <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> mostrado anteriormente na propriedade <xref:System.Windows.Controls.GridViewColumn> exemplo.  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [Visão geral de GridView](gridview-overview.md)
- [Tópicos de instruções](listview-how-to-topics.md)
- [Visão geral de ListView](listview-overview.md)
