---
title: 'Como: Criar ListViewItems com um CheckBox'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], ListView
- controls [WPF], CheckBox
- ListView controls [WPF], CheckBox controls
- CheckBox control [WPF], ListView control
ms.assetid: f6d66c7f-906c-4f65-a55a-0ede9d00e26a
ms.openlocfilehash: b09d5ad11b0961febf524cec1e19cb1e59832e44
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910774"
---
# <a name="how-to-create-listviewitems-with-a-checkbox"></a>Como: Criar ListViewItems com um CheckBox
Este exemplo mostra como exibir uma coluna de <xref:System.Windows.Controls.CheckBox> controles em um <xref:System.Windows.Controls.ListView> controle que usa um <xref:System.Windows.Controls.GridView>.  
  
## <a name="example"></a>Exemplo  
 Para criar uma coluna que contém <xref:System.Windows.Controls.CheckBox> controles em um <xref:System.Windows.Controls.ListView>, criar um <xref:System.Windows.DataTemplate> que contém um <xref:System.Windows.Controls.CheckBox>. Em seguida, defina as <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> de um <xref:System.Windows.Controls.GridViewColumn> para o <xref:System.Windows.DataTemplate>.  
  
 A exemplo a seguir mostra uma <xref:System.Windows.DataTemplate> que contém um <xref:System.Windows.Controls.CheckBox>. O exemplo associa a <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> propriedade do <xref:System.Windows.Controls.CheckBox> para o <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> valor da propriedade a <xref:System.Windows.Controls.ListViewItem> que o contém. Portanto, quando o <xref:System.Windows.Controls.ListViewItem> que contém o <xref:System.Windows.Controls.CheckBox> for selecionada, o <xref:System.Windows.Controls.CheckBox> é verificada.  
  
 [!code-xaml[ListViewChkBox#CheckBoxDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#checkboxdatatemplate)]  
  
 O exemplo a seguir mostra como criar uma coluna de <xref:System.Windows.Controls.CheckBox> controles. Para tornar a coluna, o exemplo define o <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> propriedade do <xref:System.Windows.Controls.GridViewColumn> para o <xref:System.Windows.DataTemplate>.  
  
 [!code-xaml[ListViewChkBox#GridViewColumnCheckBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#gridviewcolumncheckbox)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.Control>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [Visão geral de ListView](listview-overview.md)
- [Tópicos de instruções](listview-how-to-topics.md)
- [Visão geral de GridView](gridview-overview.md)
