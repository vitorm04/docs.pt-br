---
title: Como criar um ListViewItems com um CheckBox
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], ListView
- controls [WPF], CheckBox
- ListView controls [WPF], CheckBox controls
- CheckBox control [WPF], ListView control
ms.assetid: f6d66c7f-906c-4f65-a55a-0ede9d00e26a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: be87183efd8101233bd5cbda49d556d09802b630
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-listviewitems-with-a-checkbox"></a>Como criar um ListViewItems com um CheckBox
Este exemplo mostra como exibir uma coluna de <xref:System.Windows.Controls.CheckBox> controles em um <xref:System.Windows.Controls.ListView> controle que usa um <xref:System.Windows.Controls.GridView>.  
  
## <a name="example"></a>Exemplo  
 Para criar uma coluna que contém <xref:System.Windows.Controls.CheckBox> controles em um <xref:System.Windows.Controls.ListView>, crie um <xref:System.Windows.DataTemplate> que contém um <xref:System.Windows.Controls.CheckBox>. Em seguida, defina o <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> de um <xref:System.Windows.Controls.GridViewColumn> para o <xref:System.Windows.DataTemplate>.  
  
 A exemplo a seguir mostra um <xref:System.Windows.DataTemplate> que contém um <xref:System.Windows.Controls.CheckBox>. O exemplo associa o <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> propriedade do <xref:System.Windows.Controls.CheckBox> para o <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> valor da propriedade a <xref:System.Windows.Controls.ListViewItem> que o contém. Portanto, quando o <xref:System.Windows.Controls.ListViewItem> que contém o <xref:System.Windows.Controls.CheckBox> for selecionada, o <xref:System.Windows.Controls.CheckBox> é verificada.  
  
 [!code-xaml[ListViewChkBox#CheckBoxDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#checkboxdatatemplate)]  
  
 O exemplo a seguir mostra como criar uma coluna de <xref:System.Windows.Controls.CheckBox> controles. Para tornar a coluna, o exemplo define o <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> propriedade o <xref:System.Windows.Controls.GridViewColumn> para o <xref:System.Windows.DataTemplate>.  
  
 [!code-xaml[ListViewChkBox#GridViewColumnCheckBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#gridviewcolumncheckbox)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.Control>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [Visão geral de ListView](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [Visão geral de GridView](../../../../docs/framework/wpf/controls/gridview-overview.md)
